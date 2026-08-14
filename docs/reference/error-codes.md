# Error codes

API errors use a stable `code` field.

| Code | HTTP | Meaning |
| --- | --- | --- |
| `unauthenticated` | 401 | missing or unknown API key |
| `forbidden` | 403 | revoked key or insufficient role |
| `not_found` | 404 | unknown account or invoice |
| `rate_limited` | 429 | too many requests |
| `plan_mismatch` | 409 | feature not on the current plan |
| `invoice_not_refundable` | 409 | already void or fully refunded |
| `validation_error` | 422 | request body failed schema checks |
| `internal` | 500 | unexpected error; retry with backoff |

Clients should retry `429` and `500` only. Other codes need a new request.
