# Deploy

## Order

1. Migrate Postgres (`make migrate`).
2. Deploy workers, then API, then console.
3. Run smoke checks: health, auth, create-account.

Workers first so new job types exist before the API enqueues them.

## Environments

| Environment | Git ref | Approve |
| --- | --- | --- |
| `staging` | any `main` commit | automatic |
| `prod` | tagged `v*` release | two operators |

## Rollback

Redeploy the previous image tag. Do not reverse migrations unless the release notes say it is safe. Queue payloads stay compatible for one minor version.
