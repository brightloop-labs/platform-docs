# Runbook: billing-sync mismatches

`billing-sync` runs nightly and posts a Slack message to `#billing-alerts`
when it finds mismatches between `core-api` orders and Stripe charges.

## Triage steps

1. Open the alert and note the `order_id`(s) flagged.
2. Look up the order in `core-api` and the corresponding charge in the
   Stripe dashboard.
3. Common causes:
   - `missing_charge` - the order was created but the charge failed or
     hasn't settled yet. Usually resolves itself within 24h.
   - `amount_mismatch` - check for a partial refund or a currency
     conversion issue.
4. If it's a real discrepancy (not a timing issue), loop in finance before
   taking any corrective action.