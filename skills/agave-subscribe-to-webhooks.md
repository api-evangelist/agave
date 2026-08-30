---
name: Subscribe to Agave webhooks and verify what arrives
description: >-
  Register change-event webhooks for a linked account, and handle the fact that Agave signs nothing.
api: openapi/_ae-authored/agave-unified-api-from-postman-openapi.yml
operations:
  - postWebhooks
  - getWebhooks
  - getWebhooksByWebhookId
  - deleteWebhooksByWebhookId
  - getLinkSourceSystem
generated: '2026-08-30'
method: generated
source: https://docs.agaveapi.com/agave-api/webhooks
---

# Subscribe to Agave webhooks

## Check coverage first

Webhooks exist for **7 of 100+ source systems**: Autodesk Build, BIM 360, HubSpot, Pipedrive,
Procore, QuickBooks Online, SharePoint Online. Call `getLinkSourceSystem`
(`GET /link/source-system`) to see what this account is actually connected to; if it is Sage,
Viewpoint, Foundation, CMiC or Acumatica, there are no events and you must poll. Design the
integration so polling is the baseline and webhooks are an accelerator, not the other way round.

## Steps

1. **Register.** `postWebhooks` (`POST /webhooks`) with:
   - `callback_url` — your HTTPS endpoint.
   - `event` — `CREATE`, `UPDATE` or `DELETE`.
   - `type` — the object type (`file`, `folder`, `rfi`, `submittal`, `vendor`, and others; Agave
     publishes examples rather than a closed list).
   - `authorization_header` — optional, and the **only** delivery-authentication mechanism Agave
     offers. Set it. Agave echoes the value as the `Authorization` header on every delivery.

   Send `Project-Id` as well when registering a project-level webhook.

2. **Record what you got.** The response carries `id`, `source_id`, `target` (e.g. `file:*` — the
   type plus either one Agave UUID or `*` for all objects of that type) and `project_id` for
   project-level subscriptions.

3. **Audit.** `getWebhooks` (`GET /webhooks`) and `getWebhooksByWebhookId`. Reconcile against your
   own registry on a schedule — a subscription can outlive the code that created it.

4. **Tear down.** `deleteWebhooksByWebhookId` (`DELETE /webhooks/{webhook_id}`) when a customer
   unlinks. Nothing removes subscriptions automatically.

## Receiving events — treat the payload as untrusted

**Agave does not sign webhook deliveries.** There is no HMAC signature header, no signing secret, no
timestamp, and no replay protection. Authenticity rests entirely on the static
`authorization_header` you supplied. That means:

- Compare the incoming `Authorization` header against your stored value in constant time, and reject
  on mismatch.
- Rotate it by deleting and re-creating the subscription; there is no rotate operation.
- Never treat the payload as authoritative. Use the event as a **hint** and re-read the object
  through the API (`GET /files/{id}`, `GET /rfis/{id}`, …) before acting on it. A leaked callback URL
  plus header is a complete forgery path, and re-reading closes it.
- Agave documents no retry schedule or dead-letter behaviour, so return `2xx` fast and process
  asynchronously — and reconcile by polling anyway, because you cannot know whether a failed delivery
  will be retried.

For local development Agave suggests generating a callback URL at `webhook.site` before pointing the
subscription at a real endpoint.
