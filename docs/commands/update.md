# mo update

> Update to latest version.

## Synopsis

```bash
mo update [--force] [--nightly]
```

## Description

Updates Mole to the latest stable release from the configured install channel (Homebrew or manual install). It detects the install channel, fetches the update, verifies release assets, and reinstalls in place through the same `install.sh` path used for a fresh install. Verification failure is fail-closed - a checksum or attestation mismatch aborts rather than downgrading to an unverified source build. Use `--nightly` to install the latest unreleased `main` build, or `--force` to reinstall the current stable version.

## Options

| Flag | Description |
| --- | --- |
| `--force`, `-f` | Force reinstall the latest stable version |
| `--nightly` | Install the latest unreleased `main`-branch build (source build) |

## Examples

```bash
mo update                # update to the latest stable release
mo update --force        # reinstall the latest stable version
mo update --nightly      # install the latest nightly (main) build
```

## Notes

- Cache sudo credentials first (`sudo -v`) when the install prefix (`/usr/local/bin`) needs admin access.
- A nightly install warns that it is an unreleased source build.
- `install.sh` stays fail-closed on verification failure; it never silently downgrades to a source build.

## Source

- Dispatched inline in [`mole`](../../mole) (router)
- [`lib/manage/update.sh`](../../lib/manage/update.sh) - version discovery, channel detection, update flow
