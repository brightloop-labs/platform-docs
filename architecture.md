# Architecture overview

## Services

- **core-api** - FastAPI backend, source of truth for orders and refunds.
  Backed by Postgres (RDS).
- **web-dashboard** - React frontend used by support and ops to look up and
  manage orders.
- **billing-sync** - a scheduled worker that reconciles `core-api` orders
  against Stripe charges and posts a Slack alert on mismatches.

## Infrastructure

Everything runs on AWS, provisioned via Terraform (`infra` repo): a VPC,
an ECS Fargate cluster running `core-api`, and an RDS Postgres instance.

## Data flow

```
web-dashboard --> core-api --> RDS (Postgres)
                     ^
                     |
              billing-sync <--> Stripe
```

`billing-sync` runs nightly, pulls recent Stripe charges, and cross-checks
them against orders recorded in `core-api`. Mismatches are posted to Slack.