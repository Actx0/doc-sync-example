# Architecture

Acme Platform is three services behind an API gateway.

```
clients → gateway → api
                 → console
worker ← queue ← api
```

## API

Stateless HTTP service. Reads and writes Postgres. Enqueues jobs for invoices, emails, and webhooks.

## Worker

Consumes the queue. Idempotent handlers; failed jobs retry with backoff, then land in a dead-letter queue.

## Console

Operator UI. Talks to the API with service credentials. No direct database access.

## Data stores

| Store | Used for |
| --- | --- |
| Postgres | accounts, invoices, audit log |
| Redis | sessions, rate limits, queue |
| Object storage | invoice PDFs and exports |
