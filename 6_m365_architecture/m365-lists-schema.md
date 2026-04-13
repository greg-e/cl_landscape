# Microsoft Lists Schema: Contract Pipeline

## List Definition
- List name: Contract Pipeline
- Record grain: one row per contract
- Primary key: ContractID

## Canonical Field Set
Use these fields across Microsoft Lists, Excel templates, and Power Automate.

Core identity and ownership:
- ContractID (Single line text, Required)
- CustomerID (Single line text, Optional)
- CustomerName (Single line text, Required)
- ServiceType (Choice, Required)
- Owner (Person, Required)

Lifecycle stages:
- Stage (Choice, Required)
- RenewalStatus (Choice, Optional)

Estimate and quote tracking:
- EstimateID (Single line text, Optional)
- EstimateDate (Date, Optional)
- EstimatedAmount (Currency, Optional)
- EstimateStatus (Choice, Optional)
- QuoteID (Single line text, Optional)
- QuoteSentDate (Date, Optional)
- QuoteExpiryDate (Date, Optional)
- QuoteAmount (Currency, Optional)
- QuoteStatus (Choice, Optional)

Contract tracking:
- ContractSentDate (Date, Optional)
- ContractSignedDate (Date, Optional)
- ContractStartDate (Date, Required)
- ContractEndDate (Date, Required)
- ContractTermMonths (Number, Optional)
- BillingFrequency (Choice, Optional)

Pricing and renewal:
- CurrentPrice (Currency, Required)
- ProposedRenewalPrice (Currency, Optional)
- IncreasePercent (Number, Optional)
- Renewal90Date (Date, Optional)
- Renewal60Date (Date, Optional)
- Renewal30Date (Date, Optional)
- RenewalSentDate (Date, Optional)
- RenewalDecisionDate (Date, Optional)
- OutcomeReason (Choice, Optional)

Action and controls:
- NextAction (Single line text, Optional)
- NextActionDate (Date, Optional)
- LastActionDate (Date, Required)
- QBInvoiceMemoRef (Single line text, Required)
- Notes (Multiple lines text, Optional)

Optional automation stamp fields:
- Reminder90SentDate (Date, Optional)
- Reminder60SentDate (Date, Optional)
- Reminder30SentDate (Date, Optional)
- EscalationSentDate (Date, Optional)

## Choice Sets
ServiceType:
- Maintenance
- Install
- Seasonal Add-On
- Irrigation
- Other

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

RenewalStatus:
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

BillingFrequency:
- Monthly
- Quarterly
- Annual
- Other

OutcomeReason:
- Renewed
- Price Sensitivity
- Scope Mismatch
- Service Issues
- Budget Freeze
- Competitor
- Other

## Useful List Views
1. My Work Today
- Filter: Owner = [Me] and NextActionDate <= [Today + 1]

2. 90-Day Renewals
- Filter: RenewalStatus = Upcoming Renewal (90)

3. Overdue Renewal Tasks
- Filter: NextActionDate < [Today] and Stage not in Renewed, Declined

4. Recently Signed
- Filter: ContractSignedDate in last 30 days

## Validation Rules
- ContractEndDate must be greater than ContractStartDate.
- ProposedRenewalPrice must be greater than 0 when Stage in Pricing Review (60), Renewal Sent (30).
- IncreasePercent should be populated when ProposedRenewalPrice is entered.
- RenewalStatus should be populated when ContractEndDate is within 90 days.
- QBInvoiceMemoRef must equal ContractID for reconciliation integrity.

## Traceability Rule
ContractID must match:
- SharePoint document file names
- QBInvoiceMemoRef
- Renewal communications and exported reports

This is the anchor key used for reconciliation.
