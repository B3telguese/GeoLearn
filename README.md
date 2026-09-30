<div align="center">
  <img src="app/src/main/res/drawable/app_logo.png" alt="GeoLearn app logo" width="140">
  <h1>GeoLearn</h1>
  <p><strong>Explore geography. Test your knowledge. Track your progress.</strong></p>
  <p>A native Android learning app built with Java, XML, and Firebase.</p>
  <p>
    <img src="https://img.shields.io/badge/Platform-Android-3DDC84?logo=android&logoColor=white" alt="Platform: Android">
    <img src="https://img.shields.io/badge/Language-Java-ED8B00" alt="Language: Java">
    <img src="https://img.shields.io/badge/Backend-Firebase-FFCA28?logo=firebase&logoColor=black" alt="Backend: Firebase">
    <img src="https://img.shields.io/badge/Project-Academic-2563EB" alt="Academic project">
  </p>
</div>

---

## Overview

GeoLearn is an educational Android project that brings together geography flashcards, trivia quizzes, and flag-guessing activities. Users can explore country information, save flashcards, and review their learning progress through dedicated results and analysis screens.

This repository preserves an academic group project for portfolio review and further development. You can browse the source and interface layouts without installing Android Studio. Running the app requires an Android build environment and a configured Firebase backend.

## Features

| Area | Included functionality |
| --- | --- |
| Accounts | Registration, username-based login, profile editing, and password changes |
| Guest access | A separate guest menu and exploration flow |
| Flashcards | Country information, category selection, and bookmarks |
| Geography trivia | Questions, answer selection, and quiz results |
| Flag guessing | Flag questions and a dedicated results screen |
| Progress | Score history, progress dashboard, and game analysis |
| Feedback | Submit, view, and edit feedback |

Feature descriptions are based on the included source code. The public packaging pass did not build or execute the app, and backend availability has not been verified.

## Explore the source

| Start here | What it contains |
| --- | --- |
| [Home screens](app/src/main/java/com/example/geolearn/home) | Splash screen, signed-in menu, guest menu, and about page |
| [Games and flashcards](app/src/main/java/com/example/geolearn/game) | Quizzes, flag guessing, flashcards, results, and analysis |
| [Profiles and bookmarks](app/src/main/java/com/example/geolearn/profile) | Settings, user profile, saved content, and progress |
| [Authentication](app/src/main/java/com/example/geolearn/auth) | Registration, login, and session-related code |
| [Feedback](app/src/main/java/com/example/geolearn/feedback) | Feedback screens and adapters |
| [XML layouts](app/src/main/res/layout) | The app's screen layouts |
| [Question assets](app/src/main/assets) | Bundled trivia and flag-question JSON files |

## Technology

| Layer | Technology |
| --- | --- |
| Application | Java, Android SDK, AndroidX |
| Interface | XML layouts and Material Components |
| Authentication | Firebase Authentication |
| Cloud storage | Cloud Firestore |
| Local storage code | Room / SQLite |
| Networking and images | Retrofit, Gson, and Glide |
| Charts | MPAndroidChart |
| Build | Gradle Kotlin DSL |

Firebase Analytics and Realtime Database dependencies are also declared. A declared dependency does not imply every feature uses it; the inspected account, quiz, bookmark, and feedback flows use Firebase Authentication and/or Firestore.

## Build configuration

| Setting | Included value |
| --- | --- |
| Application ID | `com.example.geolearn` |
| Minimum SDK | 24 |
| Compile / target SDK | 36 / 36 |
| Android Gradle Plugin | 8.13.2 |
| Gradle wrapper | 8.13 |
| Java source / target compatibility | 11 |
| Firebase BoM | 34.8.0 |

Use a compatible Android Studio installation and Gradle runtime JDK. JDK 17 is the documented baseline for AGP 8.13; Java source compatibility 11 does not mean Gradle should run on JDK 11.

## Getting started

1. Clone or download this repository.
2. Open the repository root in Android Studio (the folder containing `settings.gradle.kts`).
3. Install Android SDK Platform 36 and configure a compatible Gradle JDK.
4. Follow the [Firebase setup guide](docs/FIREBASE_SETUP.md). The original `app/google-services.json` is deliberately excluded from this public copy; supply your own before building.
5. Sync Gradle and allow the declared dependencies to download.
6. Select an emulator or Android device with API 24 or newer, then run the `app` configuration.

Optional Windows command-line build, once the Android SDK, Java, and Firebase configuration are available:

```cmd
gradlew.bat assembleDebug
```

The expected debug APK output path is `app/build/outputs/apk/debug/app-debug.apk`. No APK is included in this repository, and this command was not executed during repository preparation.

## Firebase and data

The repository contains application code and question assets, not a complete cloud database backup. Flashcards and other remote data must exist in the configured Firestore project. Firebase rules, indexes, and Authentication provider configuration are not included.

The quiz activities contain first-run logic that attempts to write bundled question data to Firestore. Review this behavior before connecting to an existing backend. See the [setup guide](docs/FIREBASE_SETUP.md) for collection names and limitations.

## Preview and project status

The logo above is an original project asset. Runtime screenshots, a demo video, and a downloadable APK are not included. The source is available for review; GitHub Pages cannot execute this Android application.

Future presentation improvements could include genuine screenshots of the main menu, flashcards, quiz, and progress dashboard, captured from an existing device or recording.

## Credits and reuse

Developed as an academic group project. Existing in-app credits and project assets are preserved; see the [About layout](app/src/main/res/layout/activity_about.xml).

The app uses third-party libraries and visual assets whose respective licenses and ownership still apply. No new license has been assigned to the group's source code in this preparation pass. Public visibility alone does not grant a general license to reuse or redistribute the project.

## Repository preparation

- Added this README and a Firebase setup guide.
- Excluded IDE metadata, JVM crash/replay logs, and the original Firebase client configuration.
- Expanded `.gitignore` for local settings, build output, configuration, and signing files.
- Preserved the Java source, XML layouts, Gradle configuration, and application assets.
- Did not run Gradle, an emulator, or the app.
