# PovaIsland — Codemagic build package

This archive is arranged with the Android project at the repository root:
`app/`, `settings.gradle.kts`, `build.gradle.kts`, and `codemagic.yaml`.

## GitHub upload

Upload the **contents inside this PovaIsland folder** to the root of the GitHub repository (not an extra nested PovaIsland folder). After upload, the repository root must show:

- `app/`
- `codemagic.yaml`
- `settings.gradle.kts`
- `build.gradle.kts`
- `gradle.properties`

## Codemagic

The included workflow targets `mac_mini_m2`, uses Java 17, downloads Gradle 8.9 (compatible with Android Gradle Plugin 8.7.3), installs Android SDK Platform 36 and Build Tools 36.0.0, then runs `assembleDebug`.

This workflow intentionally does not depend on `gradlew` or a wrapper JAR. It invokes the downloaded Gradle distribution directly.

The availability of `mac_mini_m2` depends on the account's current Codemagic plan and quota. If Codemagic still reports that the machine is unavailable, do not switch randomly between machine types; check the account's plan/build minutes or use another supported runner.

## Expected APK

`app/build/outputs/apk/debug/app-debug.apk`

## Verification status

The ZIP layout and required Gradle project files were checked locally. This environment did not run an Android SDK/Gradle build, so compilation and device behavior remain unverified.
