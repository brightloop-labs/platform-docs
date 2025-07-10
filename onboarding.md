# Engineering onboarding

Welcome to the team! This doc covers what you need to get productive in
your first week.

## Accounts and access

1. Ask your manager to add you to the `brightloop-labs` GitHub org.
2. Request access to the shared 1Password vault for service credentials.
3. Get added to the `#eng` and `#incidents` Slack channels.

## Local environment

Most of our services are Python or TypeScript. You'll want:

- Python 3.11+
- Node 20+
- Docker Desktop (or an equivalent local Docker setup)

## Repositories

- `core-api` - the main backend service (FastAPI)
- `web-dashboard` - internal ops dashboard (React)
- `billing-sync` - nightly billing reconciliation worker
- `infra` - Terraform for our AWS environment

## First week checklist

- [ ] Clone and run `core-api` locally via docker-compose
- [ ] Clone and run `web-dashboard` locally, pointed at your local `core-api`
- [ ] Read `architecture.md`
- [ ] Shadow an on-call handoff