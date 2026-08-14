# Troubleshooting

## Sync skipped every file

Checksums already match the documents in the workspace. Edit a file under `docs/` and push again, or confirm the workflow is using the same labels as the existing knowledge documents.

## Sync failed with authentication errors

Check that `ACTX0_WORKSPACE_ID` and `ACTX0_ACCESS_KEY` are set for this repository. The access key must belong to the same workspace.

## Nested docs were not uploaded

Directory paths such as `docs/` include nested markdown and text files. Glob patterns like `docs/*.md` only match the top level. Use `docs/**/*.md` when you want nested markdown through a glob.

## Dry run did not change knowledge

That is expected. `dry_run: true` compares checksums and prints `upload`, `replace`, or `skip` without calling the Actx0 write APIs.
