# Gmail queries

Replace `YYYY/MM/DD` with the window start. Run **one query at a time**. Cap 200 threads.

Do not add `has:attachment` (that pulls invoices you should not open).

```
after:YYYY/MM/DD (from:paypal.com OR from:paypal.nl OR from:service@paypal.nl) (betaling OR receipt OR ontvangstbewijs OR "automatische betaling" OR payment)
```

```
after:YYYY/MM/DD (from:apple.com OR from:email.apple.com) (invoice OR factuur OR receipt OR "Apple Pay")
```

```
after:YYYY/MM/DD (from:googleplay OR from:google.com OR subject:"Google Play") (subscription OR abonnement OR "Google LLC" OR receipt)
```

```
after:YYYY/MM/DD ("Google Pay" OR "GPay" OR "kaart toegevoegd" OR "card added")
```

```
after:YYYY/MM/DD (from:stripe.com OR from:paddle.com OR from:lemonsqueezy.com) (receipt OR invoice OR payment)
```

```
after:YYYY/MM/DD (incasso OR "automatische incasso" OR sepa OR machtiging OR "direct debit")
```

```
after:YYYY/MM/DD (from:klarna OR from:afterpay) -unsubscribe -nieuwsbrief
```

```
after:YYYY/MM/DD (from:noreply@github.com OR from:obsidian.md OR from:tradingview.com) (receipt OR invoice OR payment)
```

If a vendor is known locally (gym, pension, student loan), add one extra query for that sender. Do not boil the ocean with `subject:invoice`.
