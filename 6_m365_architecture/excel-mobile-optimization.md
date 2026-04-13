# Excel Mobile Optimization Standard

## Goal
Make the lifecycle tracker fast to update on a phone with minimal horizontal scrolling and minimal typing.

## Use the Mobile Template
Primary file:
- `customer-lifecycle-template-mobile.csv`

Reason:
- Critical action fields are in the first 8 columns, so users can update stage and next steps without scrolling far.

## Mobile-First Column Order
Keep these columns first and never move them:
1. ContractID
2. CustomerName
3. Stage
4. Owner
5. NextAction
6. NextActionDate
7. RenewalStatus
8. ContractEndDate

Secondary columns (contact and pricing) can remain to the right.

## Required Dropdowns
Create validation lists for:
- Stage: Estimate, Quote Sent, Contract Pending Signature, Active, Upcoming Renewal (90), Pricing Review (60), Renewal Sent (30), Renewed, Declined
- RenewalStatus: Upcoming Renewal (90), Pricing Review (60), Renewal Sent (30), Renewed, Declined
- Owner: team member names only

This reduces typing errors on mobile keyboards.

## Formatting Rules for Mobile Visibility
1. Convert data range to an Excel Table.
2. Freeze top row.
3. Use Wrap Text for NextAction and Notes.
4. Increase row height slightly for touch accuracy.
5. Set date columns to short date format.

## Mobile Quick Filters
Create saved views (or quick filters):
- My Work Today: Owner = current user, NextActionDate <= Today + 1
- Renewal Window: RenewalStatus in Upcoming Renewal (90), Pricing Review (60), Renewal Sent (30)
- Overdue: NextActionDate < Today and Stage not in Renewed, Declined

## Data Entry Rules
1. Update Stage and RenewalStatus first.
2. Update NextAction and NextActionDate second.
3. Always stamp LastActionDate.
4. Keep ContractID unchanged.

## Weekly Hygiene Checklist
- Remove blank Owner values.
- Resolve overdue items older than 7 days.
- Confirm all records with upcoming end dates have a renewal status.
- Confirm QBInvoiceMemoRef matches ContractID.
