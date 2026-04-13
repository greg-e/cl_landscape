# Simple Low-Cost Flow: Estimate -> Quote -> Contract -> Renewal

## Decision Note (April 12, 2026)
If Jobber cost is a concern, CL Landscape should run a simple operational flow first, then add Jobber only if the team outgrows the manual process.

Primary goal:
- Keep the sales-to-renewal process consistent and fast without adding expensive software complexity.

---

## Recommended Operating Model
Use a two-lane model:

1. Lane A (default now): No-new-platform flow
- Estimate/quote/contract managed with templates + shared folders + QuickBooks Desktop references
- Renewal pipeline managed in a simple tracker (spreadsheet)

1A. Lane A+ (recommended with M365): Organized low-cost flow
- Keep the same Estimate -> Quote -> Contract -> Renewal process
- Use Microsoft 365 tools to improve structure, reminders, and document control

2. Lane B (optional later): Jobber-assisted flow
- Add Jobber only for stages where it clearly saves admin time (proposal tracking, renewals, reminders)
- Keep QuickBooks Desktop 2019 as accounting system of record

Rule:
- Do not subscribe to higher-cost tooling until Lane A KPIs show process strain.

---

## End-to-End Workflow (Simple SOP)

### Step 1: Estimate
Owner: Estimator

Process:
1. Build estimate from standard scope template.
2. Save estimate as: CustomerName-Service-YYYY-MM-DD-EST.
3. Record target gross margin and key assumptions (labor hours, materials, frequency).

Output:
- Approved internal estimate

### Step 2: Quote
Owner: Sales/Owner

Process:
1. Convert estimate to customer-facing quote (clear scope, exclusions, start window).
2. Include payment options accepted today (check, Zelle, ACH when active).
3. Add expiration date (for example, 14 days).

Output:
- Sent quote with expiration date

### Step 3: Contract
Owner: Sales Admin/Owner

Process:
1. Convert accepted quote into one-page contract template.
2. Confirm term dates, service frequency, cancellation terms, and renewal notice window.
3. Assign Contract ID and store in shared contract folder.
4. Add Contract ID to QuickBooks invoice memo/custom field.

Output:
- Signed contract linked to accounting record

### Step 4: Renewal
Owner: Renewal Owner

Process:
1. At 90 days before term end, move contract to Upcoming Renewal.
2. At 60 days, complete pricing review (flat, modest increase, or targeted increase).
3. At 30 days, send renewal offer with old vs new terms clearly shown.
4. Track outcome: Renewed, Declined, Pending.

Output:
- Closed renewal decision before expiration

---

## Minimum Tool Stack (Lowest Cost)

Required:
- QuickBooks Desktop 2019 (invoices, receivables, accounting)
- Shared folder structure (contracts, quotes, signed documents)
- Spreadsheet tracker for renewal pipeline

Optional:
- E-sign tool only if signature turnaround is slow
- Jobber only if manual admin load becomes too high

---

## M365 Setup (Best Organization for Low Added Cost)

Use these Microsoft 365 components:
- SharePoint: single document library for Estimates, Quotes, Contracts, and Renewals
- Microsoft Lists: contract pipeline tracker instead of an unmanaged spreadsheet
- Power Automate: 90/60/30-day reminder flows and status-change alerts
- Teams: one channel for renewal coordination, owner accountability, and weekly review
- Outlook: standardized email templates for quote send and renewal outreach

Suggested SharePoint structure:
- SalesOps/
- SalesOps/01_Estimates/
- SalesOps/02_Quotes/
- SalesOps/03_Contracts/
- SalesOps/04_Renewals/

Document rules:
- Require Contract ID in file name and list item
- Enforce version history and permissions by folder
- Keep signed contracts in one protected location only

---

## M365 Workflow Mapping (Estimate -> Quote -> Contract -> Renewal)

Step 1: Estimate
- Store estimate document in SharePoint 01_Estimates
- Create/update corresponding item in Microsoft Lists with stage = Estimate

Step 2: Quote
- Move or copy finalized file to 02_Quotes
- Send quote with Outlook template and record Sent Date in Lists

Step 3: Contract
- Store signed agreement in 03_Contracts
- Update Lists record with Start Date, End Date, and Contract ID
- Keep Contract ID matched to QuickBooks memo/custom field

Step 4: Renewal
- Power Automate sends reminders at 90/60/30 days before End Date
- Renewal owner updates stage in Lists: Upcoming, Review, Sent, Renewed, Declined
- Store renewal documents in 04_Renewals

Outcome:
- A low-cost workflow with visible ownership, consistent records, and automatic reminders

---

## Renewal Tracker Fields (Spreadsheet)
Use one row per contract with these columns:
- Customer
- Contract ID
- Service Type
- Start Date
- End Date
- Current Price
- Proposed Price
- Increase %
- 90-Day Date
- 60-Day Date
- 30-Day Date
- Renewal Stage
- Owner
- Outcome Reason

This gives most of the benefit of a software pipeline at near-zero added cost.

---

## Pricing Rule (Simple)

Use three pricing outcomes only:
1. Flat renewal
- Account is healthy and service load is stable.

2. Modest increase (example: 3-5%)
- Inflation/labor pressure present but account is operationally clean.

3. Targeted increase (example: 6-10%)
- Underpriced account, high complexity, or repeated service friction.

Approval rule:
- Any exception below target minimum increase requires owner sign-off.

---

## When to Add Jobber (Cost Trigger)
Adopt Jobber only if 2 or more conditions are true for 2 straight months:
- More than 75 active contracts in renewal cycle
- Renewal follow-up tasks are regularly missed
- Time from quote acceptance to signed contract is too slow
- Team spends excessive admin time searching for latest contract status
- M365 process automation is still not enough to keep renewals on time

If these triggers appear, start with a limited Jobber rollout focused on:
- Proposal acceptance tracking
- Renewal reminders
- Contract status visibility

Keep QuickBooks Desktop as financial system of record.

---

## 30-Day Implementation Plan
1. Finalize estimate, quote, and contract templates.
2. Set naming convention and Contract ID standard.
3. Build renewal tracker with 90/60/30-day views.
4. Assign one Renewal Owner.
5. Run this process on all new contracts and next renewal cohort.
6. Review weekly for missed steps and cycle time.

---

## Success Metrics (Keep Simple)
Track monthly:
- Quote-to-contract conversion rate
- Average days: quote sent -> signed contract
- Renewal rate
- Realized renewal increase %
- Number of contracts renewed before expiration

---

## Bottom Line
CL Landscape can run Estimate -> Quote -> Contract -> Renewal effectively without immediate Jobber expansion.

Start with a disciplined template + tracker workflow now.
Add Jobber later only when volume or admin burden clearly justifies the cost.
