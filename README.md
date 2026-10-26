# Agave (agave)

<!-- API-EVANGELIST-PROVENANCE:BEGIN -->
> ### About this repository
>
> **This is not our API.** This repository is an independent, third-party profile of a company's
> **publicly available** API surface, maintained by [API Evangelist](https://apievangelist.com).
> API Evangelist does not operate, host, resell, or support this company's APIs, and is not
> affiliated with or endorsed by the company unless stated on the profile.
>
> **Where the information came from.** Everything here is assembled from material a member of the
> public can reach with a browser and no credentials — the company's own website, developer portal
> and documentation, the specifications it publishes for public use (OpenAPI, AsyncAPI, JSON Schema,
> `apis.json`, `llms.txt` and similar), its public repositories, and its public status, pricing and
> changelog pages. **Nothing here is obtained by breaching a system, defeating an access control, or
> using credentials of any kind.**
>
> **The rating is an independent assessment.** The Kin Score and Agent Readiness rating are
> independently calculated scores of a company's *public* API artifacts, produced by API Evangelist
> against a published rubric. They are not certifications, endorsements, security assessments, or
> audits, and they score published artifacts — not the quality, safety, or security of the software.
>
> **Corrections, re-scores, and removal are free.** No partnership, contract, or purchase is
> required, and you do not need to justify the request.
>
> - **Something wrong?** Open an issue on this repository, or email
>   [info@apievangelist.com](mailto:info@apievangelist.com).
> - **Published something new?** Ask for a re-score and we will re-run the rating.
> - **Want the listing taken down?** Say so and we will honor it. The profile is reduced to your
>   company name, a factual description, and a link to your own site, and the company is recorded as
>   **unrated** — never scored zero for having asked.
>
> **Response times.** Acknowledgement within **one business day**; removal or restriction within
> **two business days**; corrections and re-scores within **five business days**.
>
> **Not from the company, and here with a question?** You are welcome here — we would rather be the
> front line and point you the right way than have a good report go nowhere. What this repository
> can answer is narrow, though, so it is worth knowing who you are actually looking for:
>
> - **A question about how the API works, an account, billing, or a bug in the service** — that is
>   the company's own support, not us. We profile this API; we do not operate it and cannot see
>   your account.
> - **A bug in an open-source project we only catalog** — file it on that project's own repository.
>   This has happened with a real and correct bug report that reached us instead of the people who
>   could fix it, which helped nobody.
> - **Anything about this listing itself** — the description, the tags, the rating, a missing or
>   wrong artifact — is ours. Open an issue here.
> - **Not sure, or something general about API Evangelist or APIs.io** — open an issue on the
>   [APIs.io Inbox](https://github.com/api-search/inbox) and we will route it.
>
> **This repository contains no software, and we will never ask you to download anything.** There is
> no build, release, installer, or binary here — only text and machine-readable API descriptions, so
> there is nothing here that can be "corrupt" or need "repairing". Any issue, comment, or email
> claiming otherwise and offering a download link is not from us and is hostile. Do not follow the
> link; it is a lure. Report it to GitHub and, if you like, tell us at
> [info@apievangelist.com](mailto:info@apievangelist.com) so we can take it down.
>
> **On a security or compliance team?** Email
> [info@apievangelist.com](mailto:info@apievangelist.com) with *security* in the subject line and
> you will get a person, not a form. We will tell you exactly which public URLs this profile was
> built from so your team can see the same surface we did, and we will take the listing down on
> request while you work through it.
>
> Full detail: **[Where this data comes from](https://apievangelist.com/about/where-our-data-comes-from)**
<!-- API-EVANGELIST-PROVENANCE:END -->

Agave is a unified API platform for the construction industry, enabling software companies and contractors to read and write data across 100+ construction and accounting software systems including Procore, Autodesk Build, QuickBooks, Sage, Viewpoint, and more.

**APIs.json:** [https://raw.githubusercontent.com/api-evangelist/agave/refs/heads/main/apis.yml](https://raw.githubusercontent.com/api-evangelist/agave/refs/heads/main/apis.yml)

## Scope

- **Position:** Consuming
- **Access:** 3rd-Party

## Tags

- Accounting
- Construction
- Integration

## Timestamps

- **Created:** 2025-03-01
- **Modified:** 2026-04-19

## APIs

### Agave Unified Construction API

The Agave Unified Construction API provides a single REST API to read and write data from 100+ construction and accounting software systems. It normalizes data across platforms covering projects, budgets, contracts, commitments, purchase orders, invoices, cost codes, vendors, timesheets, and employees.

- **Human URL:** [https://docs.agaveapi.com/](https://docs.agaveapi.com/)
- **Base URL:** `https://api.agaveapi.com`

#### Tags

- Accounting
- Budgets
- Construction
- Contracts
- Integration
- Projects

#### Properties

- [Documentation](https://docs.agaveapi.com/)
- [API Reference](https://docs.agaveapi.com/reference)
- [Quickstart](https://docs.agaveapi.com/quickstart)
- [OpenAPI](openapi/agave-unified-api-openapi.yml) — [OpenAPI Specification](https://spec.openapis.org/oas/latest.html)
- [Postman Collection](collections/agave-unified-api.postman_collection.json) — [Postman Collection 2.1](https://schema.getpostman.com/json/collection/v2.1.0/collection.json)
- [Open Collection](collections/agave-unified-api.opencollection.json) — [Open Collection 1.0](https://schema.opencollection.com/opencollection/v1.0.0.json)

### Agave Link Component

Agave Link is a front-end component that enables users to select source systems, authenticate with their construction software accounts, and share data with your application, handling OAuth flows for all supported platforms.

- **Human URL:** [https://docs.agaveapi.com/](https://docs.agaveapi.com/)
- **Base URL:** `https://api.agaveapi.com`

#### Tags

- Authentication
- Construction
- Front-End
- OAuth

#### Properties

- [Documentation](https://docs.agaveapi.com/)
- [SDK](https://github.com/agave-api/react-agave-link)
- [Postman Collection](collections/agave-unified-api.postman_collection.json) — [Postman Collection 2.1](https://schema.getpostman.com/json/collection/v2.1.0/collection.json)
- [Open Collection](collections/agave-unified-api.opencollection.json) — [Open Collection 1.0](https://schema.opencollection.com/opencollection/v1.0.0.json)

### Agave File Manager Component

Agave File Manager is a front-end component that allows users to pick files and folders from linked construction software accounts to share with your application.

- **Human URL:** [https://docs.agaveapi.com/agave-file-manager/component](https://docs.agaveapi.com/agave-file-manager/component)
- **Base URL:** `https://api.agaveapi.com`

#### Tags

- Construction
- Documents
- Files
- Front-End

#### Properties

- [Documentation](https://docs.agaveapi.com/agave-file-manager/component)
- [Postman Collection](collections/agave-unified-api.postman_collection.json) — [Postman Collection 2.1](https://schema.getpostman.com/json/collection/v2.1.0/collection.json)
- [Open Collection](collections/agave-unified-api.opencollection.json) — [Open Collection 1.0](https://schema.opencollection.com/opencollection/v1.0.0.json)

## Common Properties

- [LinkedIn](https://www.linkedin.com/company/agave-api)
- [Portal](https://docs.agaveapi.com)
- [Getting Started](https://docs.agaveapi.com/quickstart)
- [Authentication](https://docs.agaveapi.com/agave-api/identifiers)
- [Pricing](https://www.agaveapi.com/software-vendors/pricing/)
- [Security](https://security.agaveapi.com/)
- [Partners](https://www.agaveapi.com/partners/)
- [GitHub Organization](https://github.com/agave-api)
- [SDK](https://github.com/agave-api/react-agave-link)
- [Features](undefined)
- [Use Cases](undefined)
- [Integrations](undefined)
- [OpenAPI](openapi/agave-unified-api-openapi.yml) — [OpenAPI Specification](https://spec.openapis.org/oas/latest.html)
- [JSON Schema](json-schema/unified-api-budget-list-schema.json) — [JSON Schema](https://json-schema.org/specification)
- [JSON Schema](json-schema/unified-api-budget-schema.json) — [JSON Schema](https://json-schema.org/specification)
- [JSON Schema](json-schema/unified-api-contract-list-schema.json) — [JSON Schema](https://json-schema.org/specification)
- [JSON Schema](json-schema/unified-api-contract-schema.json) — [JSON Schema](https://json-schema.org/specification)
- [JSON Schema](json-schema/unified-api-cost-code-list-schema.json) — [JSON Schema](https://json-schema.org/specification)
- [JSON Schema](json-schema/unified-api-cost-code-schema.json) — [JSON Schema](https://json-schema.org/specification)
- [JSON Schema](json-schema/unified-api-employee-list-schema.json) — [JSON Schema](https://json-schema.org/specification)
- [JSON Schema](json-schema/unified-api-employee-schema.json) — [JSON Schema](https://json-schema.org/specification)
- [JSON Schema](json-schema/unified-api-invoice-list-schema.json) — [JSON Schema](https://json-schema.org/specification)
- [JSON Schema](json-schema/unified-api-invoice-request-schema.json) — [JSON Schema](https://json-schema.org/specification)
- [JSON Schema](json-schema/unified-api-invoice-schema.json) — [JSON Schema](https://json-schema.org/specification)
- [JSON Schema](json-schema/unified-api-link-session-request-schema.json) — [JSON Schema](https://json-schema.org/specification)
- [JSON Schema](json-schema/unified-api-link-session-schema.json) — [JSON Schema](https://json-schema.org/specification)
- [JSON Schema](json-schema/unified-api-project-list-schema.json) — [JSON Schema](https://json-schema.org/specification)
- [JSON Schema](json-schema/unified-api-project-schema.json) — [JSON Schema](https://json-schema.org/specification)
- [JSON Schema](json-schema/unified-api-timesheet-list-schema.json) — [JSON Schema](https://json-schema.org/specification)
- [JSON Schema](json-schema/unified-api-timesheet-schema.json) — [JSON Schema](https://json-schema.org/specification)
- [JSON Schema](json-schema/unified-api-vendor-list-schema.json) — [JSON Schema](https://json-schema.org/specification)
- [JSON Schema](json-schema/unified-api-vendor-schema.json) — [JSON Schema](https://json-schema.org/specification)
- [JSON Structure](json-structure/unified-api-budget-list-structure.json)
- [JSON Structure](json-structure/unified-api-budget-structure.json)
- [JSON Structure](json-structure/unified-api-contract-list-structure.json)
- [JSON Structure](json-structure/unified-api-contract-structure.json)
- [JSON Structure](json-structure/unified-api-cost-code-list-structure.json)
- [JSON Structure](json-structure/unified-api-cost-code-structure.json)
- [JSON Structure](json-structure/unified-api-employee-list-structure.json)
- [JSON Structure](json-structure/unified-api-employee-structure.json)
- [JSON Structure](json-structure/unified-api-invoice-list-structure.json)
- [JSON Structure](json-structure/unified-api-invoice-request-structure.json)
- [JSON Structure](json-structure/unified-api-invoice-structure.json)
- [JSON Structure](json-structure/unified-api-link-session-request-structure.json)
- [JSON Structure](json-structure/unified-api-link-session-structure.json)
- [JSON Structure](json-structure/unified-api-project-list-structure.json)
- [JSON Structure](json-structure/unified-api-project-structure.json)
- [JSON Structure](json-structure/unified-api-timesheet-list-structure.json)
- [JSON Structure](json-structure/unified-api-timesheet-structure.json)
- [JSON Structure](json-structure/unified-api-vendor-list-structure.json)
- [JSON Structure](json-structure/unified-api-vendor-structure.json)
- [JSON-LD](json-ld/agave-unified-context.jsonld) — [JSON-LD](https://www.w3.org/TR/json-ld11/)
- [Example](examples/unified-api-budget-example.json)
- [Example](examples/unified-api-budget-list-example.json)
- [Example](examples/unified-api-contract-example.json)
- [Example](examples/unified-api-contract-list-example.json)
- [Example](examples/unified-api-cost-code-example.json)
- [Example](examples/unified-api-cost-code-list-example.json)
- [Example](examples/unified-api-employee-example.json)
- [Example](examples/unified-api-employee-list-example.json)
- [Example](examples/unified-api-invoice-example.json)
- [Example](examples/unified-api-invoice-list-example.json)
- [Example](examples/unified-api-invoice-request-example.json)
- [Example](examples/unified-api-link-session-example.json)
- [Example](examples/unified-api-link-session-request-example.json)
- [Example](examples/unified-api-project-example.json)
- [Example](examples/unified-api-project-list-example.json)
- [Example](examples/unified-api-timesheet-example.json)
- [Example](examples/unified-api-timesheet-list-example.json)
- [Example](examples/unified-api-vendor-example.json)
- [Example](examples/unified-api-vendor-list-example.json)
- [Spectral Rules](rules/agave-spectral-rules.yml)
- [Vocabulary](vocabulary/agave-vocabulary.yaml)

## Maintainers

**FN:** Kin Lane
**Email:** kin@apievangelist.com
