# Step 3: QuickBooks Desktop 2019 — Send Invoices Through Outlook

This guide walks through the complete setup to have QuickBooks Desktop 2019 send invoices directly through Outlook desktop using your Microsoft 365 business mailbox.

---

## Prerequisites

Before starting, confirm you have:

1. QuickBooks Desktop 2019 installed and activated.
2. Microsoft 365 Business Standard (or higher) license — required for the Outlook desktop app.
3. Outlook desktop app installed and fully configured with your business mailbox (e.g., `invoices@cllandscape.com`).
4. Your Outlook profile is set as the **default** mail profile in Windows.
5. Windows is fully updated; QuickBooks 2019 is on the latest release (Help > Update QuickBooks Desktop).

> **Important:** QuickBooks Desktop requires the full Outlook desktop application. Web-based Outlook (OWA) and Microsoft 365 Business Basic do not work. You must have Microsoft 365 Business Standard or higher.

---

## Part A: Configure Outlook Desktop

### 1. Add Your Microsoft 365 Mailbox to Outlook

1. Open **Outlook**.
2. Go to **File > Add Account**.
3. Enter your business email address (e.g., `invoices@cllandscape.com`) and click **Connect**.
4. Outlook will auto-discover your Microsoft 365 settings. Sign in with your Microsoft 365 credentials.
5. Complete the sign-in and allow Outlook to finish syncing.
6. Confirm the mailbox appears in the left-hand folder pane.

### 2. Set Outlook as the Default Mail Client in Windows

1. Open **Windows Settings** (Win + I) > **Apps** > **Default Apps**.
2. Scroll to **Email** and click it.
3. Select **Outlook** from the list and confirm.
4. Close Settings.

### 3. Set the Correct Default Outlook Profile

This step is critical — QuickBooks uses the default Outlook profile to send mail.

1. Open the Windows **Control Panel** (search "Control Panel" in the Start menu).
2. Go to **Mail (Microsoft Outlook)** — you may need to switch to "Large icons" view to find it.
3. Click **Show Profiles**.
4. Confirm only one profile exists, or identify the one linked to your business mailbox.
5. Under "When starting Microsoft Outlook, use this profile," select **Always use this profile** and choose your business profile from the dropdown.
6. Click **OK**.

### 4. Verify Outlook Sends Correctly

Send a test email directly from Outlook to a Gmail or personal address before touching QuickBooks.

1. Open Outlook.
2. Click **New Email**.
3. Address it to a test account (e.g., your personal Gmail).
4. Send it and confirm it arrives in the inbox (not spam).
5. If it lands in spam, complete the SPF/DKIM/DMARC setup in Step 2 before proceeding.

---

## Part B: Configure QuickBooks Desktop 2019

### 1. Open Send Forms Preferences

1. Open QuickBooks Desktop 2019.
2. Go to **Edit > Preferences**.
3. In the left panel, click **Send Forms**.
4. Click the **My Preferences** tab.

### 2. Set the Email Method to Outlook

1. Under "Send email using," select **Outlook**.
2. QuickBooks will attempt to detect the installed Outlook profile.
3. If Outlook does not appear in the dropdown, see the Troubleshooting section at the bottom of this guide.
4. Click **OK** to save.

### 3. Configure the Invoice Email Template

1. In QuickBooks, go to **Edit > Preferences > Send Forms**.
2. Click the **Company Preferences** tab.
3. Under "Auto-check the 'To be e-mailed' checkbox if customer's e-mail address is on file" — enable this option so invoices are queued for email automatically.
4. In the **Email Templates** section, select **Invoices** from the template list.
5. Customize the subject line and body as needed. Example:
   - **Subject:** Invoice [Invoice No.] from CL Landscape — Due [Due Date]
   - **Body:** Hi [Customer Name], please find your invoice attached. Contact us with any questions. Thank you.
6. Click **OK**.

### 4. Ensure Customer Records Have Email Addresses

1. Go to **Customers > Customer Center**.
2. Open each active customer record.
3. Confirm the **Email** field is populated.
4. Save any changes.

