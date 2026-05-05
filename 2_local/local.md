# Local Network and Backup Strategy (QuickBooks Desktop 2019)

## Scope

This document provides a practical setup for CL Landscape to run **QuickBooks Desktop 2019** on 2 computers with reliable local sharing and strong backup protection.

It covers:
- Hardware selection (simple, reliable, low-maintenance)
- Network configuration for stable QuickBooks multi-user access
- QuickBooks Desktop host/client setup
- Automated backup schedule (local + offsite/cloud)
- Recovery steps so data loss does not stop operations

---

## Current Starting Point

- One Wi-Fi router
- Two computers
- Need both computers to access the same QuickBooks company file
- Home office environment (not a dedicated commercial office)

Main risk today: if the company file exists on one PC with no structured backup, a drive failure, ransomware event, or accidental deletion can permanently lose accounting data.

---

## Home Office Design Principles

For a home-office business, the goal is not enterprise IT. The goal is dependable, affordable, and easy to maintain.

- Keep infrastructure minimal: router + wireless bridge/mesh node + small switch + 2 wired PCs
- Avoid always-on complexity (no domain server required)
- Use scheduled automation so backups run without daily manual steps
- Keep business systems logically separated from family/guest devices
- Prefer proven tools over advanced custom setups

---

## Target Outcome

A small-business setup that is stable and recoverable:

1. One PC acts as the **QuickBooks host** (stores company file)
2. Both PCs use **wired Ethernet** (not Wi-Fi) for QuickBooks traffic
3. Automated backups run multiple times daily
4. Backups exist in at least 3 places (host PC, local backup device, cloud/offsite)

This follows the 3-2-1 principle:
- 3 copies of data
- 2 different storage types
- 1 copy offsite

---

## Recommended Hardware (Right-Sized)

## Core Network Hardware

| Item | Recommendation | Why |
|---|---|---|
| Router | Keep existing router if stable; replace only if unreliable | Avoid unnecessary changes |
| Wireless uplink | Wireless bridge, travel router in client mode, or mesh node with Ethernet ports | Connects the remote switch area back to the router without a long cable run |
| Switch | 5-port or 8-port unmanaged gigabit switch (TP-Link/Netgear) | Gives stable wired links for both PCs |
| Ethernet Cabling | Cat6 cables for each PC to switch and from bridge/mesh node to switch | Reduces disconnects and latency |
| UPS Battery Backup | 1 UPS for router/switch + 1 UPS for host PC | Prevents file corruption from power loss |

Home-office placement tips:
- Put host PC, switch, and backup drive where they are protected from pets, dust, and accidental unplugging
- Label power bricks and cables to reduce accidental shutdowns
- Keep UPS audible alarms enabled so outages are noticed quickly

## Backup Hardware

| Item | Recommendation | Why |
|---|---|---|
| Local backup drive | 4TB external USB drive (WD/Seagate) | Plug-and-play backup; lowest cost and complexity. Insufficient alone (single point of failure) but paired with cloud backup is very solid. |
| Cloud backup | Backblaze, CrashPlan, or similar endpoint backup | Offsite protection from theft/fire/ransomware. The real safety net for this setup. |

## Amazon Hardware - Selected Items

This section reflects the items you selected.

### Selected Core Hardware

