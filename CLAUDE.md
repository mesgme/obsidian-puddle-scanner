# Puddle App

This repo is a swamp application created by the Puddle platform.

## First-time setup

After cloning, initialise the swamp project:

```bash
swamp init --force --tool claude
```

This generates `.swamp.yaml` and the local runtime directory. It is safe
to re-run.

## Structure

| Path | Purpose |
|------|---------|
| `workflows/` | Swamp workflow definitions (YAML) |
| `grants/` | Authorisation policies for swamp serve |
| `puddle-run.sh` | Delivery wrapper — the requester runs this |

## Development

1. Edit the workflow in `workflows/workflow.yaml`
2. Test locally: `swamp workflow run <name> --input key=value`
3. Test via serve: `swamp workflow run <name> --server http://localhost:9090 --input key=value`
4. Update `puddle-run.sh` with the correct `APP_NAME` and `WORKFLOW` values

## Conventions

- Workflows default to `dryRun: true` — pass `dryRun=false` for real runs
- Use vault expressions for secrets, never hardcoded values
- Tag workflows with `puddle: "true"` so they are discoverable
