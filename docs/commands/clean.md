# mo clean

> Free up disk space.

## Synopsis

```bash
mo clean [options]
```

## Description

Runs Mole's cleanup modules across system caches, browser caches, app caches, developer-tool caches, cloud/app support data, and Apple Silicon caches. It previews every reclaimable target before deleting, respects the app-protection and path-protection rules, and routes user-facing removals through Trash. System-cache cleanup needs sudo; run `sudo -v` first for a full preview and clean.

## Options

| Flag | Description |
| --- | --- |
| `--dry-run`, `-n` | Preview what would be cleaned without making changes |
| `--external <path>` | Clean macOS metadata (`.DS_Store`, `.Spotlight-V100`, etc.) from an external volume directory |
| `--whitelist` | Manage protected paths that cleanup must never touch |
| `--debug` | Show detailed operation logs |
| `--help`, `-h` | Show help |

## Examples

```bash
mo clean --dry-run                 # preview the full cleanup plan
sudo -v && mo clean --dry-run      # include sudo-gated system caches in the preview
mo clean --whitelist               # add or review protected paths
mo clean --external /Volumes/Backup  # strip OS metadata from an external volume
```

## Notes

- Always run `--dry-run` first to review the exact deletion plan.
- Cleanup that needs privileged access is gated behind an explicit sudo prompt; typed input is never treated as a skip.
- Protected paths (`/System`, `/Library/Apple`, `com.apple.*`, and anything you whitelist) are never removed.

## Source

- [`bin/clean.sh`](../../bin/clean.sh) - command orchestration
- [`lib/clean/`](../../lib/clean) - cleanup modules
