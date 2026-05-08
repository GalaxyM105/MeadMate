# Mead Mate

Android app for mead makers. HTML5/jQuery Mobile UI rendered in a WebView with SQLite storage. Single-module Gradle project (`:app`).

## Cursor Cloud specific instructions

### Prerequisites

- **JDK 17+** (JDK 21 works) — pre-installed in the VM.
- **Android SDK** with platform 35 and build-tools 35.0.0 — installed at `/opt/android-sdk`. The update script handles this automatically.
- `ANDROID_HOME=/opt/android-sdk` is set in `~/.bashrc`.

### Key commands

| Task | Command |
|---|---|
| Build debug APK | `./gradlew assembleDebug` |
| Lint | `./gradlew lint` |
| Unit tests | `./gradlew test` |
| Instrumented tests | `./gradlew connectedAndroidTest` (requires emulator/device — not available in Cloud VM) |
| Clean | `./gradlew clean` |

### Notes

- There are **no local unit tests** (`src/test/`). The only automated tests are instrumented tests in `app/src/androidTest/` (`AbvCalculatorTests.java`) which require an Android emulator or device — these cannot run in the Cloud VM.
- The project compiles with Java source/target 1.8 on JDK 21, which produces deprecation warnings. These are expected and harmless.
- No external services, databases, or Docker containers are needed. The app is fully self-contained.
- The Gradle wrapper (`./gradlew`) is checked in; do not install Gradle globally.
