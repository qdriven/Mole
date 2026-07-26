# mo uninstall

> Remove apps completely.

## Synopsis

```bash
mo uninstall [options]
```

## Description

Interactive app uninstaller. Lists installed apps, lets you select one or more, then removes the app bundle and its leftovers - preferences, caches, application support, launch agents/daemons, login items, and Group Container siblings - matching only by exact bundle ID or app-name variants. Leftover removal is gated by the shared-bundle-id sibling guard and protected-path checks, so a protected or still-present app is never torn down. By default removal is reversible; `--permanent` opts into direct deletion.

## Options

| Flag | Description |
| --- | --- |
| `--dry-run`, `-n` | Preview the uninstall plan without deleting anything |
| `--permanent` | Delete directly instead of routing through Trash (opt-in, irreversible) |
| `--list` | Print the app inventory and exit (read-only) |
| `--whitelist` | Redirects to `mo clean --whitelist` / `mo optimize --whitelist` |
| `--debug` | Show detailed operation logs |
| `--help`, `-h` | Show help |

## Examples

```bash
mo uninstall --list               # list installed apps
mo uninstall --dry-run            # preview teardown for a selected app
mo uninstall --permanent          # remove the selected app without Trash
```

## Notes

- `--list` is fully read-only and short-circuits before any destructive code.
- Helper remnants (launch services, login items, cask zap) are only removed after the parent app is confirmed gone and protected-path checks pass.
- Without `--permanent`, removed files go to Trash so you can recover them.

## Source

- [`bin/uninstall.sh`](../../bin/uninstall.sh) - command orchestration, app inventory
- [`lib/uninstall/batch.sh`](../../lib/uninstall/batch.sh) - batch execution, sibling guard, teardown
