# mo history

> Review cleanup activity.

## Synopsis

```bash
mo history [options]
```

## Description

Shows recent Mole operation and deletion activity from the operation log. Useful for reviewing what `clean`, `uninstall`, `purge`, and `installer` actually removed, and for auditing after the fact. Supports JSON export for scripts and log archival.

## Options

| Flag | Description |
| --- | --- |
| `--json` | Output history as JSON |
| `--limit N` | Show the most recent N entries, 1-200 |
| `--help`, `-h` | Show help |

## Examples

```bash
mo history                  # show recent activity
mo history --limit 50       # show the last 50 entries
mo history --json           # export history as JSON
```

## Notes

- History is read from the project operation-log path; it is read-only here.

## Source

- [`bin/history.sh`](../../bin/history.sh) - command orchestration
- [`lib/core/history.sh`](../../lib/core/history.sh) - history parsing and formatting
