# Onboarding

1. Create an account with `POST /v1/accounts`.
2. Confirm the email from the inbox used at signup.
3. Store the API key in a secret manager. It is shown once.
4. Call `GET /v1/accounts/{id}` to verify the key.
5. Subscribe to `invoice.paid` and `invoice.failed` webhooks.

## First invoice

New accounts get a `$0` draft invoice. It becomes `open` after the first paid usage or a plan upgrade.

## Console access

Invite operators from **Settings → Members**. Owners can refund and rotate keys. Operators can view jobs and replay the dead-letter queue.
