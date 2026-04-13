# Customer Lifecycle Excel Template Guide

## Purpose
Use this template to track a customer from Estimate -> Quote -> Contract -> Renewal in one sheet.

## File
- `customer-lifecycle-template.csv`
- `customer-lifecycle-template-mobile.csv`

Open directly in Excel and save as `.xlsx` if needed.

## Mobile Recommendation
Use `customer-lifecycle-template-mobile.csv` for phone-first work.

It places action fields first so users can update status with minimal horizontal scrolling:
- ContractID
- CustomerName
- Stage
- Owner
- NextAction
- NextActionDate
- RenewalStatus
- ContractEndDate

## Required Fields
- ContractID
- CustomerName
- ServiceType
- Stage
- Owner
- ContractStartDate
- ContractEndDate
- CurrentPrice
- QBInvoiceMemoRef
- LastActionDate

## Status Values
Stage:
- Estimate
- Quote Sent
- Contract Pending Signature
- Active
- Upcoming Renewal (90)
- Pricing Review (60)
- Renewal Sent (30)
- Renewed
- Declined

EstimateStatus:
- Draft
- Approved
- Rejected

QuoteStatus:
- Draft
- Sent
- Accepted
- Rejected
- Expired

RenewalStatus:
- Upcoming Renewal (90)
- Pricing Review (60)
- Renewal Sent (30)
- Renewed
- Declined

## Operating Rules
1. Keep one row per contract lifecycle.
2. Keep ContractID consistent across documents and QBInvoiceMemoRef.
3. Update LastActionDate any time a stage changes.
4. Update RenewalStatus when the contract enters renewal windows.
5. Never delete historical rows; mark final outcome in Stage, RenewalStatus, and OutcomeReason.

## Suggested Excel Enhancements
1. Add data validation dropdowns for status columns.
2. Add conditional formatting for contracts in renewal windows.
3. Freeze top row and convert range to Table format.
4. Create filtered views by Owner and RenewalStatus.
5. On mobile-focused sheets, keep the first 8 columns locked as the action lane.
