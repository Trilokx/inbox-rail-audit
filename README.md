# Inbox Rail Audit (free n8n workflow)

Map ~13 months of Gmail receipt metadata to payment rails:
PayPal, Apple/Apple Pay, Google Play/Pay, Stripe/Paddle, SEPA/incasso, Klarna/Afterpay.

Output: a Google Sheet rail map with amount, last4, and VERIFIED/UNCERTAIN evidence.
No PDF download. No mailbox writes. No LLM.

## Install

1. Import [`n8n/inbox-rail-audit.json`](./n8n/inbox-rail-audit.json) into n8n Cloud or self-hosted.
2. Attach Gmail OAuth2 (read-only is enough) to all seven Gmail nodes.
3. Create a Google Sheet tab named `rails` and attach Sheets OAuth2.
4. Set `WINDOW_AFTER` (default window is ~13 months).
5. Run once. Cancel subscriptions yourself.

## Free vs full pack

| | This repo (free) | Full pack ($29) |
| --- | --- | --- |
| n8n workflow JSON | yes | yes |
| Gmail query cheatsheet | yes | yes |
| Agent `SKILL.md` + schema + sample report | no | yes |
| License for commercial reuse of the pack | no | yes |

Full pack: https://rajankie.gumroad.com/l/fazpf

## License

Workflow JSON and queries in this repo: personal use free.
Do not resell as a competing template.
