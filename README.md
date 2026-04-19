# Agave (agave)
Agave is a unified API platform for the construction industry, enabling software companies and contractors to read and write data across 100+ construction and accounting software systems including Procore, Autodesk Build, QuickBooks, Sage, Viewpoint, and more.

**URL:** [https://docs.agaveapi.com](https://docs.agaveapi.com)

**Run:** [Capabilities Using Naftiko](https://github.com/naftiko/fleet?utm_source=api-evangelist&utm_medium=readme&utm_campaign=company-api-evangelist&utm_content=repo)

## Tags:

 - Accounting, Authentication, Budgets, Construction, Contracts, Documents, Files, Front-End, Integration, OAuth, Projects

## Timestamps

- **Created:** 2025-03-01
- **Modified:** 2026-04-19

## APIs

### Agave Unified Construction API
The Agave Unified Construction API provides a single REST API to read and write data from 100+ construction and accounting software systems. It normalizes data across platforms covering projects, budgets, contracts, commitments, purchase orders, invoices, cost codes, vendors, timesheets, and employees.

**Human URL:** [https://docs.agaveapi.com/](https://docs.agaveapi.com/)

#### Tags:

 - Accounting, Budgets, Construction, Contracts, Integration, Projects

#### Properties

- [Documentation](https://docs.agaveapi.com/)
- [APIReference](https://docs.agaveapi.com/reference)
- [Quickstart](https://docs.agaveapi.com/quickstart)
- [OpenAPI](openapi/agave-unified-api-openapi.yml)

### Agave Link Component
Agave Link is a front-end component that enables users to select source systems, authenticate with their construction software accounts, and share data with your application, handling OAuth flows for all supported platforms.

**Human URL:** [https://docs.agaveapi.com/](https://docs.agaveapi.com/)

#### Tags:

 - Authentication, Construction, Front-End, OAuth

#### Properties

- [Documentation](https://docs.agaveapi.com/)
- [SDK](https://github.com/agave-api/react-agave-link)

### Agave File Manager Component
Agave File Manager is a front-end component that allows users to pick files and folders from linked construction software accounts to share with your application.

**Human URL:** [https://docs.agaveapi.com/agave-file-manager/component](https://docs.agaveapi.com/agave-file-manager/component)

#### Tags:

 - Construction, Documents, Files, Front-End

#### Properties

- [Documentation](https://docs.agaveapi.com/agave-file-manager/component)

## Common Properties

- [Portal](https://docs.agaveapi.com)
- [GettingStarted](https://docs.agaveapi.com/quickstart)
- [Authentication](https://docs.agaveapi.com/agave-api/identifiers)
- [Pricing](https://www.agaveapi.com/software-vendors/pricing/)
- [Security](https://security.agaveapi.com/)
- [Partners](https://www.agaveapi.com/partners/)
- [GitHubOrganization](https://github.com/agave-api)
- [SDK](https://github.com/agave-api/react-agave-link)

## Features

| Name | Description |
|------|-------------|
| Unified Construction API | Single REST API to read and write data across 100+ construction and accounting software systems with normalized data models. |
| Agave Link Authentication | Pre-built front-end component for user authentication that handles OAuth flows for all supported construction software platforms. |
| ERP Sync | Automatic synchronization of jobs, financials, timesheets, and cost data between field systems and ERP platforms. |
| AP Invoice Automation | AI-powered invoice capture, job matching, cost code coding, approval routing, and ERP sync for accounts payable workflows. |
| Passthrough Requests | Direct passthrough of requests to source system APIs with Agave handling authentication and protocol translation. |
| Webhooks | Real-time webhook notifications for data changes in connected construction software systems. |
| Sandbox Environments | Sandbox mode for testing integrations without affecting production data in connected systems. |
| Agave File Manager | Pre-built front-end component for browsing and selecting files from connected construction document storage systems. |

## Use Cases

| Name | Description |
|------|-------------|
| Construction Software Integration | Construction software companies integrate with 100+ other platforms via a single API instead of building and maintaining individual integrations. |
| ERP and PM Sync | Automatically sync jobs, cost codes, and financials between project management systems like Procore and ERP systems like QuickBooks or Sage. |
| Invoice Processing Automation | Automate AP invoice capture, job matching, and ERP posting using AI-powered invoice processing workflows. |
| Job Costing | Pull budget, contract, commitment, and cost data from construction software for real-time job cost analysis and reporting. |
| Timesheet Integration | Sync employee timesheets from field systems to accounting ERPs to eliminate manual payroll data entry. |
| Document Management | Enable users to select and share files from connected construction document storage systems using Agave File Manager. |

## Integrations

| Name | Description |
|------|-------------|
| Procore | Full read/write integration with Procore for projects, budgets, contracts, commitments, and documents. |
| Autodesk Build | Integration with Autodesk Build for project management and document storage. |
| QuickBooks Online | Integration with QuickBooks Online for job costing, invoices, and financial data. |
| Sage 100 Contractor | Integration with Sage 100 Contractor for construction job costing and accounting. |
| Sage Intacct | Integration with Sage Intacct cloud ERP for construction financial management. |
| Viewpoint Vista | Integration with Viewpoint Vista for construction ERP including SQL-based data access. |
| ServiceTitan | Integration with ServiceTitan for field service management and job costing. |
| Acumatica | Integration with Acumatica cloud ERP for construction financial management. |
| Foundation | Integration with Foundation construction accounting software. |
| CMiC | Integration with CMiC enterprise construction ERP platform. |

## Artifacts

Machine-readable API specifications organized by format.

### OpenAPI

- [agave-unified-api-openapi](openapi/agave-unified-api-openapi.yml)

### JSON Schema

- [unified-api-budget-list-schema](json-schema/unified-api-budget-list-schema.json)
- [unified-api-budget-schema](json-schema/unified-api-budget-schema.json)
- [unified-api-contract-list-schema](json-schema/unified-api-contract-list-schema.json)
- [unified-api-contract-schema](json-schema/unified-api-contract-schema.json)
- [unified-api-cost-code-list-schema](json-schema/unified-api-cost-code-list-schema.json)
- [unified-api-cost-code-schema](json-schema/unified-api-cost-code-schema.json)
- [unified-api-employee-list-schema](json-schema/unified-api-employee-list-schema.json)
- [unified-api-employee-schema](json-schema/unified-api-employee-schema.json)
- [unified-api-invoice-list-schema](json-schema/unified-api-invoice-list-schema.json)
- [unified-api-invoice-request-schema](json-schema/unified-api-invoice-request-schema.json)
- [unified-api-invoice-schema](json-schema/unified-api-invoice-schema.json)
- [unified-api-link-session-request-schema](json-schema/unified-api-link-session-request-schema.json)
- [unified-api-link-session-schema](json-schema/unified-api-link-session-schema.json)
- [unified-api-project-list-schema](json-schema/unified-api-project-list-schema.json)
- [unified-api-project-schema](json-schema/unified-api-project-schema.json)
- [unified-api-timesheet-list-schema](json-schema/unified-api-timesheet-list-schema.json)
- [unified-api-timesheet-schema](json-schema/unified-api-timesheet-schema.json)
- [unified-api-vendor-list-schema](json-schema/unified-api-vendor-list-schema.json)
- [unified-api-vendor-schema](json-schema/unified-api-vendor-schema.json)

### JSON Structure

- [unified-api-budget-list-structure](json-structure/unified-api-budget-list-structure.json)
- [unified-api-budget-structure](json-structure/unified-api-budget-structure.json)
- [unified-api-contract-list-structure](json-structure/unified-api-contract-list-structure.json)
- [unified-api-contract-structure](json-structure/unified-api-contract-structure.json)
- [unified-api-cost-code-list-structure](json-structure/unified-api-cost-code-list-structure.json)
- [unified-api-cost-code-structure](json-structure/unified-api-cost-code-structure.json)
- [unified-api-employee-list-structure](json-structure/unified-api-employee-list-structure.json)
- [unified-api-employee-structure](json-structure/unified-api-employee-structure.json)
- [unified-api-invoice-list-structure](json-structure/unified-api-invoice-list-structure.json)
- [unified-api-invoice-request-structure](json-structure/unified-api-invoice-request-structure.json)
- [unified-api-invoice-structure](json-structure/unified-api-invoice-structure.json)
- [unified-api-link-session-request-structure](json-structure/unified-api-link-session-request-structure.json)
- [unified-api-link-session-structure](json-structure/unified-api-link-session-structure.json)
- [unified-api-project-list-structure](json-structure/unified-api-project-list-structure.json)
- [unified-api-project-structure](json-structure/unified-api-project-structure.json)
- [unified-api-timesheet-list-structure](json-structure/unified-api-timesheet-list-structure.json)
- [unified-api-timesheet-structure](json-structure/unified-api-timesheet-structure.json)
- [unified-api-vendor-list-structure](json-structure/unified-api-vendor-list-structure.json)
- [unified-api-vendor-structure](json-structure/unified-api-vendor-structure.json)

### JSON-LD

- [agave-unified-context](json-ld/agave-unified-context.jsonld)

### Examples

- [unified-api-budget-example](examples/unified-api-budget-example.json)
- [unified-api-budget-list-example](examples/unified-api-budget-list-example.json)
- [unified-api-contract-example](examples/unified-api-contract-example.json)
- [unified-api-contract-list-example](examples/unified-api-contract-list-example.json)
- [unified-api-cost-code-example](examples/unified-api-cost-code-example.json)
- [unified-api-cost-code-list-example](examples/unified-api-cost-code-list-example.json)
- [unified-api-employee-example](examples/unified-api-employee-example.json)
- [unified-api-employee-list-example](examples/unified-api-employee-list-example.json)
- [unified-api-invoice-example](examples/unified-api-invoice-example.json)
- [unified-api-invoice-list-example](examples/unified-api-invoice-list-example.json)
- [unified-api-invoice-request-example](examples/unified-api-invoice-request-example.json)
- [unified-api-link-session-example](examples/unified-api-link-session-example.json)
- [unified-api-link-session-request-example](examples/unified-api-link-session-request-example.json)
- [unified-api-project-example](examples/unified-api-project-example.json)
- [unified-api-project-list-example](examples/unified-api-project-list-example.json)
- [unified-api-timesheet-example](examples/unified-api-timesheet-example.json)
- [unified-api-timesheet-list-example](examples/unified-api-timesheet-list-example.json)
- [unified-api-vendor-example](examples/unified-api-vendor-example.json)
- [unified-api-vendor-list-example](examples/unified-api-vendor-list-example.json)

## Capabilities

Naftiko capabilities organized as shared per-API definitions composed into customer-facing workflows.

### Shared Per-API Definitions

- [unified-api](capabilities/shared/unified-api.yaml)

### Workflow Capabilities

| Workflow | APIs Combined | Tools | Persona |
|----------|--------------|-------|---------|
| [Agave Construction Data Sync](capabilities/construction-data-sync.yaml) | agave-unified | 8 | Construction Software Engineer |

## Vocabulary

- [Agave Vocabulary](vocabulary/agave-vocabulary.yaml) — Unified taxonomy mapping resources, actions, workflows, and personas

## Rules

- [agave-spectral-rules](rules/agave-spectral-rules.yml) — 24 rules enforcing Agave API conventions

## Maintainers

**FN:** Kin Lane

**Email:** kin@apievangelist.com
