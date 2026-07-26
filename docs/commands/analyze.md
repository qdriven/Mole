# mo analyze

> Explore disk usage.

## Synopsis

```bash
mo analyze [path] [options]      # `mo analyse` is also accepted
```

## Description

Launches the Go-based disk-analysis TUI. It scans a target directory (default: the home directory) and presents a navigable, sortable view of the largest files and folders so you can drill into where space is going. Drives ad hoc cleanup from inside the TUI through the safe deletion helpers. Use a path argument to scope the scan, e.g. `mo analyze /Volumes` to inspect external drives only.

## Options

| Flag | Description |
| --- | --- |
| `[path]` | Directory to scan (defaults to `$HOME`) |
| `--json` | Output the analysis as JSON instead of launching the TUI |
| `--help`, `-h` | Show help |

## Examples

```bash
mo analyze                   # scan the home directory, launch the TUI
mo analyze /Volumes          # analyze external drives only
mo analyze ~/Library --json  # machine-readable analysis of ~/Library
```

## Notes

- Scans are timeout-bounded; slow disks degrade to partial output rather than hanging.
- Ad hoc deletion from the TUI routes through the same safe deletion funnel as `clean` (Trash routing, path protection, dry-run aware).

## Source

- [`bin/analyze.sh`](../../bin/analyze.sh) - thin launcher that `exec`s the bundled binary
- [`cmd/analyze/`](../../cmd/analyze) - Go TUI source (`main.go`, `model.go`, `update.go`, `scanner.go`)
