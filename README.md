# Actx0 doc-sync example

Example repository for [Actx0/doc-sync](https://github.com/Actx0/doc-sync), the GitHub Action that syncs repository docs into an Actx0 workspace knowledge base.

Unchanged files are skipped by checksum. Changed files replace the previous document with the same filename and labels.

## Setup

1. Fork or copy this repository.
2. Add GitHub Actions secrets:
   - `ACTX0_WORKSPACE_ID`
   - `ACTX0_ACCESS_KEY`
3. Push to `main`, or run **Sync docs to Actx0** from the Actions tab.

The workflow in [`.github/workflows/sync-docs.yml`](.github/workflows/sync-docs.yml) checks out the repo and runs:

```yaml
- uses: Actx0/doc-sync@v1
  with:
    workspace_id: ${{ secrets.ACTX0_WORKSPACE_ID }}
    access_key: ${{ secrets.ACTX0_ACCESS_KEY }}
    tags: |
      tag: docs
      repo: ${{ github.repository }}
      team: platform
    paths: |
      docs/
    dry_run: ${{ github.event_name == 'pull_request' }}
```

Pull requests run in dry-run mode. Pushes to `main` upload and replace documents.

## Sample docs

Acme Platform knowledge used to exercise the action:

```text
docs/
├── getting-started.md
├── overview.md
├── architecture.md
├── faq.md
├── glossary.md
├── changelog.markdown      # .markdown
├── notes.txt               # plain text
├── ops-notes.txt
├── api/
│   ├── authentication.md
│   ├── accounts.md
│   └── billing.md
├── guides/
│   ├── onboarding.md
│   ├── local-development.md
│   ├── deploy.md
│   └── troubleshooting.md
├── runbooks/
│   ├── incident-response.md
│   ├── restore-from-backup.md
│   └── scale-workers.md
├── policies/
│   ├── security.md
│   └── data-retention.md
├── reference/
│   ├── env-vars.md
│   └── error-codes.md
└── snippets/
    └── curl-examples.mdx   # .mdx
```

`paths: docs/` walks that directory and syncs `.md`, `.mdx`, `.markdown`, and `.txt` files. You can also pass globs or individual files:

```yaml
paths: |
  docs/
  docs/*.md
  docs/getting-started.md
  docs/notes.txt
```

Overlapping patterns are de-duplicated. Hidden directories, `node_modules`, and `vendor` are skipped.

## Outputs

The action reports `uploaded`, `replaced`, `skipped`, and `failed`. This example prints those values after the sync step.

## CLI

The same binary the action installs can be run locally:

```zsh
./doc-sync \
  --workspace-id "$ACTX0_WORKSPACE_ID" \
  --access-key "$ACTX0_ACCESS_KEY" \
  --tags $'tag: docs\nteam: platform\nrepo: actx0/doc-sync-example' \
  --repo-dir . \
  --path docs/
```

See the [doc-sync README](https://github.com/Actx0/doc-sync) for inputs, tags, and release binaries.
