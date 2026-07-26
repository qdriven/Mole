# mo purge

> Remove old project artifacts.

## Synopsis

```bash
mo purge [options]
```

## Description

Finds heavy, rebuildable build artifacts inside project directories - `node_modules`, `target/`, `build/`, `dist/`, `.venv`, and similar - and lets you remove them interactively to reclaim space. Purge cleans the artifacts inside a project, never the project or worktree itself (worktree staleness is not decidable). Scan directories are configurable with `--paths`, and discovery of dot-directory containers must be added explicitly.

## Options

| Flag | Description |
| --- | --- |
| `--paths` | Edit the custom list of directories to scan |
| `--dry-run`, `-n` | Preview purge actions without making changes |
| `--include-empty` | Show zero-size project artifact directories too |
| `--debug` | Enable debug logging |
| `--help` | Show this help message |

## Examples

```bash
mo purge --dry-run          # preview reclaimable artifacts across scan paths
mo purge --paths            # configure which directories to scan
mo purge --include-empty    # include empty artifact dirs in the listing
```

## Notes

- Purge removes rebuildable artifacts, not the worktree, source, or any `.env`/ignored files outside the purge whitelist.
- `discover_project_dirs` skips dot-directories by default; containers like `~/.codex/worktrees` must be listed explicitly in the scan paths.

## Source

- [`bin/purge.sh`](../../bin/purge.sh) - command orchestration and section output
- [`lib/clean/project.sh`](../../lib/clean/project.sh) - discovery, artifact filtering, purge config
