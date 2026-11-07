# Karachi Public Transport Companion (KPTC) – Mobile App

A Flutter mobile app that helps commuters in Karachi find public transport routes. It is built to work on Android and iOS from a single codebase, without needing a server to stay online.

> Course project: BSCS 506 – Software Project Management, Department of Computer Science, University of Karachi.

---

## Table of Contents

1. [Requirements](#1-requirements)
2. [Install the tools (one-time setup)](#2-install-the-tools-one-time-setup)
3. [Clone the project](#3-clone-the-project)
4. [Run the app](#4-run-the-app)
5. [Build an APK](#5-build-an-apk)
6. [Project structure](#6-project-structure)
7. [Troubleshooting](#7-troubleshooting)
8. [Team](#8-team)

---

## 1. Requirements

| Tool | Needed for |
|------|-----------|
| Git | Cloning the repository |
| Flutter SDK (stable channel) | Building and running the app |
| Android Studio (includes the Android SDK) | Android builds and emulator |
| VS Code (optional) | Code editor (install the *Flutter* and *Dart* extensions) |

**Operating system:** Windows 10/11, macOS or Linux. Building for **iOS requires a Mac with Xcode**; on Windows and Linux you can build for Android only.

**Disk space:** at least 10 GB free (Flutter + Android SDK + emulator images are large).

---

## 2. Install the tools (one-time setup)

If you already have Flutter and the Android SDK working (`flutter doctor` shows no errors), skip to [step 3](#3-clone-the-project).

### 2.1 Install Git
Download from https://git-scm.com/downloads and install with the default options.
Check it works:
```bash
git --version
```

### 2.2 Install Flutter
1. Follow the official guide for your operating system: https://docs.flutter.dev/get-started/install
2. Download the Flutter SDK and extract it to a simple path, for example `C:\src\flutter` (avoid `Program Files` and paths with spaces).
3. Add `flutter\bin` to your **PATH** environment variable.
4. Open a **new** terminal and check:
```bash
flutter --version
```

### 2.3 Install Android Studio and the Android SDK
1. Download Android Studio from https://developer.android.com/studio and install it.
2. Open Android Studio and finish the setup wizard (it installs the Android SDK).
3. Go to **More Actions → SDK Manager** (or **Settings → Languages & Frameworks → Android SDK**):
   - On the **SDK Platforms** tab, tick the latest stable Android version.
   - On the **SDK Tools** tab, tick:
     - Android SDK Build-Tools
     - Android SDK Command-line Tools (latest)
     - Android SDK Platform-Tools
     - Android Emulator
4. Click **Apply** and wait for the downloads.

### 2.4 Accept the Android licenses
```bash
flutter doctor --android-licenses
```
Type `y` to accept each license.

### 2.5 Verify everything
```bash
flutter doctor
```
You want green checkmarks for **Flutter**, **Android toolchain** and **Connected device** (or an emulator). A missing Visual Studio / Xcode / Chrome item can be ignored if you only build for Android.

---

## 3. Clone the project

```bash
git clone https://github.com/<your-username>/KPTS-WebView.git
cd KPTS-WebView
```

> Replace `<your-username>` with the account that owns the repository.

If the Flutter project sits in a subfolder (for example `mobile app`), go into it. Put the folder name in quotes if it contains a space:

```bash
cd "mobile app"
```

You should now see `pubspec.yaml` in the current folder. Check with:

```bash
dir        # Windows
ls         # macOS / Linux
```

---

## 4. Run the app

### 4.1 Download the dependencies
```bash
flutter pub get
```

### 4.2 Choose a device

**Option A: Android emulator**
1. In Android Studio, open **Device Manager** and click **Create Device**.
2. Pick a phone (for example Pixel 7), choose a system image, and finish.
3. Press the ▶ button to start the emulator.

**Option B: Real Android phone (recommended, faster)**
1. On the phone, open **Settings → About phone** and tap **Build number** 7 times to enable Developer options.
2. Go to **Settings → Developer options** and turn on **USB debugging**.
3. Connect the phone to the PC with a USB cable and tap **Allow** on the "Allow USB debugging?" prompt.

Check that Flutter can see your device:
```bash
flutter devices
```

### 4.3 Run
```bash
flutter run
```
If several devices are connected, pick one with `flutter run -d <device-id>`.

While the app is running in the terminal, press `r` for hot reload, `R` for hot restart and `q` to quit.

---

## 5. Build an APK

To get an installable file you can share or install directly on a phone:

```bash
flutter build apk --release
```

The file is created at:
```
build/app/outputs/flutter-apk/app-release.apk
```

Copy it to an Android phone and open it to install (you may need to allow "Install from unknown sources").

> **Publishing on Google Play** requires an app bundle (`flutter build appbundle`) signed with your own keystore.
> **Never commit your keystore (`.jks`) or `key.properties` file to GitHub.**

---

## 6. Project structure

```
.
├── lib/                 # App source code (Dart)
├── android/             # Android-specific project files
├── ios/                 # iOS-specific project files
├── test/                # Unit and widget tests
├── pubspec.yaml         # Dependencies and assets
├── pubspec.lock         # Locked dependency versions
└── analysis_options.yaml
```

Run the tests (when available):
```bash
flutter test
```

---

## 7. Troubleshooting

| Problem | Fix |
|---------|-----|
| `flutter` is not recognized | `flutter\bin` is not in PATH. Add it and open a new terminal. |
| `Android license status unknown` | Run `flutter doctor --android-licenses` and accept all. |
| `cmdline-tools component is missing` | In Android Studio SDK Manager → SDK Tools, install **Android SDK Command-line Tools**. |
| Phone not listed in `flutter devices` | Enable USB debugging, use a data cable (not charge-only), accept the prompt on the phone, then run `adb kill-server` and reconnect. |
| Gradle or build errors after cloning | Run `flutter clean`, then `flutter pub get`, then `flutter run`. |
| `Could not find MainActivity` | Check that `MainActivity.kt` is at `android/app/src/main/kotlin/<package-path>/`. |
| `local.properties` missing | It is generated automatically. Running `flutter pub get` or `flutter run` creates it. |
| Slow first build | Normal. The first Gradle build downloads many files and can take several minutes. |

Still stuck? Run `flutter doctor -v` and read the first red or yellow message. It usually says exactly what is missing.

---

## 8. Team

| Name        |
|-------------|
| Nida Hafeez |
| Ayesha Abid |
| Ayesha Khan | 
| Mahnoor Khan |
| Romaisa Ajaz |

**Supervisor:** _Dr.Humera Bashir_
