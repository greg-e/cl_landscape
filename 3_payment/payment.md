# Priority 3: Payment

## Scope

This document provides a full payment landscape for CL Landscape, including:
- All practical payment method options
- All common payment portal/platform options
- Pros and cons of each option
- A customer-friction view focused on "pay the way the customer wants"

---

## Known Facts Today

- CL Landscape currently accepts checks and Zelle
- The business wants additional payment solutions
- The main goal is lower customer friction and easier payment completion

---

## What "Low Friction" Means

A low-friction payment system lets customers choose from several familiar methods, gives clear instructions, and requires minimal back-and-forth to complete payment.

Signals of low friction:
- Customer can pay in less than 2-3 minutes once invoice is received
- At least one option works for residential customers and one for commercial/AP customers
- Customer does not need to call for basic payment instructions
- Payment can be matched to the invoice number without manual detective work

---

## Payment Method Options (Complete View)

| Method | How It Works | Customer Experience | Pros | Cons | Best Fit |
|---|---|---|---|---|---|
| Check | Customer mails or hands over check | Familiar, but slow | No app required, accepted by all demographics | Slow delivery/deposit, potential lost mail, manual handling | Customers who prefer traditional payment |
| ACH push (customer bill pay) | Customer sends from their bank portal | Easy after first setup | Trusted, broad adoption, good for recurring customers | First-time setup can be manual | Residential and commercial repeat customers |
| ACH debit (authorized pull) | Customer authorizes CL to pull funds | Very convenient after authorization | Strong for recurring billing, low effort for customer | Requires authorization controls and return handling | Scheduled/recurring services |
| Zelle | Customer sends via bank app | Fast and familiar for many | Simple and quick for smaller invoices | Bank limits, not universal for business workflows | Transitional digital option |
| Cash | Physical cash payment | Immediate, no app | Instant settlement | Security, recordkeeping, and handling risk | Small in-person payments |
| Debit/credit card (card-not-present) | Customer enters card online or by phone | Very familiar and fast | Highest convenience for many customers | Processing fees, chargeback risk | One-time convenience payments |
| Debit/credit card (in-person tap/chip) | Customer taps/inserts card on device | Very easy in-person | Fast checkout on-site | Requires hardware + fees | On-site and same-day collection |
| Digital wallet (Apple Pay/Google Pay) | Customer pays via phone wallet | Very low effort on mobile | Fast, modern UX, strong completion rates | Usually tied to card rails and card fees | Mobile-first customers |
| PayPal/Venmo/Cash App balance transfers | Customer pays in app | Familiar for many households | Easy for app users, fast confirmation | Platform/account disputes, inconsistent usage across demographics | Residential convenience channel |
| Wire transfer | Customer bank sends wire | Reliable for high amounts | Strong for high-value commercial invoices | Higher bank fees, not ideal for routine small invoices | Large commercial jobs |

---

## Payment Portal/Platform Options (Complete View)

