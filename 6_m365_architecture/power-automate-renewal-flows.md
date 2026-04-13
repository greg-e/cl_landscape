# Power Automate Flows: Renewal Management

## Flow 1: 90-Day Reminder
Purpose:
- Alert owner that renewal window has opened

Trigger:
- Scheduled daily run

Filter logic:
- `ContractEndDate - Today = 90`
- `Stage = Active`
- `Reminder90SentDate` is blank

Actions:
1. Update Stage to `Upcoming Renewal (90)`.
2. Update RenewalStatus to `Upcoming Renewal (90)`.
3. Send Outlook email to Owner.
4. Post Teams message to Renewal channel.
5. Set Reminder90SentDate = Today.
6. Set LastActionDate = Today.

## Flow 2: 60-Day Pricing Review Reminder
Purpose:
- Force pricing review before customer outreach

Trigger:
- Scheduled daily run

Filter logic:
- `ContractEndDate - Today = 60`
- `Stage in Active, Upcoming Renewal (90)`
- `Reminder60SentDate` is blank

Actions:
1. Update Stage to `Pricing Review (60)`.
2. Update RenewalStatus to `Pricing Review (60)`.
3. Send Owner email with pricing checklist.
4. Create Planner task (optional) due in 7 days.
5. Set Reminder60SentDate = Today.
6. Set LastActionDate = Today.

## Flow 3: 30-Day Renewal Send Reminder
Purpose:
- Ensure renewal communication is sent before expiration risk

Trigger:
- Scheduled daily run

Filter logic:
- `ContractEndDate - Today = 30`
- `Stage in Pricing Review (60), Upcoming Renewal (90), Active`
- `Reminder30SentDate` is blank

Actions:
1. Update Stage to `Renewal Sent (30)` if not already sent.
2. Update RenewalStatus to `Renewal Sent (30)`.
3. Send Owner email with template link.
4. Post Teams reminder with customer and end date.
5. Set Reminder30SentDate = Today.
6. Set LastActionDate = Today.

## Flow 4: Overdue Escalation
Purpose:
- Escalate contracts close to expiration without closed outcome

Trigger:
- Scheduled daily run

Filter logic:
- `ContractEndDate - Today <= 14`
- `Stage not in Renewed, Declined`
- `EscalationSentDate` is blank OR older than 7 days

Actions:
1. Send escalation email to Owner and Manager.
2. Post Teams alert tagged as High Priority.
3. Add `Overdue` keyword in Notes.
4. Set EscalationSentDate = Today.
5. Set LastActionDate = Today.

## Flow 5: Outcome Capture
Purpose:
- Keep reporting clean when contract is closed

Trigger:
- When Stage changes to Renewed or Declined

Actions:
1. Require OutcomeReason if Stage = Declined.
2. Set RenewalStatus to match Stage value.
3. Stamp LastActionDate = Today.
4. Notify finance/admin for follow-up handling.

## Operating Notes
- Keep all date checks in local business timezone.
- Use `ContractEndDate` as the date source for renewal calculations.
- Use reminder stamp fields to prevent duplicate notifications.
- Test flows with a pilot list before production deployment.