| Item | Qty | Model/Link | Price |
|---|---|---|---|
| Seagate Expansion Desktop 4TB external USB drive | 1 | STKP4000400 | $139.99 |
| TP-Link Archer A54 AC1200 Wi-Fi router | 1 | [Search on Amazon](https://www.amazon.com/s?k=TP-Link+Archer+A54) | $34.99 |
| TP-Link 8-port gigabit switch | 1 | TL-SG108 | $19.99 |
| Cable Matters Cat6 8ft cable 5-pack | 1 | [Search on Amazon](https://www.amazon.com/s?k=Cable+Matters+Cat6+8ft) | $17.99 |
| Cable Matters Cat6 3ft cable 5-pack | 1 | [Search on Amazon](https://www.amazon.com/s?k=Cable+Matters+Cat6+3ft) | $12.49 |
| EZYUMM Ethernet coupler 3-pack (extenders) | 1 | [Search on Amazon](https://www.amazon.com/s?k=EZYUMM+Ethernet+Coupler) | $4.95 |
| **Estimated total hardware** | | | **~$230** |

### Optional But Recommended

- [UPS for switch and router (650VA class)](https://www.amazon.com/s?k=APC+Back-UPS+650VA) — keeps network online during brief outages (qty 1)
- [UPS for QuickBooks host PC (850VA to 1000VA class)](https://www.amazon.com/s?k=CyberPower+CP850AVRLCD) — prevents file corruption from power loss (qty 1)

### Optional Accessories

- [Cable ties or Velcro wraps](https://www.amazon.com/s?k=Velcro+cable+ties)
- [Label maker](https://www.amazon.com/s?k=Brother+P-touch+label+maker)
- [Surge-protected power strip](https://www.amazon.com/s?k=APC+surge+protector+power+strip)
- [Fireproof document safe](https://www.amazon.com/s?k=fireproof+document+safe)

---

## Network Design (Simple and Reliable)

Topology:
- Internet Modem/Router -> Wi-Fi uplink -> Wireless bridge or mesh node -> Gigabit Switch -> Host PC + Workstation PC
- Router Wi-Fi remains available for phones/tablets; QuickBooks PCs should stay wired to the local switch, not connect individually by Wi-Fi when possible

Important note:
- A direct Ethernet run from router to switch is still the best option for QuickBooks
- If that is not possible, a dedicated wireless bridge or mesh node feeding the switch is the next-best layout
- This is usually more reliable than having each QuickBooks PC connect to the router by Wi-Fi on its own

Configuration checklist:
- Set DHCP reservations on router for both PCs (so they keep predictable IP addresses)
- Rename computers clearly (example: `CL-QB-HOST`, `CL-OFFICE-01`)
- Set network profile to Private on both Windows PCs
- Disable sleep/hibernate on host PC during business hours
- Ensure host PC auto-starts after power loss (BIOS setting if available)
- Create a separate guest Wi-Fi network for non-business devices if router supports it
- Place the wireless bridge or mesh node where it has a strong signal back to the main router
- Keep the bridge or mesh node on a UPS if practical so the uplink does not drop during brief outages
- Do not expose QuickBooks shares to internet access (no port forwarding to host PC)

---

## QuickBooks Desktop 2019 Multi-User Setup

### Step 0: Download QuickBooks Desktop 2019 Installer

Before beginning setup, you need the QuickBooks Desktop 2019 installer. Since one PC does not have a CD drive, you'll need to download the MSI or `.exe` file.

**Option 1: Download via Intuit Customer Account Portal (Recommended)**
1. Go to [https://camps.intuit.com](https://camps.intuit.com) (Intuit's Customer Account Management Portal)
2. Sign in with your Intuit account
3. Click **"QuickBooks Desktop"** under your products
4. Find **QuickBooks Desktop 2019** and click **"Download"**
5. Save the installer file (`.exe`) to a USB flash drive or cloud storage
6. Transfer to the PC without a CD drive via USB or cloud sync

**Option 2: Contact Intuit Support to Request Download Link**
1. Call Intuit Support: **1-800-446-8848**
2. Have your QuickBooks license key ready
3. Explain you need the download link (your CD drive is unavailable)
4. Intuit will email you a direct download link to the MSI installer
5. Download the file and transfer to your PC via USB

**Option 3: Order a Physical Backup CD (Slower)**
1. Call Intuit Support: **1-800-446-8848**
2. Request a backup CD be shipped to you
3. Once received, use the CD on the PC with a CD drive or use an external CD drive on the other PC

**Option 4: Copy the CD You Already Have to a USB Drive (Easiest if you have the CD)**

Since you own the license, copying the CD contents to a USB drive is perfectly fine.

On the PC that has a CD drive:
1. Insert the QuickBooks Desktop 2019 CD
2. Open File Explorer and navigate to the CD drive (usually `D:` or `E:`)
3. Select all files on the CD: **Ctrl+A**
4. Copy them: **Ctrl+C**
5. Plug in a USB flash drive (at least 2GB free space)
6. Open the USB drive in File Explorer and create a folder called `QB2019`
7. Open that folder and paste all the CD files into it: **Ctrl+V**
8. Wait for the copy to finish (2–5 minutes)

On the PC without a CD drive:
1. Plug in the USB drive
2. Open File Explorer > navigate to the USB drive > open the `QB2019` folder
3. Find `setup.exe` or `autorun.exe`
4. Right-click it > **Run as Administrator**
5. The QuickBooks installer launches — proceed as outlined in Step 2 below

> **License key:** You'll need it during installation. It's printed on the CD sleeve or case, or available at [camps.intuit.com](https://camps.intuit.com) under your products.

**Once you have the installer file:**
- Save it to a USB drive or cloud location accessible to both PCs
- You'll use this file in **Step 2: Install QuickBooks Desktop 2019 on Both PCs** below

---

### Pre-Setup Verification

Before starting, verify:
- Both PCs are wired to the switch via Ethernet (not Wi-Fi)
- Both PCs can ping each other: open Command Prompt and type `ping [other-pc-name]` — should see replies
- Both PCs can see each other in **Network** (File Explorer > Network)
- Both PCs are on the same local subnet (Windows Settings > Network > Status > View your network properties; check IPv4 address range)

---

## Step 1: Choose and Prepare the Host Computer

**Host selection:**
- Choose the more reliable/newer PC (this will store the company file permanently)
- This PC must remain powered on during all business hours
- Example: `CL-QB-HOST`

**Create the data folder on the host PC:**
1. Open File Explorer on the host PC
2. Create a new folder at `C:\QBData\CompanyFiles`
   - Right-click C: drive > New > Folder
   - Name it `QBData`
   - Inside QBData, create another folder named `CompanyFiles`
3. Create a second folder for backups: `C:\QBData\Backups`
   - This is where QuickBooks will store its `.QBB` backup files

**Set folder permissions on the host:**
1. Right-click `C:\QBData` folder > Properties > Sharing tab
2. Click "Share" button
3. Add your local Windows user account and the workstation user account with "Read/Write" permissions
4. Click "Share" > "Done"
5. Note the network path (should be something like `\\CL-QB-HOST\QBData`)

---

## Step 2: Install QuickBooks Desktop 2019 on Both PCs

**Preparation:**
- You should have the QuickBooks Desktop 2019 installer file (from Step 0) saved to a USB drive or cloud location
- If using USB: insert the USB drive into the PC without a CD drive
- If using cloud: download the installer file from Google Drive, Dropbox, or OneDrive

**On both the host and workstation PC (do host first):**
1. Locate the QuickBooks Desktop 2019 installer file (`.exe` or `.msi`)
2. Double-click the installer to launch it
3. When prompted, select **Custom Install** (not Express)
4. When prompted, select **both** of these components:
   - QuickBooks Desktop application
   - QuickBooks Database Server (required on both PCs for multi-user mode)
5. Select the installation location (default is fine): C:\Program Files (x86)\Intuit\QuickBooks
6. Complete the installation
7. The installer may prompt to restart — restart the PC if asked
8. Do NOT open QuickBooks yet; wait until both PCs are installed

---

## Step 3: Install and Configure Database Server Manager (Host Only)

Database Server Manager tells QuickBooks where the company file lives and sets up network access.

**On the host PC (`CL-QB-HOST`) only:**

1. Open **Start Menu** > Search for "QuickBooks Database Server Manager"
2. If not found, look in: C:\Program Files (x86)\Common Files\Intuit\QuickBooks\QBCFMonitorService
3. Right-click QuickBooks Database Server Manager > Run as Administrator
4. A window appears asking to scan for company files
5. Click **"Scan Folder"** button
6. Browse to `C:\QBData\CompanyFiles` (where your company file is or will be)
7. Select the folder > OK
8. The Database Server Manager will scan and list any `.QBW` files (company files)
9. If your company file already exists here, you'll see it listed
10. If this is a brand new setup, the folder will be empty for now
11. Close the Database Server Manager window
12. Windows Firewall may prompt to allow QuickBooks — click "Allow"

---

## Step 4: Move or Copy Your QuickBooks Company File

**If you have an existing company file:**
1. Locate your current `.QBW` file (usually in Documents or My Business Files)
2. Copy it to `C:\QBData\CompanyFiles\` on the host PC
3. Verify the file is there and no longer open on any PC

**If this is a new company file:**
1. You'll create it in Step 5 when you first open QuickBooks on the host PC

---

## Step 5: Configure QuickBooks Multi-User Mode (Host PC)

**On the host PC only:**

1. Open QuickBooks Desktop 2019
2. Open your company file from `C:\QBData\CompanyFiles\`
   - Go to **File > Open or Restore Company**
   - Navigate to `C:\QBData\CompanyFiles\`
   - Select your `.QBW` file > Open
3. When prompted, choose **Multi-User Mode** (not Single-User)
4. Go to **File > Utilities > Database Server Manager**
   - This confirms the host is set as the database server for this company file
5. Go to **Edit > Preferences > Files and Backup**
   - Under "Backup Location," set it to: `C:\QBData\Backups\`
   - This is where scheduled backups will be stored
6. Go to **File > Utilities > Set Up User Security** (if using user accounts)
   - Create user accounts for each person who will use QuickBooks
   - Assign permissions (optional but recommended for security)
7. Leave QuickBooks open on the host PC so it can serve requests from the workstation

**Important:** The host PC should keep QuickBooks open in multi-user mode during all business hours. If you close QuickBooks on the host, the workstation PC cannot access the company file.

---

## Step 6: Connect the Workstation PC to the Company File

**On the workstation PC (`CL-OFFICE-01`):**

1. Open QuickBooks Desktop 2019
2. Go to **File > Open or Restore Company**
3. Instead of browsing to a local folder, you'll enter a **network path**:
   - Click the folder icon and type (or browse to): `\\CL-QB-HOST\QBData\CompanyFiles\`
   - Select your company file (`.QBW`)
4. When prompted, choose **Multi-User Mode**
5. QuickBooks will connect to the company file on the host PC
6. You should now see the company file open on the workstation PC, pulling data from the host PC across the network

**Verify multi-user is working:**
- Make a small test entry on the workstation (like a new memo or item)
- Switch to the host PC and refresh the screen (Ctrl+R or **View > Refresh**)
- You should see your test entry appear on the host PC
- Delete the test entry to clean up

---

## Step 7: Configure Scheduled Backups

**On the host PC:**

1. Go to **File > Utilities > Scheduled Backup**
2. Set up daily/weekly automated backups:
   - **Backup location:** `C:\QBData\Backups\`
   - **Frequency:** Every 2-4 hours during business day
   - **Keep backups:** Set to 30 days or more
3. For the external USB drive (Seagate Expansion):
   - Plug it into the host PC
   - Go to **File > Backup Company > Create Local Backup**
   - Select **Backup to a portable storage device**
   - Choose the Seagate Expansion drive > Folder "Backups\QB" (you created earlier)
   - This backs up to the external drive for offsite safety

---

## Step 8: Map the Company File Path as a Network Drive (Optional but Recommended)

This makes it easier to access the company file without typing the full network path.

**On the workstation PC:**

1. Open File Explorer
2. Right-click **"This PC"** > **Map network drive...**
3. Drive letter: Pick any unused letter (e.g., `Z:`)
4. Folder: `\\CL-QB-HOST\QBData\CompanyFiles\`
5. Check **"Reconnect at sign-in"**
6. Click **Finish**
7. The folder now appears as a mapped drive (e.g., `Z:\`)
8. In QuickBooks on the workstation, you can now open the file as `Z:\YourCompanyFile.QBW`

---

## Step 9: Set Up User Accounts and Permissions (Recommended)

For security, create separate Windows user accounts for each person using QuickBooks.

**On the host PC:**

1. Go to **Settings > Accounts > Other people**
2. Click **Add another person to this PC**
3. Create accounts for each user (e.g., `Greg`, `Assistant`)
4. Right-click `C:\QBData` folder > Properties > Sharing tab
5. Click "Share" > Add each user account > Assign Read/Write permissions
6. In QuickBooks, go to **Edit > Preferences > Accounting** (optional: set company file user rights)

**On the workstation PC:**

1. Create the same user accounts so people can log in locally
2. Each user will have the same access to the shared company file (if permissions are set correctly)

---

## Step 10: Daily Use Validation

After setup, run through this checklist before relying on the system:

1. **Host PC morning startup:**
   - Power on `CL-QB-HOST`
   - Open QuickBooks and load the company file
   - Leave it open all day

2. **Workstation PC startup:**
   - Power on `CL-OFFICE-01`
   - Open QuickBooks
   - Go to **File > Open or Restore Company**
   - Navigate to `\\CL-QB-HOST\QBData\CompanyFiles\` (or use mapped drive `Z:\`)
   - Open the company file
   - Confirm multi-user mode is active (should say "Multi-User Mode" in the title bar)

3. **Test multi-user functionality:**
   - Make an entry on one PC (e.g., a customer note)
   - Switch to the other PC and press **Ctrl+R** (Refresh)
   - Verify the entry appears
   - Delete the test entry to clean up

4. **Test backup:**
   - Run **File > Backup Company > Create Local Backup**
   - Select the Seagate Expansion drive
   - Confirm the backup completes successfully
   - Check the external drive: should have a `.QBB` backup file dated today

---

## Critical Stability Rules

1. **Always use wired Ethernet:** Both PCs must connect via the TL-SG108 switch, not Wi-Fi
2. **Keep host PC powered:** The host must stay on during business hours; if it powers down, the workstation loses access
3. **No cloud sync:** Do NOT store the company file in OneDrive, Dropbox, or Google Drive — QuickBooks does not work correctly with cloud folders
4. **Back up frequently:** Run backups at least once daily to the external drive, plus enable cloud backup service (Backblaze or CrashPlan)
5. **Test restores monthly:** A backup is only as good as your ability to restore from it. Once a month, restore a backup to a test folder and verify it opens correctly

---

## Troubleshooting Common Issues

**Problem: Workstation PC cannot find the host PC**
- Solution: Verify both PCs are on the same local network and can ping each other
- Check: `ping CL-QB-HOST` from the workstation PC command line
- If ping fails, check network cables and switch connectivity

**Problem: "Cannot find company file" when opening on workstation**
- Solution: Verify the file path exists: `\\CL-QB-HOST\QBData\CompanyFiles\`
- Check: Host PC shares the folder correctly (run **net share** command to list shares)
- Verify: The company file (`.QBW`) is actually in that folder

**Problem: QuickBooks says "This file is already open in single-user mode"**
- Solution: The file was not properly closed or is already open on another PC
- Close QuickBooks on all PCs
- Wait 5 minutes
- Open on host PC first, then workstation

**Problem: Workstation PC is very slow opening QuickBooks**
- Solution: Check network connectivity — run `ipconfig` to verify IP address is correct
- Check: All cables are firmly plugged into the switch
- Verify: No one is running large downloads or backups simultaneously

**Problem: Backup fails or says "file is locked"**
- Solution: Close QuickBooks on the workstation PC temporarily while backup runs on host
- Set backup schedule for off-hours if possible (e.g., 6 PM when work ends)

---

## Backup Strategy (Automated)

Use layered backups, not a single backup job.

## Layer A: QuickBooks Native Backup (Frequent)

- In QuickBooks, schedule local backup every 2-4 hours during business hours
- Keep at least 30 days of rolling `.QBB` backups
- Backup destination: local backup folder on host (not same folder as live company file)

## Layer B: System/File Backup to External Drive (Nightly)

- Connect external USB drive to host PC
- Nightly backup of:
  - `C:\QBData\CompanyFiles`
  - QuickBooks backup folder (where `.QBB` files are stored)
  - Key business folders (contracts, invoices, docs)
- Retention:
  - Daily backups for 14 days
  - Weekly backups for 8 weeks
  - Monthly backups for 12 months

## Layer C: Offsite/Cloud Backup (Continuous or Nightly)

- Install endpoint cloud backup on host PC (and optionally workstation)
- Include QuickBooks data and backup folders
- Turn on version history and immutable retention if available

Recommended policy:
- Minimum 90-day version history
- At least 1 year retention for monthly snapshots

---

## Suggested Schedule

| Time | Task |
|---|---|
| Every 2-4 hours (business day) | QuickBooks local backup (`.QBB`) |
| 9:00 PM daily | Full file backup to external USB drive |
| Overnight | Cloud backup sync/upload |
| Friday 9:30 PM | Weekly integrity check + test restore validation |
| 1st business day monthly | Recovery drill: restore latest backup to test folder |

---

## Security and Data-Loss Prevention Controls

- Enable BitLocker on host and workstation drives
- Turn on Microsoft Defender and automatic updates
- Use standard (non-admin) accounts for daily work
- Enable MFA on cloud backup account and Microsoft 365 admin accounts
- Keep QuickBooks and Windows patched
- Document all credentials and recovery steps in a secure password manager

---

## Recovery Playbook (When Something Breaks)

## Scenario A: Host PC drive fails

1. Replace/rebuild host PC
2. Reinstall QuickBooks Desktop 2019 + Database Server Manager
3. Restore latest backup from external drive
4. If local backup is unavailable, restore from cloud backup
5. Open restored company file and run QuickBooks Verify/Rebuild tools

## Scenario B: Accidental deletion or corruption

1. Stop QuickBooks access on both PCs immediately
2. Restore most recent clean `.QBB` or file backup copy
3. Confirm data integrity and resume multi-user access

## Scenario C: Ransomware event

1. Disconnect affected PC(s) from network immediately
2. Reimage affected machines
3. Restore from clean, previous-version backup (offsite/cloud)
4. Rotate passwords and review security settings

---

## Implementation Plan (48 Hours After Hardware Arrives)

## Day 1 — Morning: Hardware and Network Setup (2–3 hours)

- [ ] Unbox all hardware: switch (TL-SG108), Archer A54 router, external drive (STKP4000400), cables, and couplers
- [ ] Choose a location for the TL-SG108 switch (away from main router, near the two PCs)
- [ ] If the switch area is far from the Archer A54 placement: use 1 EZYUMM coupler to extend Ethernet from Archer A54 to the switch with two Cat6 cables (8ft + 3ft chained together)
- [ ] From the TL-SG108 switch, run two Cat6 cables (one 8ft, one 3ft) to each of the two PCs
- [ ] Power on the Archer A54 router and configure it:
  - Connect to your main Wi-Fi router (or plug into LAN port if physically accessible)
  - Set Archer A54 to **Access Point mode** (not router mode) so it bridges your network
  - Note its IP address (typically printed on the device or found via router admin panel)
- [ ] Power on the TL-SG108 switch (passive device, no power button needed if powered via PoE)
- [ ] Set DHCP reservations on your main router for both PCs (so they keep static IPs)
- [ ] Rename PCs clearly:
  - First PC: `CL-QB-HOST`
  - Second PC: `CL-OFFICE-01`
- [ ] Set Windows network profile to **Private** on both PCs (Settings > Network > Status > Properties)

## Day 1 — Afternoon: QuickBooks Multi-User (1–2 hours)

- [ ] Create QuickBooks host data folder (`C:\QBData\CompanyFiles`)
- [ ] Set folder sharing and permissions (authorized users only)
- [ ] Install/configure QuickBooks Database Server Manager on host PC
- [ ] Enable multi-user hosting on host PC only
- [ ] Confirm workstation PC opens company file in multi-user mode

## Day 1 — External Drive Preparation (15 minutes)

- [ ] Unbox external USB drive (Seagate Expansion 4TB)
- [ ] Connect to host PC via USB
- [ ] Create a backup folder (example: `C:\BackupLocation` on the drive)
- [ ] Create folder for QuickBooks backups (example: `Backups\QB`)
- [ ] Create folder for nightly file backups (example: `Backups\Daily`)

## Day 2 — Backup Validation (1–2 hours)

- [ ] Configure QuickBooks scheduled backups (every 2–4 hours during business day) → backup to external drive
- [ ] Configure nightly file backup job (Windows Backup or similar) → backup to external drive
- [ ] Sign up for cloud backup service (Backblaze or CrashPlan recommended) and install on host PC
- [ ] Run one manual backup end-to-end
- [ ] Perform one test restore to a separate folder and confirm file opens correctly
- [ ] Label cables and power bricks
- [ ] Document backup paths and schedule

**Total expected time: 4–5 hours across 2 days**

---

## Practical Starting Stack (Low Complexity)

If you want the least complexity while still being reliable:

1. Keep current router
2. Add 1 unmanaged gigabit switch
3. Wire both PCs with Cat6
4. Use one PC as QuickBooks host
5. Add one 4TB USB backup drive + cloud backup service
6. Use a guest Wi-Fi SSID for non-business/home devices

This gives a strong reliability improvement without needing a server rack or IT-heavy infrastructure.

Estimated one-time hardware cost for this home-office stack:
- Selected hardware: about $230
- Optional UPS units (2): about $180–$350 total
- Cloud backup service: about $10–$15 per month
- 4TB external backup drive: about $90-$140

Estimated ongoing cost:
- Cloud backup: about $10-$25 per month depending on provider/retention

---

## Notes Specific to QuickBooks Desktop 2019

- Multi-user performance depends heavily on stable LAN quality, so wired is strongly preferred
- The host machine should remain consistently online during business operations
- Always test restore periodically; backups are only trustworthy after a successful restore test

---

*Last updated: April 21, 2026*
