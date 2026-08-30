---
name: Link a construction source system to Agave
description: >-
  Take an end customer from "I use Procore" to a working Account-Token, using Agave Link, so every
  later API call acts against their real ERP or PM system.
api: openapi/_ae-authored/agave-unified-api-from-postman-openapi.yml
operations:
  - getLinkSourceSystems
  - postLinkTokenCreate
  - postLinkTokenExchange
  - getLinkAccount
  - getLinkCompanies
  - getLinkConnection
generated: '2026-08-30'
method: generated
source: https://docs.agaveapi.com/agave-link/quickstart
---

# Link a construction source system to Agave

Nothing else in the Agave API works until this is done. Agave's own credentials
(`Client-Id` + `Client-Secret`) identify **your application**; the `Account-Token` you get at the end
of this flow identifies **one customer's connected system**, and every data call needs both.

## Before you start

Every request carries four headers. Three are yours, one comes from this flow.

- `API-Version: 2021-11-21` — required on **every** request. Without it you get `401` with
  `{"message": "Invalid API-Version header"}`, before authentication is even considered.
- `Client-Id` — 36-character UUID, issued by Agave (`api-support@agaveapi.com`).
- `Client-Secret` — 40-character string. **Server-side only.** It must never reach a browser.
- `Account-Token` — the output of this skill. Not applicable on Link Token requests.

Base URL is `https://api.agaveapi.com`. There is no `/v1` prefix and there is no sandbox host —
`sandbox.agaveapi.com` does not resolve. Testing happens by linking a *source system's* sandbox
account (`sandbox/agave-sandbox.yml`).

## Steps

1. **Decide which systems to offer.** Call `getLinkSourceSystems` (`GET /link/source-systems`) to
   read the systems available to your account. Use it to build your own picker, or skip it and let
   Agave Link render the selection screen.

2. **Mint a Link Token.** Call `postLinkTokenCreate` (`POST /link/token/create`) with a
   `reference_id`. Send only `Client-Id`, `Client-Secret` and `API-Version` — **no `Account-Token`**;
   there isn't one yet.

   The `reference_id` is load-bearing and easy to get wrong. It is an opaque string of yours, max 255
   characters, and Agave uses it to decide whether this is a new integration or a re-authentication.
   One `reference_id` belongs to exactly one integration. If a user can link several accounts (say
   two Procore companies), give each its own — `user-1234:procore-a`, `user-1234:procore-b`. For
   on-prem and hosted systems (QuickBooks Desktop, Foundation, Vista, Sage 100/300, ComputerEase,
   Cheops) you **must** reuse the same `reference_id` to re-authenticate the same user, because a
   different one produces different Agave ids for the same underlying objects.

3. **Open Agave Link in the browser.** Load `https://cdn.agaveapi.com/init.js` directly — Agave
   requires it be loaded from their CDN, not bundled — and call
   `AgaveLink.openLink({ linkToken, onSuccess, onExit })`. During development set
   `showSandboxSourceSystems: true` and `showProductionSourceSystems: false` so nobody links a live
   ERP by accident.

4. **Exchange the public token.** `onSuccess` hands you a `publicToken`. Send it from your server to
   `postLinkTokenExchange` (`POST /link/token/exchange`) and store the returned `Account-Token`
   against your user. It is long-lived and non-scoped: it grants whatever the linking user granted,
   and there is nothing to narrow.

5. **Confirm what you actually linked.** With the new `Account-Token` in place, call
   `getLinkAccount` (`GET /link/account`) and `getLinkConnection` (`GET /link/connection`) to see the
   account and its connection state. If the customer granted cross-company access, call
   `getLinkCompanies` (`GET /link/companies`) and carry the chosen company UUID as the `Company-Id`
   header on subsequent requests.

## Rules that bite

- **The `Client-Secret` is not a browser credential.** Steps 2 and 4 are server-side. Only the
  `linkToken` and the `publicToken` are safe to expose.
- **Re-linking with a different `reference_id` renumbers everything.** Agave ids are derived per
  reference — the same Procore project comes back with a different `id`. Store `source_id` alongside
  `id` if you need to survive a re-link.
- **Revocation exists but is undocumented.** `postLinkRevokeTokens` (`POST /link/revoke-tokens`) and
  the admin equivalent appear in Agave's own Postman collection; neither is covered in the developer
  docs. Treat them as real but unsupported, and confirm behaviour with `api-support@agaveapi.com`
  before wiring them into a teardown path.
