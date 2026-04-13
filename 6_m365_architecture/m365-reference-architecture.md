# M365 Reference Architecture

## 1. Platform Components
- SharePoint Online: central document library for estimates, quotes, contracts, and renewals
- Microsoft Lists: pipeline record for each customer contract lifecycle
- Power Automate: reminder, assignment, and escalation workflows
- Microsoft Teams: daily coordination and weekly renewal review
- Outlook: standardized outbound communications for quote and renewal steps
- QuickBooks Desktop 2019: invoices, receivables, and accounting records

## 2. Logical Architecture

### Document System (SharePoint)
Primary library: `SalesOps`

Folders:
- `01_Estimates`
- `02_Quotes`
- `03_Contracts`
- `04_Renewals`

Document conventions:
- File naming: `CustomerName-Service-YYYY-MM-DD-<Stage>-<ContractID>`
- Version history: enabled
- Signed contract folder: restricted edit permissions
- Retention: keep signed contracts and renewal letters per policy

### Pipeline System (Microsoft Lists)
List name: `Contract Pipeline`

One row per contract.
A contract can move stages but keeps the same `ContractID`.

Stage values:
- Estimate
- Quote Sent
- Contract Pending Signature
- Active
- Upcoming Renewal (90)
- Pricing Review (60)
- Renewal Sent (30)
- Renewed
- Declined

RenewalStatus values:
- Upcoming Renewal (90)
- Pricing Review (60)
- Renewal Sent (30)
- Renewed
- Declined

### Workflow System (Power Automate)
Automation handles:
- Date-based reminders (90, 60, 30 days to end date)
- Owner notifications in Teams and Outlook
- Escalation when stage is overdue

## 3. Data Flow
1. Estimate created and document stored in SharePoint.
2. Pipeline row created/updated in Microsoft Lists.
3. Quote sent and status/date updated in Lists.
4. Signed contract saved in SharePoint and row moved to Active.
5. ContractEndDate triggers 90/60/30 reminders via Power Automate.
6. Renewal action updates `Stage` and `RenewalStatus` and stores renewal documents.
7. `ContractID` is mirrored into `QBInvoiceMemoRef` in QuickBooks for traceability.

## 4. Security and Governance
- Security groups:
  - `SalesOps-Owners`
  - `SalesOps-Editors`
  - `SalesOps-ReadOnly`
- Principle of least privilege for signed contract documents
- Multi-factor authentication required for all M365 user accounts
- Change logging:
  - SharePoint version history
  - List item modified metadata

## 5. Operational Cadence
- Daily: owner checks new reminders and pending actions
- Weekly: Teams renewal standup with overdue review
- Monthly: KPI review (renewal rate, cycle time, on-time renewal completion)

## 6. Integration Boundary with QuickBooks
QuickBooks Desktop remains the accounting system of record.

Required cross-reference fields:
- ContractID
- CustomerName
- ServiceType
- ContractStartDate
- ContractEndDate
- QBInvoiceMemoRef

Rule:
- Do not create duplicate accounting balances in M365 tools.
M365 manages operational workflow and document lifecycle only.