---

## Part C: Send a Test Invoice Through Outlook

### 1. Create or Open a Test Invoice

1. Go to **Customers > Create Invoices**.
2. Select a test customer (use a customer whose email address you control, such as your own Gmail).
3. Add one or more line items.
4. Confirm the **"To be e-mailed"** checkbox at the top of the invoice is checked.

### 2. Send the Invoice

1. Click the **Email** button at the top of the invoice (envelope icon), or go to **File > Send Forms**.
2. QuickBooks will open a send confirmation window showing the recipient email and subject.
3. Review the details and click **Send Now**.
4. QuickBooks hands the email off to Outlook. You will briefly see Outlook open in the background.

### 3. Verify Delivery

1. Check the **Sent Items** folder in your Outlook mailbox — the invoice email should appear there with the PDF attachment.
2. Check the test recipient inbox (your Gmail or personal account) — the invoice should arrive within 1–2 minutes.
3. Confirm the PDF attachment opens correctly and all invoice details are accurate.
4. In QuickBooks, open the invoice and confirm the **"Sent"** status is reflected.

---

## Part D: Send a Batch of Invoices

For sending multiple invoices at once:

1. Go to **File > Send Forms**.
2. QuickBooks will display a list of all invoices with "To be e-mailed" checked.
3. Review the list, uncheck any you do not want to send in this batch.
4. Click **Send Now**.
5. QuickBooks will process each invoice sequentially through Outlook.
6. After sending, spot-check one or two in Outlook's Sent Items to confirm delivery.

---

## Troubleshooting

### Outlook Does Not Appear in QuickBooks Send Forms Preferences

| Cause | Fix |
|---|---|
| Outlook is not installed (only web Outlook) | Install Outlook desktop via Microsoft 365 setup |
| Outlook is 64-bit but QuickBooks is 32-bit (or vice versa) | Both must match bit-version — check QuickBooks (Help > About) and Outlook (File > Office Account > About Outlook) |
| No Outlook profile configured | Set up a mail profile in Control Panel > Mail |
| Outlook is not set as the default mail client | Fix in Windows Settings > Default Apps > Email |

### QuickBooks Crashes or Freezes When Sending

| Cause | Fix |
|---|---|
| QuickBooks is out of date | Help > Update QuickBooks Desktop, install all updates |
| Outlook is not fully closed/open during send | Have Outlook open but not composing another email when QuickBooks sends |
| Antivirus blocking MAPI (mail API) calls | Temporarily disable real-time AV protection, test send, re-enable — then whitelist QuickBooks in AV settings |

### Invoice Arrives in Customer's Spam Folder

| Cause | Fix |
|---|---|
| SPF/DKIM/DMARC not configured | Complete Step 2 of this guide series |
| Sending from a free email (Gmail, Yahoo) | Use only your business domain mailbox in Outlook |
| Invoice subject line is spam-like | Edit the template — avoid all-caps, exclamation marks, "URGENT" |

### Customer Reports No Attachment

| Cause | Fix |
|---|---|
| QuickBooks PDF driver issue | Go to Help > QuickBooks PDF & Print Repair Tool and run the repair |
| Customer's email service stripped the PDF | Re-send directly from File > Send Forms and ask customer to check spam or request from a different email |

---

## Summary Checklist

| Step | Done? |
|---|---|
| Microsoft 365 Business Standard license confirmed | ☐ |
| Outlook desktop installed and mailbox added | ☐ |
| Outlook set as default mail client in Windows | ☐ |
| Default Outlook profile set in Control Panel > Mail | ☐ |
| Test email sent from Outlook — arrived in inbox (not spam) | ☐ |
| SPF, DKIM, DMARC records configured (Step 2) | ☐ |
| QuickBooks Send Forms preference set to Outlook | ☐ |
| Customer email template configured in QuickBooks | ☐ |
| Customer records have email addresses populated | ☐ |
| Test invoice sent and confirmed delivered with PDF | ☐ |
| Batch send tested with File > Send Forms | ☐ |
