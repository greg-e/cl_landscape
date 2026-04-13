# M365 Architecture for CL Landscape

This folder defines a practical Microsoft 365 architecture to support the process:
Estimate -> Quote -> Contract -> Renewal.

Goals:
- Keep software cost low by using M365 tools already included in licensing
- Improve document control and accountability
- Automate renewal reminders and follow-up tasks
- Keep QuickBooks Desktop 2019 as accounting system of record

## Contents
- `m365-reference-architecture.md`: platform architecture, data flow, and controls
- `m365-lists-schema.md`: Microsoft Lists structure and required fields
- `power-automate-renewal-flows.md`: reminder and escalation flow design
- `customer-lifecycle-template.csv`: Excel-ready lifecycle tracking template
- `customer-lifecycle-template-guide.md`: setup and usage instructions for the template
- `customer-lifecycle-template-mobile.csv`: mobile-first Excel lifecycle template
- `excel-mobile-optimization.md`: phone/tablet optimization standard for Excel use

## Canonical Naming Standard
Use one shared field naming model across SharePoint, Microsoft Lists, Power Automate, and Excel templates.

Primary key and references:
- `ContractID` = lifecycle anchor key
- `QBInvoiceMemoRef` = QuickBooks cross-reference (must match `ContractID`)

Primary workflow fields:
- `Stage` = lifecycle stage (Estimate through Declined)
- `RenewalStatus` = renewal-only state (90/60/30, Renewed, Declined)
- `Owner`, `NextAction`, `NextActionDate`, `LastActionDate` = operational accountability

## Scope Boundaries
In scope:
- Sales and contract operations workflow management
- Document storage and version control
- Renewal scheduling and reminders

Out of scope:
- Invoicing and accounting ledger (QuickBooks Desktop remains authoritative)
- Full CRM replacement
- Field service route optimization

## Recommended Rollout Order
1. Build SharePoint document library and folder permissions.
2. Create Microsoft List for contract pipeline.
3. Stand up Power Automate 90/60/30-day reminders.
4. Add Teams channel for weekly renewal review.
5. Monitor KPIs for 30 days before expanding automation.
