# Step 2: Configure Email Authentication (SPF, DKIM, DMARC)

This guide gives you a complete, practical sequence for configuring email authentication so your business email is trusted and delivered reliably.

## Goal of Step 2

Set up and validate:

1. SPF: declares which mail servers are allowed to send for your domain.
2. DKIM: cryptographically signs outgoing mail so recipients can verify integrity and origin.
3. DMARC: enforces policy and reporting by telling receivers what to do when SPF/DKIM checks fail.

When done correctly, this reduces spoofing and improves inbox placement.

---

## Before You Start

Gather these prerequisites first:

1. Access to your DNS hosting provider (where domain TXT/CNAME records are managed).
2. Access to your email platform admin portal (for example, Microsoft 365 Exchange Admin Center).
3. A list of all systems that send email as your domain (Microsoft 365, CRM, invoicing tools, marketing platforms, ticketing apps, etc.).
4. A testing mailbox at a major provider (Gmail or Outlook.com) for validation.
5. Optional but recommended: access to a DMARC report viewer (for easier aggregate report analysis).

---

## Recommended Rollout Order

Follow this exact order:

1. SPF first.
2. DKIM second.
3. DMARC in monitoring mode (`p=none`) first, then enforce later (`quarantine` or `reject`).

---

## Part A: Configure SPF

### 1. Build Your Authoritative Sender Inventory

Create a sender list before touching DNS:

1. Primary mail platform (for example, Microsoft 365).
2. Third-party senders (billing, support, forms, newsletter tools).
3. On-prem SMTP relays or printers/scanners (if any).

If a system can send as `@yourdomain.com`, it must be accounted for in SPF and/or DKIM alignment strategy.

### 2. Check for Existing SPF Record

In DNS, look for a TXT record at the root domain (host/name often `@`) that starts with:

`v=spf1`

Rules:

1. Only one SPF TXT record is allowed per domain.
2. Multiple SPF records cause failures at some receivers.

### 3. Create or Consolidate SPF Record

Typical Microsoft 365 baseline SPF is:

`v=spf1 include:spf.protection.outlook.com -all`

If you have additional legitimate senders, add their include mechanisms as documented by those vendors.

Example combined record (illustrative only):

`v=spf1 include:spf.protection.outlook.com include:sendgrid.net include:mailgun.org -all`

Guidance:

1. Start with `~all` (soft fail) only if you are uncertain about all senders.
2. Move to `-all` (hard fail) once inventory is complete.
3. Keep SPF under DNS/lookup limits (SPF has a hard limit of 10 DNS lookups).

### 4. Publish SPF in DNS

1. Record type: TXT
2. Host/Name: `@` (or your DNS provider equivalent)
3. Value: your final SPF string
4. TTL: 3600 seconds (or provider default)

### 5. Validate SPF

1. Send a message from your domain to a Gmail mailbox.
2. In Gmail, open message details and confirm SPF = PASS.
3. Repeat with at least one internal and one external sender path.

---

## Part B: Configure DKIM

### 1. Enable DKIM in Your Mail Platform

For Microsoft 365 custom domains, the usual flow is:

1. Create the DKIM CNAME records in DNS (selectors provided by Microsoft).
2. Enable DKIM signing for the domain in Microsoft 365 after DNS propagates.

Common selector hostnames used by Microsoft 365:

1. `selector1._domainkey`
2. `selector2._domainkey`

Target values are tenant-specific and must come from your Microsoft 365 admin portal instructions.

### 2. Add DKIM DNS Records

1. Record type: CNAME
2. Host/Name: `selector1._domainkey`
3. Value/Target: Microsoft-provided selector1 target

And:

1. Record type: CNAME
2. Host/Name: `selector2._domainkey`
3. Value/Target: Microsoft-provided selector2 target

Use exactly what your platform provides; do not guess tenant values.

### 3. Turn On DKIM Signing

After CNAME records resolve publicly:

1. Go to Microsoft 365 Defender or Exchange admin DKIM settings (UI may vary).
2. Enable DKIM for your domain.
3. Confirm status shows Enabled.

### 4. Validate DKIM

1. Send a test email to Gmail.
2. Inspect headers/details and confirm `dkim=pass`.
3. Confirm the signing domain aligns with your From domain (alignment matters for DMARC).

---

## Part C: Configure DMARC

### 1. Start in Monitoring Mode

Create DMARC as TXT record at `_dmarc.yourdomain.com` with policy `p=none` first.

Starter record:

`v=DMARC1; p=none; rua=mailto:dmarc-reports@yourdomain.com; ruf=mailto:dmarc-forensics@yourdomain.com; fo=1; adkim=s; aspf=s; pct=100`

Notes:

1. `rua` = aggregate reports (highly recommended).
2. `ruf` = forensic/failure reports (optional; many providers send limited data).
3. `adkim=s` and `aspf=s` enforce strict alignment. If you expect subdomain/vendor variation initially, use relaxed (`r`) then tighten later.

### 2. Publish DMARC in DNS

1. Record type: TXT
2. Host/Name: `_dmarc`
3. Value: DMARC policy string
4. TTL: 3600 seconds (or provider default)

### 3. Monitor Reports for 2-4 Weeks

Review aggregate reports regularly:

1. Identify legitimate systems failing SPF/DKIM alignment.
2. Fix sender configurations (SPF include, DKIM signing domain/alignment).
3. Remove unauthorized sources where possible.

### 4. Move to Enforcement Gradually

Progression:

1. `p=none` (monitor)
2. `p=quarantine` (start with `pct=25`, then 50, then 100)
3. `p=reject` (start with `pct=25`, then 100 once clean)

Example quarantine policy:

`v=DMARC1; p=quarantine; pct=50; rua=mailto:dmarc-reports@yourdomain.com; adkim=s; aspf=s`

Example reject policy:

`v=DMARC1; p=reject; pct=100; rua=mailto:dmarc-reports@yourdomain.com; adkim=s; aspf=s`

---

## Verification Checklist (Use This Before Sign-Off)

1. SPF exists and only one SPF record is published.
2. SPF returns PASS for primary sending systems.
3. DKIM is enabled for the domain and returns PASS.
4. DMARC record is published and syntactically valid.
5. DMARC aggregate reports are being received.
6. Unknown or unauthorized senders are identified and remediated.
7. Enforcement progression plan is documented with timeline and owner.

---

## Common Mistakes to Avoid

1. Publishing multiple SPF records instead of one consolidated record.
2. Using `-all` too early before inventory is complete.
3. Enabling DMARC enforcement before DKIM is fully deployed.
4. Forgetting alignment: SPF/DKIM pass alone is not enough; alignment with From domain is required for DMARC pass.
5. Not monitoring DMARC reports before tightening policy.
6. Missing third-party platforms that send on behalf of your domain.

---

## Suggested Ownership Model

1. IT/Email Admin: DNS changes, M365 DKIM enablement, technical validation.
2. Security/Compliance Owner: DMARC policy progression and risk sign-off.
3. Business App Owners: Confirm each SaaS sender is correctly authenticated.

---

## Example Change Log Template

Use this simple format to track rollout:

- Date:
- Domain:
- SPF change:
- DKIM status:
- DMARC policy:
- Report findings:
- Next action:
- Owner:

Keeping this log makes future troubleshooting and audits much easier.
