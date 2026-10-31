# Enciphered Kernel v1.1 for Samsung Galaxy Tab A8 10.5 (2021)

[![GitHub Release](https://img.shields.io/github/v/release/encipherdev/enciphered-kernel-4.14?color=blue&logo=github)](https://github.com/encipherdev/enciphered-kernel-4.14/releases/tag/v1.1)
[![XDA Thread](https://img.shields.io/badge/XDA-Thread-orange?logo=xda-developers)](https://xdaforums.com/t/kernel-sm-x200-sm-x205-enciphered-kernel-v1-1-resukisu-v4-1-0-susfs-v2-1-0-wireguard-bbr-nethunter.4807120/)
[![Linux Kernel](https://img.shields.io/badge/Linux-4.14.199-green.svg?logo=linux)](https://kernel.org)
[![KernelSU](https://img.shields.io/badge/ReSukiSU-v4.1.0-brightgreen.svg)](https://github.com/ReSukiSU/ReSukiSU)
[![SuSFS](https://img.shields.io/badge/SuSFS-v2.1.0-red.svg)](https://gitlab.com/simonpunk/susfs4ksu)
[![License](https://img.shields.io/badge/License-GPL%20v2-blue.svg)](LICENSE)

High-performance, pen-testing ready custom kernel featuring **ReSukiSU Multi-Manager Root**, **SuSFS v2.1.0 Inline Hooking**, **Universal Vendor Module Fix**, **WireGuard**, **TCP BBR**, and **Kali NetHunter BadUSB** for Samsung Galaxy Tab A8 10.5 (`SM-X200` Wi-Fi / `SM-X205` LTE).

---

## Supported Devices

| Model | Code Name | Connectivity | Chipset |
| :--- | :--- | :--- | :--- |
| **SM-X200** | `gta8wifi` | Wi-Fi Only | Unisoc Tiger T618 (`ums512_25c10`) |
| **SM-X205** | `gta8` | 4G LTE + Wi-Fi | Unisoc Tiger T618 (`ums512_25c10`) |

---

## Key Features

- **ReSukiSU v4.1.0 In-Tree Driver:**
  - Multi-Manager Support: Fully compatible with **SukiSU Ultra**, **ReSukiSU**, **KowSU**, **KernelSU-Next**, **WildKSU**, and **Official KernelSU**.
- **SuSFS v2.1.0 (Inline Hook):**
  - Advanced root and kernel symbol hiding (`SUS Path`, `SUS Mount`, `SUS Kstat`, `Spoof Uname`).
  - Passes Google Play Integrity (`MEETS_DEVICE_INTEGRITY` & `MEETS_STRONG_INTEGRITY`) when paired with Play Integrity Fix modules.
- **Universal OS Bootability & Hardware Fix:**
  - Patched `kernel/module.c` with a universal symbol CRC & vermagic bypass.
  - Allows all stock Samsung proprietary vendor modules (`mali_gondul.ko` Mali G52 GPU, `sprdwl_ng.ko` Wi-Fi, `sprdbt_tty.ko` Bluetooth, camera, sensors, and audio DSP) to load without mismatch errors on both **Stock Samsung One UI (Android 11–13)** and **GSIs / AOSP (Android 13–16)**.
- **WireGuard In-Tree Kernel Driver:**
  - Native kernel-level WireGuard VPN driver for ultra-low latency and maximum bandwidth.
- **TCP BBR Congestion Control & FQ-Codel:**
  - Replaced standard BIC/Cubic default with Google TCP BBR algorithm and Fair Queueing for enhanced networking speeds.
- **Kali NetHunter BadUSB & Wi-Fi Injection:**
  - USB ConfigFS HID driver enabled (`/dev/hidg0`) for USB Rubber Ducky / BadUSB payloads.
  - External wireless monitor mode and packet injection drivers (`ath9k_htc`, `rt2800usb`, `rtl8187`, `rtl8192cu`).
- **Memory & Storage:**
  - ZRAM compression with LZ4 and hardware-accelerated ZSTD support.
- **SELinux:**
  - Full compatibility with Enforcing SELinux mode.

---

## Installation Guide

### Option 1: Custom Recovery (TWRP / OrangeFox)
1. Download `EncipheredKernel-SM-X200-v1.1.zip` (Wi-Fi) or `EncipheredKernel-SM-X205-v1.1.zip` (LTE) from [Releases](https://github.com/encipherdev/enciphered-kernel-4.14/releases/tag/v1.1).
2. Reboot into recovery (TWRP / OrangeFox).
3. Tap **Install**, select the downloaded ZIP, and swipe to flash.
4. Reboot system.

### Option 2: ADB Sideload
```bash
adb reboot sideload
adb sideload EncipheredKernel-SM-X200-v1.1.zip
```

---

## Recommended Root Manager

Install **SukiSU Ultra Manager APK** from the [v1.1 Release Page](https://github.com/encipherdev/enciphered-kernel-4.14/releases/tag/v1.1) for native management of ReSukiSU root permissions and SuSFS modules.

---

## Source & Credits

- **XDA Thread:** [XDA Developers Forum](https://xdaforums.com/t/kernel-sm-x200-sm-x205-enciphered-kernel-v1-1-resukisu-v4-1-0-susfs-v2-1-0-wireguard-bbr-nethunter.4807120/)
- **Kernel Source:** [encipherdev/enciphered-kernel-4.14](https://github.com/encipherdev/enciphered-kernel-4.14)
- **Maintainer:** [encipherdev](https://github.com/encipherdev)

### Special Thanks & Acknowledgements
- **[DevCat3](https://github.com/DevCat3)** - Huge thanks for the Tab A8 base kernel tree and the initial ReSukiSU integration that made this project possible!
- **[ReSukiSU Team](https://github.com/ReSukiSU/ReSukiSU)** - For the exceptional ReSukiSU root driver
- **[simonpunk](https://gitlab.com/simonpunk/susfs4ksu)** - SuSFS kernel-level root hiding
- **[osm0sis](https://github.com/osm0sis/AnyKernel3)** - AnyKernel3 flasher
- **Samsung OSRC** - Stock kernel source code
