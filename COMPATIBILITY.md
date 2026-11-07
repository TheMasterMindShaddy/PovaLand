# Tecno Compatibility Report — Pova 7 Pro 5G

| Item | Status | Notes |
|---|---|---|
| Device detection | ✅ | Build.MANUFACTURER/BRAND check |
| HiOS version detect | ✅ | Best-effort via build fingerprint + settings probe |
| Built-in Mini Capsule active detection | ⚠️ Heuristic | No public setting key; guesses common keys, may report false |
| External integration with built-in capsule | ❌ Not possible | No documented API; we do not modify protected system apps |
| Overlay permission (SYSTEM_ALERT_WINDOW) | ✅ | Standard Android, works on HiOS 16 |
| Foreground service survival | ✅ | `specialUse` FGS + user battery exemption |
| MediaSession (Spotify/YTM/VLC) | ✅ | Standard Android API |
| NotificationListenerService | ✅ | Standard Android API |
| Camera cutout positioning | ✅ | Overlay anchored to top-center via WindowManager gravity; centered punch-hole on Pova 7 Pro aligns automatically |
| Android 16 permission changes | ✅ | POST_NOTIFICATIONS runtime request; FGS types declared |
| Two islands overlapping | Prevented | COMPANION mode suppresses overlay when capsule is detected |

**Conclusion:** MODE B (COMPANION) and MODE C (STANDALONE) are fully functional.
MODE A (NATIVE) degrades to COMPANION because Tecno exposes no supported integration surface.
