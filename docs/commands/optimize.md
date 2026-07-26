# mo optimize

> Refresh caches and services.

## Synopsis

```bash
mo optimize [options]      # British spelling `mo optimise` is also accepted
```

## Description

Runs bounded, explainable system maintenance tasks - rebuilding the LaunchServices database, flushing DNS, refreshing Spotlight indexing, clearing quarantine attributes, and similar reversible maintenance. Every task is previewable with `--dry-run` and skips protected and whitelisted plists before attempting removal. Optimize is intentionally narrow: it does not add background agents, schedulers, or broad system modification.

## Options

| Flag | Description |
| --- | --- |
| `--dry-run` | Preview the maintenance tasks without applying them |
| `--whitelist` | Manage protected items that optimize must skip |
| `--debug` | Show detailed operation logs |
| `--help`, `-h` | Show help |

## Examples

```bash
mo optimize --dry-run      # preview which tasks would run
mo optimize --whitelist    # manage protected plists/items
mo optimize                # run the maintenance tasks
```

## Notes

- Preference repair and cleanup always skip protected and whitelisted plists.
- Tasks are designed to be explained in one terminal screen and tested without real authorization prompts.

## Source

- [`bin/optimize.sh`](../../bin/optimize.sh) - command orchestration
- [`lib/optimize/tasks.sh`](../../lib/optimize/tasks.sh) - task registration and maintenance actions
