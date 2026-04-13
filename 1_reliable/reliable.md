# Reliable Invoice Delivery

## The Business Case

When invoices land in spam folders, customers never receive them, never pay, and you never know why. Estimates suggest 10–20% of business emails land in junk. For a landscaping company sending 40–50 invoices per month, that's 4–10 invoices per month disappearing silently.

**The fix is straightforward:** Use a business domain, Cloudflare DNS, Microsoft 365 email, configure authentication (SPF/DKIM/DMARC), and integrate with QuickBooks. Cost: domain + ~$6–12/month per mailbox. Timeline: 1–2 hours setup.

---

## The Problem

Spam filters at Gmail, Outlook, Yahoo, and others analyze every invoice email. If the sending domain, email content, or authentication records look suspicious, the message is silently dropped into junk. No bounce-back. No notification. Just lost revenue.

## Why Invoices Get Flagged

| Cause | Impact |
|---|---|
| Sending from Gmail/Yahoo with a business name | Receivers can't verify the sender; filters are suspicious |
| No SPF/DKIM/DMARC records on your domain | Receiving servers have no way to authenticate you |
| Spam-like subject lines ("PAYMENT DUE NOW!", "URGENT") | Pattern-matched as phishing |
| Sending through low-reputation email | Your IP/domain has no track record |

---

## The Solution — Three Essential Steps

**Recommended stack for CL Landscape:**
- Domain registration and DNS: **Cloudflare**
- Business email + mailbox deliverability: **Microsoft 365**
- Invoice sending from QuickBooks Desktop: **Outlook with the Microsoft 365 mailbox**

### Step 1: Use a Business Domain for Email

Do not send invoices from Gmail or Yahoo. Register a business domain and send from a professional email address on that domain.

- **Cost:** Domain registration (Cloudflare) + ~$6–12/month for Microsoft 365 business email
- **Setup time:** ~30 minutes
- **What you'll do:**
  1. Register `cllandscape.com` in Cloudflare Registrar (or transfer an existing domain to Cloudflare)
  2. Sign up for Microsoft 365 for business email
  3. Create a mailbox: `invoices@cllandscape.com` or `billing@cllandscape.com`
  4. Add that account to Outlook on your PC

### Step 2: Configure Email Authentication (SPF, DKIM, DMARC)

These are three DNS records that tell receiving mail servers your email is legitimate. Your email provider will give you the exact records to add.

- **Cost:** $0 (included with Microsoft 365)
- **Setup time:** ~20 minutes
- **What happens:** Receiving servers verify your email is genuine, dramatically reducing spam folder risk
- **Implementation path:**
  1. Log into Cloudflare DNS
  2. Add the three DNS records provided by Microsoft 365:
     - **SPF** — tells receiving servers which mail servers can send on your behalf
     - **DKIM** — adds a cryptographic signature to every email
     - **DMARC** — tells servers what to do if SPF or DKIM fails
  3. Publish these records; DNS propagation takes 1–24 hours

**Recommendation:** Use Cloudflare for domain + DNS and Microsoft 365 for email. This is a clean, low-complexity setup that integrates well with QuickBooks Desktop through Outlook.

### Step 3: Configure QuickBooks Desktop to Send Through Your Business Email

QuickBooks Desktop doesn't send through Intuit's servers. Instead, it sends through whatever email account you configure on your PC. The fix: connect it to your business email.

- **Setup time:** ~5 minutes
- **What you'll do:**
  1. In QuickBooks Desktop: **Edit → Preferences → Send Forms**
  2. Choose **Outlook** (if you've added your business email account to Outlook, which you will have in Step 1)
  3. Send a test invoice to confirm it goes out from your business email address
  4. Optional: Enable read receipts if your email client supports them

---

## Best Practices for Email Content

Subject lines and body copy affect spam filter scores. Keep it simple and professional.

**Subject line:** `Invoice #1042 — CL Landscape — April Services`  
**Avoid:** All-caps words, excessive punctuation, or urgency triggers like "PAYMENT DUE NOW"

**Body:** Short and professional — 3–5 sentences. Include your business name, phone, and address in the signature.

**Attachments:** Send invoices as PDF files (no macros, universally trusted). Name clearly: `CL_Landscape_Invoice_1042.pdf`

---

## Customer Confirmation

Ask new customers to add your email address to their contacts:

> *"To make sure you always receive invoices from us, please add `invoices@cllandscape.com` to your contacts."*

This creates a positive sender signal that overrides most spam filters.

---

## Confirming Delivery

Even with authentication in place, confirm invoices arrive for first-time customers:

1. **Request read receipts** when sending (most email clients support this)
2. **Follow up by text or phone** after 2–3 days if you don't see payment — quickest confirmation method
3. **Check bounce notifications** — undeliverable emails typically bounce back within minutes

---

## Quick-Start Implementation

**Week 1 — Domain & Email Setup (~1.5 hours)**
- [ ] Register a business domain in Cloudflare Registrar (or transfer your existing domain to Cloudflare)
- [ ] Sign up for Microsoft 365 for business email
- [ ] Create an `invoices@cllandscape.com` mailbox
- [ ] Add the account to Outlook on your PC

**Week 1–2 — Email Authentication (~30 minutes)**
- [ ] Log into Cloudflare DNS and add the SPF, DKIM, and DMARC records provided by Microsoft 365
- [ ] Allow 24 hours for DNS propagation

**Week 2 — QuickBooks Configuration (~5 minutes)**
- [ ] In QuickBooks Desktop, set email method to Outlook: **Edit → Preferences → Send Forms**
- [ ] Send a test invoice to confirm it goes out from your business email address

**Ongoing**
- [ ] Use the new subject line format and send professional, clean invoice emails
- [ ] Ask new customers to add your email address to their contacts
- [ ] Follow up by phone if payment doesn't arrive within 3 days
- [ ] Use read receipts for first-time invoices when available

---

*Last updated: April 12, 2026*
