# device-firmware

Public firmware release channel for General Intelligence Labs devices.

## Devices

| Device | Tag prefix | Changelog |
|---|---|---|
| Egocentric headset | `ego-` | [CHANGELOG-ego.md](CHANGELOG-ego.md) |

Additional devices will be added to this channel over time.

## Releases

Each release is a git tag of the form `<device>-v<major>.<minor>.<patch>-<source-sha>` (e.g. `ego-v0.1.0-524803e`). The trailing 7-char SHA identifies the internal source commit the firmware was built from, and matches the `build` string the device reports over its HTTP info endpoint. Tags publish to the [GitHub Releases page](https://github.com/General-Intelligence-Labs/device-firmware/releases) with these assets:

- `<tag>.img` — flashable firmware image
- `<tag>.img.sha256` — image checksum
- `gi-flash` — single-binary flasher (Linux x86_64; tested on Ubuntu 24.04 LTS only)
- `gi-flash.sha256` — flasher checksum
- `SOURCES.txt` — pinned source commit + dependency SHAs for this build

Per-device release cadence is independent.

## Flashing

Download the `.img`, its `.sha256`, and `gi-flash` from the release page, then:

```bash
chmod +x gi-flash
./gi-flash <tag>.img
```

First run prompts for sudo to install USB permissions; subsequent flashes need no sudo. See [docs/flashing.md](docs/flashing.md) for the full reference, verification steps, troubleshooting, and the recovery path for unresponsive devices.

## License

Repository contents (README, docs, scripts) are MIT-licensed — see [LICENSE](LICENSE). Firmware binaries distributed via Releases are aggregates of many open-source components under different licenses; the per-component breakdown is in [SOURCES.md](SOURCES.md).
