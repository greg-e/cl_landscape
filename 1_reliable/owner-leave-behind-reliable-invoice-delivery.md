# CL Landscape
## Invoice Delivery Plan
### For CL Landscape Ownership

Date: April 12, 2026  
Prepared for: Owner, CL Landscape  
Prepared by: Greg Ehrenberg

---

## Decision Summary

Approve this setup:
1. Cloudflare for domain registration and DNS
2. Microsoft 365 for business email
3. Outlook as QuickBooks Desktop send method
4. SPF, DKIM, and DMARC enabled in DNS

Why: improves invoice inbox delivery, shortens time to payment, and reduces avoidable follow-up.

---

## Cost and Effort

- Domain: about $10 to $20 per year
- Microsoft 365 mailbox: about $6 to $12 per month
- One-time setup: about 1 to 2 hours
- Ongoing admin: minimal

---

## Implementation Plan

### Phase 1 - Setup (same day)
- Register or transfer domain to Cloudflare
- Create Microsoft 365 mailbox (example: invoices@cllandscape.com)
- Add mailbox to Outlook on invoicing PC

### Phase 2 - Authentication (same day)
- Add SPF in Cloudflare DNS
- Add DKIM records and enable DKIM in Microsoft 365
- Add DMARC in Cloudflare DNS
- Verify DNS propagation

### Phase 3 - QuickBooks Go-Live (same day)
- QuickBooks Desktop: Edit -> Preferences -> Send Forms
- Set method to Outlook
- Send test invoice and confirm From address is business domain mailbox

---

## Operating Standard

- Subject line format: Invoice #1234 - CL Landscape - Service Month
- PDF invoices only
- Ask new customers to add invoices mailbox to contacts
- If unpaid after 2 to 3 days, follow up by text or phone

---

## 30-Day Success Measures

- Fewer reports of missing invoices
- Faster average payment turnaround
- Fewer resend/recovery actions

---

## Approval

Approve implementation of the recommended invoice delivery setup.

Owner decision: ____________________________

Date: ____________________________

Signature: ____________________________
