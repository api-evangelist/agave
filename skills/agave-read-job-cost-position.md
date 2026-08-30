---
name: Read a project's job-cost position
description: >-
  Pull budget, committed cost, actual cost and approved changes for one construction project across
  whichever ERP the customer runs, and paginate it correctly.
api: openapi/_ae-authored/agave-unified-api-from-postman-openapi.yml
operations:
  - getProjects
  - getProjectsByProjectId
  - getBudgetLineItems
  - getJobCosts
  - getCostCodes
  - getCostTypes
  - getChangeOrders
  - getCostProjections
generated: '2026-08-30'
method: generated
source: https://docs.agaveapi.com/agave-api/pagination
---

# Read a project's job-cost position

This is the read-only flow Agave exists for: one shape of answer — where is this job against budget —
regardless of whether the numbers live in Sage 300, Vista, Acumatica, Foundation or QuickBooks.

## Steps

1. **Find the project.** `getProjects` (`GET /projects`), then `getProjectsByProjectId`
   (`GET /projects/{project_id}`) for detail. Note the Agave UUID.

2. **Scope the rest of the calls.** For construction PM and field-service source systems, send the
   `Project-Id` header carrying that UUID. Some endpoints accept `Project-Id: *` to return
   project-level records across all projects — useful for a portfolio roll-up, expensive on a large
   account.

3. **Pull the cost dimensions.** `getCostCodes` (`GET /cost-codes`) and `getCostTypes`
   (`GET /cost-types`) give you the axes; cache them per linked account, they change rarely.

4. **Pull the money.**
   - `getBudgetLineItems` (`GET /budget-line-items`) — the budget.
   - `getJobCosts` (`GET /job-costs`) — actuals to date.
   - `getChangeOrders` (`GET /change-orders`) — approved changes; use
     `getPrimeContractsByPrimeContractIdChangeOrders` or
     `getSubcontractsBySubcontractIdChangeOrders` when you need them attributed to one contract.
   - `getCostProjections` (`GET /cost-projections`) — where the source system publishes a forecast.

5. **Join on cost code, not on name.** Match budget lines to job costs by cost-code id. Project and
   vendor *names* differ between the PM system and the ERP for the same real entity; that mismatch is
   the whole reason the customer bought Agave.

## Pagination — the part that silently truncates

`page` and `per_page` (1–1000; the default is 10–100 depending on the source system). Responses look
like:

```json
{ "data": [ ... ], "meta": { "current_page": 1, "has_more_results": true } }
```

**Keep paginating until `has_more_results` is literally `false`.** Some source systems return `null`
when they cannot tell. `null` is *not* the end of the results — treating it as one is how a
job-cost report quietly loses its last page.

## Freshness, limits and large pulls

- `Agave-Data-Retrieved-At` on the response tells you when the data was actually read from the source
  system. Show it. A cost report with no as-of stamp is a liability.
- Read `Agave-RateLimit-Remaining` and `{SourceSystem}-RateLimit-Remaining` as you go. The Agave
  ceiling is 150 requests/minute per linked account; the source system's is usually tighter and
  varies wildly — Procore 3,600/hour per user, QuickBooks Online 500/minute, Sage 300 CRE and
  QuickBooks Desktop serially with at most 5 queued.
- On `429`, back off exponentially. Agave documents no `Retry-After` header, so you must supply the
  schedule yourself.
- For a whole-project sweep, set `Async-Request: true`, take the `202` and the
  `Agave-Async-Request-Id`, then poll `getAsyncRequestsByAsyncRequestId`
  (`GET /async-requests/{async_request_id}`) rather than holding a synchronous connection open
  against a serially-executing ERP.
- Need a field Agave has not normalised? Send `Include-Source-Data: true` (or a comma-delimited field
  list) and read `source_data` — but treat anything you find there as source-system-specific, because
  it is.
