# Inbox Rail Audit — Gmail payment-rail map (n8n)

Map **~13 months of Gmail receipt metadata** to **payment rails**, not a merchant CSV.

**Rails:** PayPal · Apple / Apple Pay · Google Play / Google Pay · Stripe / Paddle / Lemon Squeezy · SEPA / incasso · Klarna / Afterpay

Output is a Google Sheet: amount, currency, cadence, last charge, card **last4**, and **VERIFIED / UNCERTAIN** evidence.

- No PDF download
- No mailbox writes (no labels, archive, send, drafts)
- No LLM key
- You cancel. The workflow only draws the map.

Free n8n workflow in this repo. Full pack (agent `SKILL.md` + schema + sample report): [Gumroad — $29](https://rajankie.gumroad.com/l/fazpf)

## Who it is for

Solopreneurs with **PayPal + Apple + Play + Stripe on one Gmail** who cannot face 2,000 receipt mails. Also useful if you self-host n8n and want a read-only Gmail → Sheets audit.

## Who it is not for

- Bank-CSV users who already have a complete export (use that; Gmail will not see rent/health/telco SEPA unless those senders mailed a receipt)
- Anyone who wants a bot that **auto-cancels** subscriptions — this does not, on purpose

## Install (n8n Cloud or self-hosted)

1. Import [`n8n/inbox-rail-audit.json`](./n8n/inbox-rail-audit.json).
2. Attach **Gmail OAuth2** (read-only is enough) to all seven Gmail nodes. Credentials in the JSON are placeholders (`REPLACE`).
3. Create a Google Sheet tab named `rails`. Attach **Google Sheets OAuth2**. Paste the spreadsheet ID into **Append sheet** (`REPLACE_SHEET_ID`).
4. Set `WINDOW_AFTER` in **Set window** (`YYYY/MM/DD`, default is a ~13-month window).
5. Confirm every Gmail node has **Download Attachments = off**.
6. Execute once. Read `evidence` before you cancel anything.

Gmail searches and the 200-thread cap: [`queries.md`](./queries.md).

## Free repo vs full pack

| | This repo (free) | Full pack ($29) |
| --- | --- | --- |
| n8n workflow JSON | yes | yes |
| Gmail query cheatsheet | yes | yes |
| Agent `SKILL.md` + schema + sample report | no | yes |
| License for commercial reuse of the pack | no | yes |

Pack: https://rajankie.gumroad.com/l/fazpf

## Limits (named, not hidden)

- Household SEPA (rent, health insurance, telco, tax) is often **UNAVAILABLE in Gmail** — that is a blind spot, not “you have no rent”.
- Keep EUR and USD separate. Do not invent FX.
- A query that hits 200 threads is under-sampled; the workflow says so instead of pretending completeness.
- “Card added / kaart toegevoegd” is not a charge. Stripe *seller* onboarding mail is not spend.

## Adjacent pack

**Gmail Renewal Radar** (SKU2, listing not live yet): merchant + cadence first — recurring vs one-off, price hike, cancel URL in snippet. Run this rail audit first if you do not yet know the rails.

## License

Workflow JSON and queries in this repo: personal use free. Do not resell as a competing template.
