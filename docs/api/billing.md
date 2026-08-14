# Billing API

## List invoices

```http
GET /v1/invoices?account_id=acc_123&status=open
```

Statuses: `draft`, `open`, `paid`, `void`.

## Get invoice

```http
GET /v1/invoices/{id}
```

The response includes `pdf_url` when the worker has finished rendering.

## Refund

```http
POST /v1/invoices/{id}/refund
{
  "amount_cents": 1500,
  "reason": "duplicate_charge"
}
```

Partial refunds are allowed until the remaining amount is zero. Console operators and the account owner can refund; read-only members cannot.
