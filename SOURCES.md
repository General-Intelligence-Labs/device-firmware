# Upstream sources

Each firmware image distributed from this repo is an aggregate of upstream open-source components and proprietary vendor blobs. This file documents the open-source components used. Each GitHub Release attaches a `SOURCES.txt` pinning the exact commit SHAs used for that release.

## GPL-licensed components

These ship inside every image. Under GPLv2 §3, recipients of the binary are entitled to the corresponding source on request.

| Component | License | Upstream |
|---|---|---|
| Linux kernel | GPLv2 | https://www.kernel.org |
| Das U-Boot | GPLv2 | https://www.denx.de/wiki/U-Boot |
| BusyBox | GPLv2 | https://busybox.net |
| eudev | GPLv2 / LGPLv2.1 | https://github.com/eudev-project/eudev |

To request the exact corresponding source for a specific release, [open a GitHub Issue](https://github.com/General-Intelligence-Labs/device-firmware/issues) referencing the release tag.

## Permissive components

| Component | License | Upstream |
|---|---|---|
| OpenSSL | OpenSSL / SSLeay (dual) | https://openssl.org |
| zlib | zlib | https://zlib.net |
| libcurl | curl (MIT-like) | https://curl.se |
| wpa_supplicant | BSD-3-Clause | https://w1.fi/wpa_supplicant/ |
| mongoose (embedded HTTP/WS server) | MIT | https://github.com/cesanta/mongoose |

## Proprietary

Proprietary binary components from silicon and module vendors are redistributed under their respective EULAs.

## Application layer

The application binary is General Intelligence Labs proprietary code. It is not a derivative work of GPL-licensed components in this image: it interacts with the Linux kernel only through the syscall boundary (explicitly exempted in the kernel's `COPYING` notice) and links against permissively licensed userspace libraries.
