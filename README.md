# Pova Island — Tecno Pova 7 Pro 5G Dynamic Island Enhancement

A complete, free, open Dynamic Island companion for the **Tecno Pova 7 Pro 5G**
(Android 16 / HiOS 16), compatible with Android 9+ punch-hole devices
(Tecno, Samsung, Xiaomi, others).

**Everything is free. No ads, no accounts, no analytics, no in-app purchases.**

## Operating modes

| Mode | Behavior |
|---|---|
| **NATIVE** | Attempts to use supported Tecno functionality. HiOS exposes **no public API** for its built-in Mini Capsule, so this mode degrades gracefully to COMPANION. |
| **COMPANION** | Independent overlay that auto-suppresses itself if the built-in HiOS Mini Capsule is detected active, so the two never overlap. |
| **STANDALONE** | Full island experience regardless of the built-in feature. |

## Features

- Floating pill around the punch-hole, auto-insets from status bar, portrait + landscape
- Compact / Expanded / Full states with smooth animations
- **Music**: MediaSession-based (Spotify, YouTube Music, VLC, any media app) — title, artist, album art, progress, play/pause/skip, visualizer bars
- **Battery**: live %, charging connect/disconnect animations, low/full battery alerts, temperature
- **Notifications**: NotificationListenerService — icon, title, text, actions, priority, auto-hide
- **Flashlight**: CameraManager torch toggle with strength on supported devices
- **Gestures**: tap/double-tap/long-press/swipe×4 — all user-mappable
- **Customization**: 7 themes, custom colors, width/height/radius/position/opacity, live preview
- **Secondary island** slot
- **Backup/restore**: versioned JSON, fully local

## Build

Requires Android Studio Ladybug+ with SDK 36.

```
./gradlew assembleDebug    # debug APK  -> app/build/outputs/apk/debug/app-debug.apk
./gradlew assembleRelease  # release APK -> app/build/outputs/apk/release/app-release.apk
```

## Setup guide

1. Install APK → open Pova Island.
2. Enable **Master switch**.
3. Grant requested permissions when prompted:
   - **Overlay** — draws the pill around the camera cutout.
   - **Notification access** — shows notifications on the island and enables media session detection.
   - **Battery optimization exemption** — keeps the foreground service alive under HiOS 16 background restrictions.
4. (Optional) In HiOS settings, adjust the built-in Mini Capsule if you use COMPANION mode.

## HiOS optimization notes

- The island runs as a **foreground service** — HiOS 16 rarely kills these; still exempt from battery optimization.
- All updates are **event-driven** (broadcasts, session callbacks) — zero polling, minimal battery use.
- No root, no bootloader unlock, no system-app modification.

## Privacy

- Zero network usage. No analytics SDKs. No accounts.
- Notification content never leaves the device.

## Known limitations

- **No HiOS Mini Capsule integration API exists.** Tecno/Transsion does not document any public interface for third-party apps to extend the built-in feature, so NATIVE mode degrades to COMPANION. Detection of the built-in capsule is heuristic.
- Flashlight brightness levels require hardware support (most devices are on/off only).
- Synchronized lyrics: shown when present in media metadata; no scraping of lyric services.
- Screen-recording status and navigation updates are shown when they arrive as notifications.


## Repair notes (2026-11-07)

This revision fixes the DataStore backup schema, Kotlin keyword naming, missing Tecno Build import, media-session listener component reference, initial active-session binding, battery receiver compatibility, overlay state synchronization, and same-priority activity ordering. The dashboard has a refreshed dark AMOLED visual treatment.

Some capabilities remain platform- or implementation-limited: HiOS Mini Capsule cannot be reliably detected through a public API; the companion app does not modify Tecno firmware. Timer/live-delivery integrations and executable notification reply actions are not claimed as complete in this revision. The visualizer is decorative rather than microphone/audio-capture based.

### Build

Open this folder in Android Studio with Android SDK 36 and JDK 17 installed, allow Gradle to sync, then build `:app:assembleDebug`. This archive does not include a Gradle wrapper JAR or a compiled APK.


## Repair notes (2026-11-07)

This revision fixes the DataStore backup schema, Kotlin keyword naming, missing Tecno Build import, media-session listener component reference, initial active-session binding, battery receiver compatibility, overlay state synchronization, and same-priority activity ordering. The dashboard has a refreshed dark AMOLED visual treatment.

Some capabilities remain platform- or implementation-limited: HiOS Mini Capsule cannot be reliably detected through a public API; the companion app does not modify Tecno firmware. Timer/live-delivery integrations and executable notification reply actions are not claimed as complete in this revision. The visualizer is decorative rather than microphone/audio-capture based.

### Build

Open this folder in Android Studio with Android SDK 36 and JDK 17 installed, allow Gradle to sync, then build `:app:assembleDebug`. This archive does not include a Gradle wrapper JAR or a compiled APK.
