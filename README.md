<div align="center">

<table width="100%">
<tr>
<td align="left" width="33%">
<img src="https://github.com/ThinkDifferentInc/ThinkPad-AMD/blob/main/td2.png?raw=true" style="max-width:100%; height:auto;" />
</td>
<td align="center" width="34%">

# ThinkPad-AMD

**OpenCore EFI for Lenovo ThinkPad L15 Gen 1 (AMD)**

</td>
<td align="right" width="33%">
<img src="https://www.svgrepo.com/show/303321/ryzen-logo.svg" style="max-width:100%; height:auto;" />
</td>
</tr>
</table>

<img src="https://github.com/ThinkDifferentInc/ThinkPad-AMD/blob/main/TD-Tahoe2601.png?raw=true" style="max-width:100%; height:auto;" />

</div>

---

## Overview

This repository contains a custom **OpenCore EFI configuration** designed to run:

- **macOS Catalina → macOS Tahoe (26.0.1 recommended)**

On:

- **Lenovo ThinkPad L15 Gen 1 (AMD)**

---

## Tested Hardware

| Component | Specification |
|------------|---------------|
| **Model** | Lenovo ThinkPad L15 Gen 1 (AMD) |
| **CPU** | AMD Ryzen 5 PRO 4650U |
| **GPU** | AMD Radeon RX Vega 6 (Renoir) |
| **RAM** | 16GB DDR4 |
| **Storage** | 2TB KINGSTON NVMe SSD |
| **Wi‑Fi** | Intel Dual Band Wireless‑AC 7265 |

---

## Credits

> [!NOTE]
> This EFI is largely based on **fdvky1’s work**. Huge thanks for the original foundation.

Original project:
https://github.com/fdvky1/Thinkpad-L15-Hackintosh

---

# Important Notes

---

## Wi‑Fi Setup (itlwm)

> [!WARNING]
> Wi‑Fi **will NOT work in macOS Recovery** unless configured properly.

You must edit:

```
itlwm.kext/Contents/Info.plist
```

Replace:

- `YOURPASSWORDHERE`
- `YOURWIFINAMEHERE`

Alternatively:

- Use **Itlwmjector.py** (on our main page)
- Works on **Windows/Linux only**

---

## Native Wi-Fi with AirportItlwm

> [!TIP]
> Follow this guide after setting up macOS.
> <br>
> This method requires **AirportItlwm Ventura** version and **OCLP**. This works across **Ventura -> Tahoe**.
> <br>
> You will also need to put _"amfi_get_out_of_my_way"_ inside _boot-args_ to avoid a kernel panic.
> <br>
> For Ventura up to Sequoia, use the **official OCLP**. For Tahoe use **lzhoang's OCLP3 Beta.**

_TL;DR_
You can get native Wi-Fi working with a Intel card by spoofing it as a Broadcom one. Need SIP to be partially disabled.

[AirportItlwm Patching Guide](https://github.com/randomappleboi/Native-Wifi-for-Hackintoshes-with-Intel-Wireless-cards-on-macOS-sequoia)

---

## macOS Tahoe Notes

- Graphical glitches may occur on **26.1** upwards.
- Best experience: **macOS 26.0.1**

---

## USB Mapping

> [!TIP]
> For best stability, build your own USB map.

Steps:

1. Replace included UTBMap with your own
2. Open EFI in **ProperTree**
3. Run **OC Snapshot**

---

## Wi‑Fi Driver Choice

This EFI uses:

- ✅ `itlwm`
- ❌ `AirportItlwm`

**Reason:**

- Better stability
- Cross-version macOS compatibility

After installation:

- Download **HeliPort 2.0.0 beta** (for Tahoe)
- Install
- Optional: enable auto-launch at login

---

## Audio on Tahoe

> [!CAUTION]
> Apple removed **AppleHDA.kext** starting with macOS 26.0 Beta 2.

To restore audio:

- Use **MyKextInstaller**
- INSTALL A **LOWER KDK VERSION THATS NOT 26.3! Install 26.0 if available**
- Not doing so might result in a corrupted macOS install due to a kernel mismatch.
- Reinstall **AppleHDA**

---

# What Works?

Everything expected from a daily‑driver laptop:

- ✅ GPU acceleration
- ✅ HDMI output
- ✅ Audio (after AppleHDA restoration on macOS 26)
- ✅ Wi‑Fi & Bluetooth
- ✅ Sleep / Wake
- ✅ Trackpad & keyboard
- ✅ All major ports

---

# macOS Installation

<details>
<summary><strong>Click to expand installation steps</strong></summary>

1. Use `macrecovery.py` to create macOS installer
2. Place:
   - `com.apple.recovery.boot` in root of USB
   - `EFI` folder in root of USB
3. Boot from flash drive
4. Select the **yellow gear icon**

</details>

---

# UEFI / BIOS Settings

## Config Tab

### Display

- Boot Display Device → **ThinkPad LCD**
- Shared Display Priority → **HDMI**
- Boot Time Extension → **Disabled**
- Increase Framebuffer Size → **1GB recommended, 2GB for extra performance (from 512MB)**

---

## Security Tab

- Memory Protection → Execution Prevention → **On**
- Secure Boot → **Off**

---

## Startup Tab

- UEFI/Legacy Boot → **UEFI Only**

---

> [!CAUTION]
> Results may vary depending on hardware configuration.
> <br>
> This is a **PRE‑MADE EFI folder**.
> <br>
> 99% of Hackintosh communities do not support pre-built EFI users.
> <br>
> You are using this at your own risk.

---

<div align="center">

**ThinkDifferent Inc.**

</div>

