# mo status

> Monitor system health.

## Synopsis

```bash
mo status [options]
```

## Description

Launches the Go-based system status panel - a compact, read-only health dashboard covering CPU, memory, disk, battery, network, and high-CPU process alerts. It is intentionally not an iStat clone or alerting daemon: it surfaces actionable signals in a one-screen summary with stable JSON/NDJSON output for automation. Use `--watch` to stream metrics continuously.

## Options

| Flag | Description |
| --- | --- |
| `--json` | Output metrics as JSON (one-shot) instead of launching the TUI |
| `--watch` | Stream metrics continuously as newline-delimited JSON |
| `--interval <dur>` | With `--watch`, collection interval (e.g. `1s`, `2s`); defaults to `1s` |
| `--proc-cpu-threshold <float>` | Alert when a process stays above this CPU percent (default `100`) |
| `--proc-cpu-window <dur>` | Continuous duration a process must exceed the threshold (default `5m`) |
| `--proc-cpu-alerts` | Enable persistent high-CPU process alerts (default enabled) |
| `--help`, `-h` | Show help |

## Examples

```bash
mo status                       # interactive health dashboard
mo status --json                # one-shot JSON for scripts
mo status --watch               # stream NDJSON metrics every second
mo status --watch --interval 2s # stream every 2 seconds
```

## Notes

- The TUI renders a compact read-only summary; collection and JSON/NDJSON contracts are independent of rendering.
- High-CPU alerts combine a threshold and a sustained window to avoid noise from brief spikes.

## Source

- [`bin/status.sh`](../../bin/status.sh) - thin launcher that `exec`s the bundled binary
- [`cmd/status/`](../../cmd/status) - Go source (`main.go`, `view.go`, `metrics_*.go`, `process_watch.go`)
