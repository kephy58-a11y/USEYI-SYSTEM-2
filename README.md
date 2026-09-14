# USEYI Monitor

USEYI Monitor is an Android-first Flutter attendance app for Upshift Youth Empowerment Initiative.

## What is included

- QR-code student attendance scanning.
- Student registration and QR display.
- Daily attendance sheet.
- Manual present/absent correction.
- CSV student import.
- CSV attendance export through the Android share sheet.
- Local offline storage using Hive CE.
- Staff PIN lock.
- Codemagic Android APK workflow.

## Important

The GitHub repository does **not** need a committed `android/` directory. Codemagic creates it using the Flutter SDK during the build. The repository root must contain `pubspec.yaml`, `lib/`, `assets/`, and `codemagic.yaml`.

## GitHub + Codemagic Android build

1. Create a new GitHub repository named `useyi-monitor` (or another name).
2. Upload the **contents of this project folder**, not the outer ZIP folder. `pubspec.yaml` and `codemagic.yaml` must be at the repository root.
3. Commit to the `main` branch.
4. In Codemagic, add the GitHub repository and select Flutter as the project type.
5. Select the `android-apk` workflow from `codemagic.yaml`.
6. Start the build.
7. Download `app-release.apk` from the successful build's Artifacts section.
8. Install that APK on an Android phone.

Codemagic automatically creates the Android project, adds the camera permission, installs the Flutter packages, runs `flutter analyze`, and builds the release APK.

## First app test

The first time the app opens, the default staff PIN is `1234`.

To test scanning:

1. Open **Students**.
2. Add a student, for example ID `3333`.
3. Tap the QR icon next to that student.
4. Display the QR code on another phone or screen.
5. Open **SCAN STUDENT** on the Android phone running USEYI Monitor.
6. Allow camera permission.
7. Scan the QR code.
8. The student should be marked PRESENT.

## Release signing

The first APK workflow is intentionally simple so you can get a working APK before setting up a production keystore. For Google Play or a long-term release process, create/upload an Android keystore in Codemagic and configure `android_signing` in the workflow. Keep the keystore private and keep a backup of it.
