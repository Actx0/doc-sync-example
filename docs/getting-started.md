# Getting started

This repository is a working example of [Actx0/doc-sync](https://github.com/Actx0/doc-sync).

The GitHub Action uploads markdown and text files from `docs/` into an Actx0 workspace knowledge base. Unchanged files are skipped by checksum; changed files replace the previous document with the same filename and labels.

## What you need

1. An [Actx0](https://app.actx0.com) workspace
2. A workspace ID and access key stored as GitHub Actions secrets:
   - `ACTX0_WORKSPACE_ID`
   - `ACTX0_ACCESS_KEY`

## What gets synced

Every `.md`, `.mdx`, `.markdown`, and `.txt` file under `docs/` is synced, including nested directories. Hidden folders, `node_modules`, and `vendor` are ignored.

On pull requests the workflow runs in dry-run mode. On `main` it uploads and replaces documents.
