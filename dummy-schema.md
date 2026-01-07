# Dummy schema for examples

This document describes a minimal schema used in the example queries and scripts.

Tables

1) users
- user_id (string)
- created_at (timestamp)
- country (string)
- plan (string) -- e.g., "free_trial", "monthly", "annual", "ad_supported"
- signup_source (string) -- e.g., "web", "ios", "android", "partner"

2) subscriptions
- subscription_id (string)
- user_id (string)
- start_date (date)
- end_date (date) -- null if active
- amount (decimal)
- currency (string)
- status (string) -- "active", "cancelled", "expired"
- churn_reason (string) -- optional free text

3) content
- content_id (string)
- title (string)
- genre (string)
- type (string) -- "movie", "episode", "series"
- release_year (int)
- duration_sec (int)

4) views
- view_id (string)
- user_id (string)
- content_id (string)
- start_ts (timestamp)
- end_ts (timestamp)
- device (string) -- "tv", "mobile", "web"
- watch_seconds (int)
- completed (boolean)

5) sessions
- session_id (string)
- user_id (string)
- ts (timestamp) -- session start
- device (string)
- app_version (string)
- region (string)

Notes
- These are intentionally minimal. For privacy and production, add hashed IDs, event-level instrumentation, schema evolution, and data lineage tracking.
- Use this schema to seed a small dataset in SQLite/DuckDB/Postgres for experimenting.
