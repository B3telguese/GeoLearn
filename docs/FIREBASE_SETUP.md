# Firebase setup

This public copy intentionally requires a Firebase project configured by the person building it. The original client configuration is not distributed. It is a client configuration file, not a service-account private key; excluding it keeps the showcase independent of the original group's backend.

## Connect your own project

1. Create or select a Firebase project you control.
2. Register an Android app using package name `com.example.geolearn`.
3. Download its `google-services.json` and place it at `app/google-services.json`.
4. Enable the Email/Password Authentication provider. The app accepts a username, looks up its associated email in Firestore, and then uses Firebase Authentication.
5. Create a Cloud Firestore database and design rules for the app's access patterns. Do not solve permission errors by leaving the entire database publicly writable.
6. Populate the remote content needed by the app. Sync Gradle and test the app only when ready.

## Collections referenced by the source

| Collection | Purpose |
| --- | --- |
| `users` | Profile information and username lookup |
| `users/{uid}/bookmarks` | Saved flashcards |
| `flashcards` | Country learning content |
| `questions` | Trivia questions |
| `flags` | Flag questions |
| `Scores` | Game results; capitalization matters |
| `feedback` | User feedback |

Consult the Java models and activity reads/writes for exact field requirements. These collection names alone are not a complete database schema. `api/Country.java` models nested country fields used by flashcards.

## Existing limitations to review

- The bundled `Trivia Questions.json` and `Flag Questions.json` are read by first-run upload routines in the quiz activities. These routines can write to the selected Firebase project; avoid pointing an unreviewed build at a production backend.
- No complete flashcard dataset export, Firestore security rules, or index definitions are supplied.
- Login looks up a username before authentication, which requires a deliberate rules/data-design decision. Review that design instead of making all user profiles publicly readable.
- A successful build does not establish that registration, remote content, scores, or feedback work. Those flows depend on the configured backend and permissions.
- No backend resources were created or changed during this repository preparation.

## References

- [Add Firebase to an Android project](https://firebase.google.com/docs/android/setup)
- [Firebase email/password authentication](https://firebase.google.com/docs/auth/android/password-auth)
- [Firestore security rules](https://firebase.google.com/docs/firestore/security/get-started)
- [Android Gradle Plugin 8.13 documentation](https://developer.android.com/build/releases/agp-8-13-0-release-notes)
