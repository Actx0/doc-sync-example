# FAQ

## How do I create an account?

`POST /v1/accounts` with an email and plan. The API returns an account ID and an unpublished API key. Confirm the email before the key can call billing endpoints.

## Can I change plans mid-cycle?

Yes. Upgrades take effect immediately and are prorated. Downgrades apply at the next renewal.

## Where are invoices stored?

Invoice records live in Postgres. PDFs are written to object storage and linked from `GET /v1/invoices/{id}`.

## Who can use the console?

Workspace owners and operators. Read-only members can view accounts and invoices but cannot issue refunds.

## How do I rotate an API key?

Create a second key, switch clients, then revoke the old key. Revocation is immediate.
