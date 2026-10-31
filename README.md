# Enciphered Kernel v1.0 ⚡🛡️
### Advanced Custom Kernel for Samsung Galaxy Tab A8 10.5 (2021)
**Unisoc Tiger T618 (`ums512_25c10` / `qogirl6`)**
**Supported Models:** `SM-X200` (Wi-Fi), `SM-X205` (LTE), `SM-X207` (LTE)

---

## 🌟 Overview
**Enciphered Kernel** is a high-performance, security-focused, and modern custom kernel built specifically for the Samsung Galaxy Tab A8 10.5 (2021). It brings together bleeding-edge root management (**KernelSU-Next**), hardware acceleration fixes for Mali Bifrost GPU, cybersecurity & penetration testing capabilities (**Kali NetHunter**), native **WireGuard VPN**, and low-latency touch response.

---

## 🚀 Key Features

### 1. 👑 Next-Gen Root: KernelSU-Next (v3.4.x / Build 33004)
- Fully embedded in-kernel **KernelSU-Next** (Non-GKI compatible).
- Eliminates the legacy *"KernelSU only supports GKI"* issue entirely.
- Bundled with the latest `ksud` (aarch64) daemon in AnyKernel3 installer.
- Supports modern KernelSU-Next Manager features:
  - App profiles & granular SU permissions.
  - Systemless module support (Magic Mount & OverlayFS).
  - WebUI module manager.

### 2. 🛡️ Penetration Testing & NetHunter Capabilities
- **USB HID Gadget Emulation:** Emulate keyboards and mice over USB OTG (`CONFIG_USB_CONFIGFS_F_HID=y`) for DuckHunter / BadUSB payloads.
- **External Wi-Fi Drivers (Built-in with Monitor Mode & Packet Injection):**
  - **Atheros:** AR9271 (`ath9k_htc`) - *The gold standard for NetHunter*.
  - **Realtek:** RTL8187 / RTL8187B (`rtl8187`), RTL8192CU / RTL8188CU (`rtl8192cu`), `rtl8xxxu`.
  - **Ralink / MediaTek:** RT2770, RT2870, RT3070, RT3071, RT3072, RT3370, RT5370 (`rt2800usb`).
- **DriveDroid Support:** Full CD-ROM and USB Mass Storage emulation (`CONFIG_USB_CONFIGFS_MASS_STORAGE=y` with CD-ROM mode).
- **Native WireGuard VPN:** In-kernel WireGuard crypto accelerator (`CONFIG_WIREGUARD=y`) for blazing-fast encrypted tunnels.

### 3. 🎨 Graphics, DRM & Display Fixes (Zero Glitches)
- **Mali-G52 GPU Fix:** Restored missing kernel list validation exports (`CONFIG_DEBUG_LIST=y`), allowing Samsung's out-of-tree `mali_gondul.ko` driver to load with full OpenGL ES 3.2 hardware acceleration.
- **SurfaceFlinger Stability:** Attached DSI Connector `"EDID INFO"` blob property and enabled DRM CRTC Color Management (`CTM`). Completely eliminates the fatal SIGSEGV in `hwcomposer.ums512.so`.
- Full touchscreen responsiveness with `sec_touchscreen` incell panel driver.

### 4. ⚡ Extreme Performance & Low Latency
- **500μs Schedutil Ramp-Up:** Tuned cpufreq governor to ramp up to peak CPU frequencies within 500 microseconds of touch input, with 20ms hold down. Provides a buttery-smooth UI experience.
- **TCP BBR + FQ-Codel:** Replaced legacy BIC with Google's BBR congestion control and Fair Queueing for higher Wi-Fi throughput and lower bufferbloat.
- **ZRAM Compression:** Integrated fast LZ4 and ZSTD compression algorithms.
- **Bloatware Stripped:** Removed Samsung's heavy `SEC_DEBUG_SCHED_LOG`, per-CPU scheduling monitors, and kernel tracing overhead.

### 5. 📱 Android 14 / 15 / 16 / 17 GSI Ready
- Full **BinderFS** (`/dev/binderfs`) enabled for modern Android treble requirements.
- Modern **eBPF** subsystem: `CONFIG_BPF_SYSCALL=y`, `CONFIG_NET_ACT_BPF=y`, `CONFIG_CGROUP_NET_PRIO=y`, `CONFIG_CGROUP_BPF=y`.
- Boots Stock Samsung One UI, LineageOS, TrebleDroid, and AOSP GSIs flawlessly.

---

## 📦 Package Contents

| File | Description |
|---|---|
| `EncipheredKernel-X20X-v1.0.zip` | Universal AnyKernel3 flashable zip (TWRP / OrangeFox) |
| `boot.img` | Standalone boot partition image (Fastboot / TWRP Image Flash) |
| `KernelSU_Next_v3.4.2-release.apk` | Official matching KernelSU-Next Manager app |

---

## 📲 Installation Guide

### Method A: Flashing via TWRP / OrangeFox (Recommended)
1. Copy `EncipheredKernel-X20X-v1.0.zip` to your tablet's Internal Storage or MicroSD card.
2. Boot into TWRP Recovery.
3. Tap **Install**, select `EncipheredKernel-X20X-v1.0.zip`, and swipe to confirm flash.
4. (Optional) Wipe Dalvik/ART Cache.
5. Reboot System.
6. Install `KernelSU_Next_v3.4.2-release.apk` in Android to manage root access.

### Method B: Flashing via Fastboot / Boot Image
1. Boot tablet into Fastboot or TWRP.
2. If using Fastboot:
   ```bash
   fastboot flash boot boot.img
   fastboot reboot
   ```
3. If using TWRP:
   - Tap **Install** -> **Install Image** -> select `boot.img` -> choose **Boot** partition -> swipe to flash.
4. Reboot and install `KernelSU_Next_v3.4.2-release.apk`.

---

## 🛠️ Build Specifications
- **Kernel Version:** `Linux 4.14.199-Enciphered-v1.0+`
- **Toolchain:** Google Clang 11.0.1 (`r383902`) + Android GCC 4.9 (aarch64)
- **Target Architecture:** `arm64` (ARMv8.2-A / Cortex-A75 + Cortex-A55)
- **Build Machine:** Fedora Linux x86_64

---

## 📜 License
Distributed under the GNU General Public License v2 (GPLv2).
Developed for the Android & XDA modding community.
