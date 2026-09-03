# Map PayPal / Apple / Google Play / Stripe charges from Gmail

One pass over ~13 months of Gmail receipt **metadata**. Output is a payment-rail map — wallet, card last4, last charge, monthly vs dead — written to Google Sheets.

Not another merchant CSV. Does **not** cancel subscriptions. No PDF download. No mailbox writes. No LLM.

Free teaser in this repo. Full pack (agent `SKILL.md`, schema, sample report, license): **[$29 on Gumroad](https://rajankie.gumroad.com/l/fazpf)**.

## Install (free n8n path)

1. Import [`n8n/inbox-rail-audit.json`](./n8n/inbox-rail-audit.json) into n8n Cloud or self-hosted.
2. Attach Gmail OAuth2 (read-only is enough) to all seven Gmail nodes.
3. Create a Google Sheet tab named `rails` and attach Sheets OAuth2.
4. Set `WINDOW_AFTER` (~13 months back).
5. Run once. Cancel by hand if you want.

## Gmail search cheatsheet

See [`queries.md`](./queries.md) for copy-paste operators per rail (PayPal, Apple, Play, GPay, Stripe/Paddle, SEPA/incasso, Klarna).

## What you get in the free teaser

| File | Purpose |
| --- | --- |
| `n8n/inbox-rail-audit.json` | Importable workflow (credentials = `REPLACE`) |
| `queries.md` | Gmail operators |
| `LICENSE.txt` | Personal use; no resale as competing template |

## Sample shape (fake data)

| rail | merchant | amount | currency | cadence | last_charge | last4 | evidence |
| --- | --- | --- | --- | --- | --- | --- | --- |
| stripe | Charting SaaS | 29.00 | USD | monthly | 2026-08-12 | 4242 | VERIFIED |
| apple | iCloud+ | 2.99 | EUR | monthly | 2026-08-28 | — | VERIFIED |
| paypal | Dead Gym Co | 39.00 | EUR | cancelled | 2025-11-03 | — | UNCERTAIN |

## Full pack ($29)

On Gumroad: agent `SKILL.md`, output schema, sample report, same n8n JSON, license for commercial reuse of the pack.

→ https://rajankie.gumroad.com/l/fazpf

## Honest limits

- Only charges that hit Gmail. Rent/SEPA blind spots if not emailed.
- 200-thread cap per rail query — under-sampled if a query hits the cap.
- Human still cancels. No auto-send, no labels, no archive.