| Portal/Platform | Primary Payment Types | Pros | Cons | Customer Friction | Notes for CL Landscape |
|---|---|---|---|---|---|
| QuickBooks Payments | ACH + cards | Tight QuickBooks workflow, native invoice links, easier reconciliation | Fees apply, onboarding and underwriting required | Low | Strong option for QuickBooks Desktop users wanting integrated flows |
| Stripe Payment Links / Invoicing | Cards + wallets + bank options (region-dependent) | Excellent checkout UX, flexible links, strong mobile conversion | Fees, more setup than simple links, payout timing management | Very low | Great "pay now" experience for residential customers |
| Square Invoices/Links | Cards + wallets + ACH (plan-dependent) | Simple setup, easy invoicing, optional in-person hardware | Fees, less accounting-native than QB for Desktop users | Low | Good all-around usability and quick deployment |
| PayPal Invoicing | PayPal + cards | High brand recognition, many consumers already have accounts | Fees, occasional holds/dispute complexity | Low to medium | Useful where customer base is PayPal-friendly |
| Venmo for Business | Venmo app payments | Popular with some residential users, fast sender flow | Not ideal as sole business rail, fee and policy considerations | Low | Good add-on, not a complete strategy by itself |
| Clover | Cards + POS ecosystem | Strong in-person hardware ecosystem | Hardware + fees + broader setup needs | Low (in person), medium (remote) | Better if field/card-present volume is high |
| Melio | ACH + check + card routing for AP workflows | Good for B2B/AP style payments, flexibility for office admins | Platform-specific workflow and fees for some rails | Medium | More relevant for commercial clients with AP teams |
| BILL (Bill.com) | ACH + AP/AR workflows | Strong approval workflows and finance controls | Higher complexity/cost for small operators | Medium | Best for larger B2B process maturity |
| Wise Business | International/local bank transfers | Good for cross-border payments | Less common for local residential use | Medium | Use only if international clients become relevant |
| "No portal" direct bank instructions | ACH push + checks | No extra platform learning for your team | More manual support burden, less one-click convenience | Medium | Good baseline but not best for friction reduction alone |

---

## Practical Recommendation Framework (Non-Exclusive)

Instead of one "winner," use a layered mix so different customer types can pay the way they prefer.

### Layer 1: Keep Current Baseline

- Keep check
- Keep Zelle while expanding options

### Layer 2: Add a Bank-First Option

- Add ACH as a standard method (push and/or authorized debit)
- Put ACH instructions on all invoices

### Layer 3: Add a One-Click Portal Option

- Add one mainstream "Pay Now" portal for card/wallet users
- Start with one platform first (QuickBooks Payments, Stripe, or Square)

### Layer 4: Add Segment-Specific Optional Channels

- Add PayPal/Venmo for residential-heavy accounts if requested
- Add AP-focused option (Melio/BILL) only if commercial clients ask for it

This layered approach improves completion rates without forcing every customer into a single payment behavior.

---

## Customer Segment Mapping

| Customer Type | Likely Preferred Methods | Why |
|---|---|---|
| Residential, app-friendly | Card portal, wallet, Zelle, Venmo | Fastest on phone, little setup |
| Residential, traditional | Check, ACH push | Familiar and trusted |
| Small commercial | ACH push, check, card portal | Balance of control and convenience |
| Mid-size commercial/AP | ACH, vendor portals, check fallback | Internal approval requirements |

---

## Decision Criteria to Compare Any Option

Use the same scorecard for every method and portal:

1. Customer convenience and familiarity
2. Payment completion speed
3. Cost per transaction
4. Reconciliation effort in QuickBooks Desktop
5. Risk (chargebacks, returns, fraud, disputes)
6. Setup and training effort
7. Long-term reliability

Simple scoring model:
- Score each option from 1 to 5 on each criterion
- Weight customer convenience and reconciliation highest
- Pilot top 2-3 options for 30 days

---

## Risks and Tradeoffs by Strategy

| Strategy | Main Risk | Mitigation |
|---|---|---|
| Check-only or check+Zelle only | Limits customer preference and can delay payment | Add ACH and at least one one-click portal |
| Too many new methods at once | Internal confusion and posting errors | Roll out in phases and standardize internal SOP |
| Card-heavy approach | Higher processing costs | Set pricing policy and monitor net margin impact |
| ACH-heavy approach only | Some customers still want one-click card/mobile options | Keep ACH as core but offer one mainstream portal |
| Portal without accounting discipline | Hard-to-match payments | Require invoice numbers and use consistent QuickBooks receive-payment workflow |

---

## Suggested Next Step

Run a 30-day pilot with this mix:

1. Keep check and Zelle active
2. Add ACH instructions to all invoices
3. Launch one "Pay Now" portal option
4. Track payment method usage and days-to-pay by customer segment

At the end of 30 days, keep the channels customers actually use and retire low-value options.

---

*Last updated: April 11, 2026*
