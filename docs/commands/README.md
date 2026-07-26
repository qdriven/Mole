# Mole Command Reference

Mole is a terminal-first macOS maintenance toolkit. Every command is reachable as `mo <command>` (or `mole <command>`), and most destructive commands support a `--dry-run` preview. This directory holds one doc per command.

## Commands

| Command | Summary | Doc |
| --- | --- | --- |
| `mo clean` | Free up disk space | [clean.md](clean.md) |
| `mo uninstall` | Remove apps completely | [uninstall.md](uninstall.md) |
| `mo optimize` | Refresh caches and services | [optimize.md](optimize.md) |
| `mo analyze` | Explore disk usage | [analyze.md](analyze.md) |
| `mo status` | Monitor system health | [status.md](status.md) |
| `mo history` | Review cleanup activity | [history.md](history.md) |
| `mo purge` | Remove old project artifacts | [purge.md](purge.md) |
| `mo installer` | Find and remove installer files | [installer.md](installer.md) |
| `mo touchid` | Configure Touch ID for sudo | [touchid.md](touchid.md) |
| `mo completion` | Set up shell tab completion | [completion.md](completion.md) |
| `mo update` | Update to latest version | [update.md](update.md) |
| `mo remove` | Remove Mole from the system | [remove.md](remove.md) |
| `mo --help` | Show help | see below |
| `mo --version` | Show version | see below |

## Built-in

These two take no options.

```bash
mo --help        # or: mo help / mo -h    — list every command and common options
mo --version     # or: mo version / mo -V — print the installed version
```

## Conventions

- **Dry-run first.** `clean`, `uninstall`, `optimize`, `purge`, `installer`, `touchid`, `completion`, and `remove` all accept `--dry-run` (often `-n`) to preview exactly what would change without touching the filesystem.
- **Sudo is gated.** Commands that need privileged access prompt explicitly; they never treat typed password input as a skip. Cache credentials first with `sudo -v` when a command mentions admin access.
- **Recoverable removals.** User-facing cleanup routes through Trash where the project expects recoverability; `uninstall --permanent` is the explicit opt-out.
- **`--debug`** turns on detailed operation logs for any command that supports it.

## Building and installing locally

See the repo-root [`Taskfile.yml`](../../Taskfile.yml):

```bash
task build       # build cmd/analyze and cmd/status into bin/
task install     # build, then install to /usr/local/bin + ~/.config/mole (no release download)
```
