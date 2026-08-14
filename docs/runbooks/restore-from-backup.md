# Restore from backup

Postgres is snapshotted every hour and retained for 14 days.

## Staging restore (practice)

1. Create a new staging cluster from a snapshot.
2. Point a preview API at that cluster.
3. Confirm account counts and the latest invoice IDs.

## Production restore

1. Page the on-call owner. This is SEV1.
2. Stop API writes (`ACME_READ_ONLY=true`).
3. Restore the latest snapshot taken *before* the corruption window.
4. Replay the WAL if the snapshot is more than 15 minutes behind.
5. Smoke-test auth and billing, then disable read-only mode.

Never restore production over the live cluster without a snapshot of the broken state.
