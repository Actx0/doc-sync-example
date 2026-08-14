# Environment variables

| Name | Required | Notes |
| --- | --- | --- |
| `ACME_ENV` | yes | `dev`, `staging`, or `prod` |
| `DATABASE_URL` | yes | Postgres DSN |
| `REDIS_URL` | yes | queue and rate limits |
| `ACME_READ_ONLY` | no | set `true` during restores |
| `ACTX0_WORKSPACE_ID` | for doc-sync | GitHub Actions secret |
| `ACTX0_ACCESS_KEY` | for doc-sync | GitHub Actions secret |
| `ACTX0_BASE_URL` | no | defaults to `https://app.actx0.com` |

`ACME_ENV` selects key prefixes (`ak_test_` vs `ak_live_`). A mismatch refuses every authenticated request.
