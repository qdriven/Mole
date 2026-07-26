# mo touchid

> Configure Touch ID for sudo.

## Synopsis

```bash
mo touchid <subcommand> [options]
```

## Description

Guided setup for using Touch ID to authenticate `sudo` on macOS. It edits `/etc/pam.d/sudo_local` (preferred) safely via an atomic root-owned install, with status checking and a dry-run preview. This is a quality-of-life configuration tool, not a cleanup command.

## Subcommands

| Subcommand | Description |
| --- | --- |
| `enable` | Configure Touch ID for sudo (writes the `pam_tid.so` line) |
| `disable` | Remove the Touch ID configuration from sudo |
| `status` | Show whether Touch ID is currently enabled for sudo |

## Options

| Flag | Description |
| --- | --- |
| `--dry-run`, `-n` | Preview the PAM change without modifying any auth files |
| `--help`, `-h` | Show help |

## Examples

```bash
mo touchid status             # check current state
mo touchid enable --dry-run   # preview the setup
mo touchid enable             # configure Touch ID for sudo
sudo ls                       # unlock with Touch ID afterwards
```

## Notes

- Only one subcommand is accepted per run.
- PAM files are installed root-owned (`mode 444`) via an atomic swap; `--dry-run` makes no changes.

## Source

- [`bin/touchid.sh`](../../bin/touchid.sh)
