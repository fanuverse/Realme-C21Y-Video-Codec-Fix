# Realme C21Y Video Codec, Color and Touch WakeFix

[![Device](https://img.shields.io/badge/Device-Realme%20C21Y%20(RMX3261%2FRMX3263)-blue.svg)](#)
[![SoC](https://img.shields.io/badge/SoC-Unisoc%20T610%20%2F%20UMS512-orange.svg)](#)
[![Android](https://img.shields.io/badge/Android%20GSI-13%20%7C%2014%20%7C%2015+-green.svg)](#)
[![License](https://img.shields.io/badge/License-GPL%20v3-brightgreen.svg)](#)

A comprehensive Magisk / KernelSU / APatch module for the **Realme C21Y** (`RMX3261` / `RMX3263`, Unisoc T610 / UMS512) running Android 13, 14, and 15 Generic System Images (GSIs).

This module permanently fixes:
1. **Video playback color tint** (purple/cyan/green distortion in web browsers, YouTube, and gallery).
2. **Touchscreen wake unresponsiveness** (~2-second touch freeze after waking display).
3. **SurfaceFlinger color management mismatches** across Android 14/15 UI layers.

---

## The Problems Solved

### 1. Video Playback Color Inversion / Tint (YouTube & Browsers)
When playing video content inside Chrome, Jelly, Brave, or YouTube, video frames appear with a strong purple, pink, or cyan tint, inverting facial tones and color gamuts.


### 2. Touchscreen Wake Freeze (~2-Second Delay After Screen On)
Pressing the power button wakes the display immediately, but the touchscreen completely ignores finger taps and swipes for 2–3 seconds.

### 3. SurfaceFlinger Color Space Calibration
- Injects vendor properties into `system.prop` to bypass wide-color gamut gamut conversion on non-wide-gamut displays:
  ```properties
  ro.surface_flinger.use_color_management=false
  persist.sys.sf.native_mode=1
  persist.sys.sf.color_mode=0
  debug.sf.color_space=0
  ```

---

## Installation

1. Download `Realme-C21Y-Video-Codec-Fix.zip` from the [Latest Releases](../../releases/latest).
2. Open the **Magisk App** (or KernelSU / APatch Manager).
3. Go to the **Modules** tab -> **Install from storage**.
4. Select `Realme-C21Y-Video-Codec-Fix.zip`.
5. Reboot your device after installation completes.

---

## Verification

1. **Test Video Playback**:
   - Open Chrome, Jelly, or the YouTube app.
   - Play any 720p or 1080p video.
   - Colors render naturally without green, cyan, or purple tinting.
2. **Test Touch Wake Latency**:
   - Turn off the screen.
   - Press the power button and immediately swipe or tap.
   - The screen unlocks and responds instantly without hesitation.
