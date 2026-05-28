# Flashing

Firmware is flashed with `gi-flash`, a single-binary tool included as a release asset. The first run installs USB permissions; subsequent flashes are a one-command operation.

## Requirements

- Linux x86_64 host.
- A USB cable that carries data (some charge-only cables won't enumerate).

## Flash

From the release page, download these into the same directory:

- `<tag>.img` — the firmware image
- `<tag>.img.sha256` — image checksum
- `gi-flash` — the flasher

Connect the device, make `gi-flash` executable, and run it:

```bash
chmod +x gi-flash
./gi-flash <tag>.img
```

That's it. On first run, you'll be prompted for sudo to install a USB udev rule, add your user to the `plugdev` group, and install `adb`. After that, every subsequent flash needs no sudo.

The tool auto-verifies the image checksum, reboots the device into loader mode over USB, writes the new firmware, and the device reboots itself into the new image in under a minute.

## Verifying the device after flash

Once the device reboots, it presents as a USB serial + USB-Ethernet device with mDNS hostname `GILABS-XXXXXX.local`. A few seconds after the flash completes:

```bash
adb devices            # should list the device with status "device"
```

## Troubleshooting

| Symptom | Cause / fix |
|---|---|
| `checksum verification FAILED` | Image download was corrupted, or the `.sha256` is from a different release. Re-download. |
| `no device detected in loader mode after 30s` | The device didn't soft-reboot — most often a non-data USB cable. Try a different cable or USB port. |
| Permission errors talking to USB | The udev rule or `plugdev` group didn't take effect. Re-run `gi-flash` — it'll auto-activate; if that fails, log out and back in. |

## Recovery (device won't boot)

A fielded device should never need this path. In the very rare case that a device is fully unresponsive — won't boot, doesn't appear to `adb devices`, no signs of life across multiple cables/ports — recovery requires **opening the device enclosure** to access an internal `BOOT` contact.

**Please contact GI Labs before attempting this.** Opening the device may void warranty, and the recovery procedure varies by hardware revision; we'll walk you through it or arrange a replacement.
