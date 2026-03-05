# ADR 0001: Use PostgreSQL for core-api

## Status

Accepted

## Context

`core-api` needs a relational store for orders with reasonably strong
consistency guarantees, and the team already has operational experience
running Postgres.

## Decision

We will use PostgreSQL (via RDS) as the primary datastore for `core-api`,
accessed through SQLAlchemy and managed with Alembic migrations.

## Consequences

- We get transactions and strong consistency for order writes.
- We take on RDS operational overhead (backups, patching, failover) instead
  of using a fully managed serverless option.
- Schema changes go through Alembic migrations, which need review like any
  other code change.