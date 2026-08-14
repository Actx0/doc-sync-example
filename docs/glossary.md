# Glossary

**Account** — a customer tenant with a plan, keys, and billing profile.

**Workspace** — an Actx0 knowledge workspace. This example syncs `docs/` into one.

**Checksum** — hash of file contents. Unchanged docs are skipped when the remote checksum matches.

**Label** — a `key=value` tag on a knowledge document. Sync only replaces documents that share both filename and labels.

**Dry run** — compare local files to remote documents without upload or delete.

**Dead-letter queue** — jobs that exhausted retries. Operators replay or discard them from the console.
