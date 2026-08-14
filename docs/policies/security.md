# Security

## Secrets

API keys, database URLs, and Actx0 access keys live in the environment or a secret manager. They are not committed to git.

## Network

- Postgres and Redis are private.
- The API and console are public behind the gateway.
- Object storage buckets block public list; invoice URLs expire in 15 minutes.

## Access

Production console access requires SSO and a hardware key. Break-glass accounts are stored offline and audited when used.

## Disclosure

Report vulnerabilities to security@example.com. Do not file public issues for production credential leaks.
