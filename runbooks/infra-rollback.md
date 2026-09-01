# Runbook: rolling back an infra change

If a Terraform apply causes problems in staging or production:

1. Identify the last known-good commit in `infra` (check the PR history).
2. Run `terraform plan` against that commit's state to confirm what would
   change.
3. Coordinate with the team before applying - infra rollbacks can be
   disruptive if the schema or resources changed underneath.
4. Apply and verify via the runbook for the affected service.

> Draft - still need input from Marco on the RDS-specific rollback caveats.