# mo completion

> Set up shell tab completion.

## Synopsis

```bash
mo completion <shell> [options]
```

## Description

Installs tab completion for `mo`/`mole` into your shell config (bash, zsh, or fish). For bash and zsh it appends an `eval` line to the right rc file; for fish it writes completion files under `~/.config/fish/completions/`. Stale entries from previous installs are cleaned up. Use `--dry-run` to preview the config edits before applying them.

## Subcommands

| Subcommand | Description |
| --- | --- |
| `bash` | Generate / install bash completion |
| `zsh` | Generate / install zsh completion |
| `fish` | Generate / install fish completion |

Running `mo completion` with no argument auto-detects the current shell.

## Options

| Flag | Description |
| --- | --- |
| `--dry-run`, `-n` | Preview the completion edits without writing them |
| `--help`, `-h` | Show help |

## Examples

```bash
mo completion --dry-run      # preview the edits for the current shell
mo completion zsh            # install zsh completion
mo completion fish           # write fish completion files
```

## Notes

- Stale source-based completion entries from earlier installs are removed automatically.
- Open a new shell (or re-source your rc file) after installing for completions to take effect.

## Source

- [`bin/completion.sh`](../../bin/completion.sh)
