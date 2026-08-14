# Incident response

## Severity

| Level | Meaning | Page |
| --- | --- | --- |
| SEV1 | customers cannot sign in or pay | immediately |
| SEV2 | delayed invoices or webhooks | 15 minutes |
| SEV3 | console-only or single-tenant | next business hours |

## First 15 minutes

1. Declare the incident in `#incidents`.
2. Check gateway error rate and Postgres connections.
3. If error rate is above 5%, fail traffic to the last healthy region.
4. Freeze deploys until the incident is mitigated.

## After mitigation

Write a timeline, customer impact, and follow-ups. Link the postmortem from the audit log for that window.
