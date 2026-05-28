# device-firmware

Public firmware release channel for General Intelligence Labs devices.

## Devices

| Device | Tag prefix | Changelog |
|---|---|---|
| Egocentric headset | `ego-` | [CHANGELOG-ego.md](CHANGELOG-ego.md) |

Additional devices will be added to this channel over time.

## Releases

Each release is a git tag of the form `<device>-v<major>.<minor>.<patch>` (e.g. `ego-v0.1.0`). Tags publish to the [GitHub Releases page](https://github.com/General-Intelligence-Labs/device-firmware/releases) with these assets:

- `<device>-<tag>.img` — flashable firmware image
- `<device>-<tag>.img.sha256` — SHA-256 checksum

Per-device release cadence is independent.

## Flashing

See [docs/flashing.md](docs/flashing.md) for full instructions, prerequisites, and the recovery flow. Short version:

```bash
sha256sum -c <device>-<tag>.img.sha256
adb reboot loader
upgrade_tool UF <device>-<tag>.img
```

## License

Repository contents (README, docs, scripts) are MIT-licensed — see [LICENSE](LICENSE). Firmware binaries distributed via Releases are aggregates of many open-source components under different licenses; the per-component breakdown is in [SOURCES.md](SOURCES.md).
