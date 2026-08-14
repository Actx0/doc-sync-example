# Accounts API

## Create

```http
POST /v1/accounts
Content-Type: application/json

{
  "email": "ops@example.com",
  "plan": "pro"
}
```

Returns `201` with `id`, `plan`, and a one-time `api_key`.

## Get

```http
GET /v1/accounts/{id}
```

## List

```http
GET /v1/accounts?limit=50&offset=0
```

Default page size is 50. Maximum is 100.

## Update plan

```http
PATCH /v1/accounts/{id}
{
  "plan": "scale"
}
```

Upgrades apply immediately. Downgrades apply at renewal.
