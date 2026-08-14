# Local development

## Services

```zsh
docker compose up postgres redis
make run-api
make run-worker
```

API listens on `http://127.0.0.1:8080`. Console uses the same origin with `ACME_ENV=dev`.

## Test key

Seed a test account:

```zsh
make seed
```

This prints an `ak_test_` key. Never commit it.

## Docs sync

From a clone of this example, dry-run the knowledge sync without writing to Actx0:

```zsh
./doc-sync --dry-run --workspace-id "$ACTX0_WORKSPACE_ID" \
  --access-key "$ACTX0_ACCESS_KEY" --path docs/
```
