# Authentication

All API requests send a bearer token:

```http
Authorization: Bearer ak_live_...
```

## Key types

| Prefix | Environment |
| --- | --- |
| `ak_test_` | `dev` and `staging` |
| `ak_live_` | `prod` |

Test keys cannot touch production data. Live keys are refused outside `prod`.

## Errors

| Status | Meaning |
| --- | --- |
| `401` | missing or unknown key |
| `403` | key is revoked or email is unconfirmed |
| `429` | rate limit; retry after `Retry-After` |

Rotate keys from the console or `POST /v1/keys`. The old key stays valid until you revoke it.
