# Runbook: core-api incidents

## Service is returning 5xx errors

1. Check the ECS service status in the AWS console (or `terraform output`
   for the cluster name).
2. Check recent deploys - did someone just ship a change?
3. Check RDS - is the database reachable and not under heavy load?
4. If a bad deploy is suspected, roll back to the previous task definition
   revision.

## Health checks failing

`core-api` exposes `/healthz`, `/health/live`, and `/health/ready`. A
failing `/health/ready` usually means the database connection pool is
exhausted or the DB itself is unreachable.

## Escalation

Page the on-call engineer via PagerDuty if the above doesn't resolve the
issue within 15 minutes.