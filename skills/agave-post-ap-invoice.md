---
name: Post an AP invoice with line items into the customer's ERP
description: >-
  Create an accounts-payable invoice header and its line items through Agave, coded to the right
  vendor, project and cost code — and understand what you can and cannot take back.
api: openapi/_ae-authored/agave-unified-api-from-postman-openapi.yml
operations:
  - getVendors
  - getProjects
  - getCostCodes
  - getCostTypes
  - postApInvoices
  - postApInvoicesByApInvoiceIdLineItems
  - getApInvoicesByApInvoiceId
  - getApInvoicesByApInvoiceIdLineItems
  - putApInvoicesByApInvoiceId
  - deleteApInvoicesByApInvoiceId
generated: '2026-08-30'
method: generated
source: https://docs.agaveapi.com/agave-api/line-items
---

# Post an AP invoice with line items

This writes into the customer's system of record. Read the reversibility section **before** the
first POST, not after.

## Steps

1. **Resolve the references first.** An invoice that fails validation halfway through is the worst
   outcome here, so resolve every foreign reference before you create anything:
   - `getVendors` (`GET /vendors`) — the vendor.
   - `getProjects` (`GET /projects`) — the job.
   - `getCostCodes` (`GET /cost-codes`) and `getCostTypes` (`GET /cost-types`) — the coding.

2. **Create the header.** `postApInvoices` (`POST /ap-invoices`). Keep the returned Agave `id` and
   `source_id`; the `source_id` is the identifier the customer's accounting team will actually
   recognise.

3. **Add the line items.** `postApInvoicesByApInvoiceIdLineItems`
   (`POST /ap-invoices/{ap_invoice_id}/line-items`), one call per line. There is no documented bulk
   line-item write for AP invoices (bulk `PATCH` exists for budget line items, change orders and
   vendors, but not here).

4. **Read it back.** `getApInvoicesByApInvoiceId` and `getApInvoicesByApInvoiceIdLineItems`. Compare
   the totals you sent to the totals the ERP computed — rounding and tax treatment are the source
   system's, not Agave's.

## Reversibility — know this before you write

Agave publishes **no undo, void or reversal operation, and no reversal window**, for any financial
object. What exists:

- `deleteApInvoicesByApInvoiceId` (`DELETE /ap-invoices/{ap_invoice_id}`) and the line-item delete.
  Whether the ERP honours a delete depends on the ERP and on period-close state — a posted invoice
  in a closed period is typically immutable, and Agave neither surfaces that state nor documents it.
- Delete-then-recreate is **compensation, not reversal**: the new record gets a new Agave `id` and a
  new `source_id`, and anything referencing the original breaks.

Treat every AP write as effectively irreversible through Agave. If a human needs to approve, get the
approval before step 2, not between steps 2 and 3.

## Error handling

Agave normalises every source-system error into its own status vocabulary. There is **no error code
field** — only the HTTP status and a human string — so branch on the status:

- `400` — bad request, usually a missing required field or an unsupported one. Leave
  `Ignore-Prohibited-Fields` at its default `false` so a field the ERP rejects surfaces as an error
  instead of being silently dropped.
- `401` — check `API-Version`, `Client-Id`, `Client-Secret`, `Account-Token`.
- `403` — same published description as `401`; the two are not distinguishable from the docs.
- `409` — a conflict, which Agave documents as possibly "using the same idempotent key". Agave
  enforces idempotency on writes but **does not publish the header name, its scope, or its
  retention**. So: do not blind-retry a POST. Read back with `getApInvoices` filtered to your
  reference before retrying, or you risk a duplicate payable.
- `429` — rate limited. Back off exponentially; no `Retry-After` is documented.
- `500` / `503` — Agave or the source system. Retryable, but re-read before re-posting for the same
  reason as `409`.

Capture `Agave-Debug-Id` (and the `debug_id` in the error body) on every failure — it is what Agave
support asks for.
