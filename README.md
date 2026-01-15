# kmod-amneziawg-openwrt

AmneziaWG kernel module for OpenWrt. This is the recommended implementation for best performance.

## What is AmneziaWG?

AmneziaWG is a contemporary version of the WireGuard protocol with protection against Deep Packet Inspection (DPI) systems.

## Why Kernel Module?

The kernel module implementation offers:
- **Better performance** - Runs in kernel space, lower overhead
- **Lower resource usage** - Less CPU and memory compared to userspace
- **Recommended** - Default choice for most scenarios

## Installation

```bash
opkg update
opkg install kmod-amneziawg
```

## Dependencies

- `kmod-udptunnel4`
- `kmod-udptunnel6`
- `kmod-crypto-lib-chacha20poly1305`
- `kmod-crypto-lib-curve25519`

## Verification

Check if module is loaded:

```bash
lsmod | grep amneziawg
# or
cat /sys/module/amneziawg/version
```

## Compatibility

This kernel module requires:
- OpenWrt kernel with crypto API support
- Matching kernel version (vermagic)

## Troubleshooting

### Module fails to load

Check dmesg for errors:

```bash
dmesg | tail -20
```

### Version mismatch

If you get "version magic" errors, you need to rebuild the module against your specific kernel version. See the build instructions below.

## Building from Source

This package is automatically built as part of the OpenWrt build system. The source is fetched from:

```
https://github.com/amnezia-vpn/amneziawg-linux-kernel-module.git
```

## License

GPL-2.0

## Links

- [amneziawg-tools-openwrt](https://github.com/xyzmean/amneziawg-tools-openwrt) - CLI tools
- [luci-proto-amneziawg](https://github.com/xyzmean/luci-proto-amneziawg) - Web UI
- [amneziawg-go-openwrt](https://github.com/xyzmean/amneziawg-go-openwrt) - Userspace fallback
