# mo remove

> Remove Mole from the system.

## Synopsis

```bash
mo remove [--dry-run]
```

## Description

Uninstalls Mole completely: Homebrew formula (if installed that way), the manual `mole`/`mo` entry scripts in `/usr/local/bin`, the installed modules and libraries under `~/.config/mole`, and Mole's cache/log files. It lists exactly what it will delete before deleting. Use `--dry-run` to preview the full removal plan first.

## Options

| Flag | Description |
| --- | --- |
| `--dry-run`, `-n` | Preview the removal plan without deleting anything |

## Examples

```bash
mo remove --dry-run      # preview everything that would be removed
mo remove                # remove Mole from the system
```

## Notes

- Removal covers all install channels Mole detects (Homebrew + manual + config/cache/logs).
- Preview first with `--dry-run` to confirm the file list before committing.

## Source

- Dispatched inline in [`mole`](../../mole) (router)
- [`lib/manage/remove.sh`](../../lib/manage/remove.sh) - removal flow
