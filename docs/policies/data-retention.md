# Data retention

| Data | Retention |
| --- | --- |
| Account records | life of the account plus 30 days |
| Invoices | 7 years |
| Audit log | 2 years |
| Application logs | 30 days |
| Database backups | 14 days |
| Dead-letter jobs | 7 days after last retry |

## Deletion

Account deletion anonymizes PII within 30 days. Invoice rows stay for the legal retention window with the email replaced by a hash.

## Exports

Owners can request a JSON export of accounts, invoices, and webhook deliveries. Exports expire after 48 hours.
