# mo installer

> Find and remove installer files.

## Synopsis

```bash
mo installer [options]
```

## Description

Scans common download locations (`~/Downloads`, `~/Desktop`, `~/Documents`, `~/Public`, `~/Library/Downloads`, `/Users/Shared`) for leftover installer payloads - `.dmg`, `.pkg`, `.mpkg`, `.iso`, `.xip`, and installer `.zip` archives - and lets you remove them interactively. Scan depth is bounded. Use `--dry-run` to preview the plan and the space each file occupies before deleting.

## Options

| Flag | Description |
| --- | --- |
| `--dry-run`, `-n` | Preview the installer cleanup plan without deleting |
| `--debug` | Show detailed logs |
| `--help`, `-h` | Show help |

## Examples

```bash
mo installer --dry-run      # list installer files that would be removed
mo installer                # interactive selection and removal
```

## Notes

- Only installer-format files are matched; user documents and archives are left alone.
- Removal routes through the safe deletion helpers (Trash routing, path protection, dry-run aware).

## Source

- [`bin/installer.sh`](../../bin/installer.sh) - discovery, immutable delete-plan validation, paginated selection
