# Agave GraphQL Schema

## Overview

This conceptual GraphQL schema represents the Agave Unified Construction API domain model. Agave provides a single API layer that normalizes data across 100+ construction and accounting software systems including Procore, Autodesk Build, QuickBooks, Sage 100 Contractor, Sage Intacct, Viewpoint Vista, Foundation, ServiceTitan, Acumatica, and CMiC.

The schema covers all primary resource types surfaced by the Agave REST API and organized into logical groupings: project management, job costing, contracts, commitments, invoicing, payments, field operations, personnel, equipment, and platform administration.

## Schema Source

- **Type**: Conceptual (derived from Agave REST API documentation)
- **Base API**: https://api.agaveapi.com
- **Documentation**: https://docs.agaveapi.com/
- **API Reference**: https://docs.agaveapi.com/reference
- **Schema File**: agave-schema.graphql

## Domain Coverage

### Project Management
Types covering the core project lifecycle in construction: `Project`, `ProjectDetails`, `ProjectStatus`, `ProjectType`, `JobSite`, `JobSiteDetails`.

### Job Costing
Financial tracking types: `JobCost`, `JobCostDetails`, `CostCode`, `CostCodeDetails`, `BudgetItem`, `BudgetItemDetails`, `BudgetRevision`.

### Contracts and Commitments
Procurement and subcontractor types: `PO`, `PurchaseOrder`, `POLineItem`, `Subcontract`, `SubcontractDetails`, `Commitment`, `CommitmentLineItem`.

### Invoicing and Payments
Accounts payable types: `Invoice`, `InvoiceDetails`, `InvoiceLineItem`, `Payment`, `PaymentDetails`, `Retainage`.

### Change Management
Change order workflow types: `Change`, `ChangeOrder`, `ChangeOrderDetails`, `ChangeOrderLineItem`.

### Field Operations
RFI, submittal, and daily log types: `RFI`, `RFIDetails`, `RFIStatus`, `Submittal`, `SubmittalDetails`, `SubmittalStatus`, `DailyLog`, `DailyLogDetails`, `Observation`.

### Contacts and Companies
Directory types: `Contact`, `ContactDetails`, `Company`, `CompanyDetails`, `CompanyType`, `Vendor`, `VendorDetails`, `Subcontractor`.

### Personnel and Equipment
Workforce and asset types: `Employee`, `EmployeeDetails`, `Equipment`, `EquipmentDetails`, `EquipmentUsage`, `Timecard`, `TimecardDetails`.

### Documents
Drawing and specification types: `Drawing`, `DrawingDetails`, `Specification`.

### Platform Administration
Auth and webhook types: `APIKey`, `Token`, `Webhook`, `WebhookEvent`.

## Root Operations

### Query
- `projects(filter: ProjectFilter, pagination: PaginationInput): ProjectConnection`
- `project(id: ID!): Project`
- `jobCosts(projectId: ID!, filter: JobCostFilter): JobCostConnection`
- `costCodes(filter: CostCodeFilter): CostCodeConnection`
- `budgetItems(projectId: ID!): [BudgetItem!]`
- `purchaseOrders(filter: POFilter): POConnection`
- `subcontracts(filter: SubcontractFilter): SubcontractConnection`
- `commitments(projectId: ID!): [Commitment!]`
- `invoices(filter: InvoiceFilter): InvoiceConnection`
- `payments(filter: PaymentFilter): PaymentConnection`
- `changeOrders(projectId: ID!): [ChangeOrder!]`
- `rfis(projectId: ID!): [RFI!]`
- `submittals(projectId: ID!): [Submittal!]`
- `dailyLogs(projectId: ID!, filter: DailyLogFilter): [DailyLog!]`
- `contacts(filter: ContactFilter): ContactConnection`
- `companies(filter: CompanyFilter): CompanyConnection`
- `vendors(filter: VendorFilter): VendorConnection`
- `employees(filter: EmployeeFilter): EmployeeConnection`
- `equipment(filter: EquipmentFilter): EquipmentConnection`
- `timecards(filter: TimecardFilter): TimecardConnection`
- `drawings(projectId: ID!): [Drawing!]`
- `specifications(projectId: ID!): [Specification!]`
- `webhooks: [Webhook!]`

### Mutation
- `createProject(input: CreateProjectInput!): Project`
- `updateProject(id: ID!, input: UpdateProjectInput!): Project`
- `createBudgetItem(input: CreateBudgetItemInput!): BudgetItem`
- `createPurchaseOrder(input: CreatePOInput!): PurchaseOrder`
- `createSubcontract(input: CreateSubcontractInput!): Subcontract`
- `createInvoice(input: CreateInvoiceInput!): Invoice`
- `approveInvoice(id: ID!): Invoice`
- `createChangeOrder(input: CreateChangeOrderInput!): ChangeOrder`
- `createRFI(input: CreateRFIInput!): RFI`
- `createSubmittal(input: CreateSubmittalInput!): Submittal`
- `createDailyLog(input: CreateDailyLogInput!): DailyLog`
- `createTimecard(input: CreateTimecardInput!): Timecard`
- `createWebhook(input: CreateWebhookInput!): Webhook`
- `deleteWebhook(id: ID!): Boolean`

## Integration Notes

Agave normalizes field names and data structures across source systems. A `Project` queried from Procore and a `Project` queried from Sage 100 Contractor return the same GraphQL type with the same fields. The `sourceData` field on each type provides access to the raw, unmodified response from the underlying system when passthrough detail is needed.

Authentication uses bearer tokens obtained via the Agave Link OAuth component. The `API-Version` and `Account-Token` headers required by the REST API map to GraphQL context headers in this schema.
