# Project 30+ Dashboard — Cloud Sync Edition Personal

## What changed
- Preserves the existing mobile-first dashboard, 35 Java kit topics, mapped interview questions, study blocks, project lab, job pipeline, roadmap, notes, checklists and JSON backup/restore.
- Adds Google sign-in through Firebase Authentication.
- Adds per-user cloud storage in Cloud Firestore. The document path is `users/{uid}/apps/project30`.
- Local progress continues to save immediately. When signed in, changes are debounced and synced to Firestore; incoming changes from another device update the dashboard.
- Firestore browser persistence is enabled where supported. Local JSON export remains available as an independent backup.

## Important: Firebase setup is required before cloud sync works
The dashboard is still a static site and can be hosted on GitHub Pages. Cloud sync requires your own Firebase project. No Firebase project credentials have been supplied yet, so the integration is included but is not connected or live until you complete these steps.

1. In Firebase Console, create a project.
2. Register a **Web app** and copy its Firebase config.
3. In **Authentication → Sign-in method**, enable **Google**.
4. In **Authentication → Settings → Authorized domains**, add your GitHub Pages hostname (for example, `YOUR_GITHUB_USERNAME.github.io`). Also add `localhost` if testing locally.
5. Create a **Cloud Firestore** database.
6. Open Firestore Rules and publish the contents of `firestore.rules` from this ZIP.
7. Open the dashboard → Backup & Settings → Cloud sync. Paste `apiKey`, `authDomain`, `projectId`, and `appId` from the Firebase Web app config. Sender ID and storage bucket are optional for this dashboard.
8. Select **Save configuration**, then **Continue with Google**.
9. Open the same GitHub Pages URL on another device, enter the same Firebase Web app config, and sign in with the same Google account.

## Firestore security rules
The supplied `firestore.rules` restrict each signed-in user to their own document. Do not use permissive test rules such as `allow read, write: if true`.

## Configuration and privacy
- Firebase web config values are public client configuration; they are not a substitute for security rules. Do not put service-account private keys or Admin SDK credentials in this page.
- Each user's progress is stored under their Firebase Authentication UID. Other signed-in users cannot read that user's document under the supplied rules.
- The dashboard still keeps a local copy in browser storage and offers JSON export/import.
- GitHub Pages hosts the HTML; Firebase provides authentication and database services.
- The dashboard does not require or use a custom server.

## Deploy to GitHub Pages
Upload `index.html` to the repository root (and optionally `README.md` and `firestore.rules`). Enable Pages from `main` / `/(root)`. Add the resulting `github.io` hostname to Firebase Authentication's authorised domains.

## Notes
- Cloud sync requires an internet connection. Local progress remains usable offline and syncs when online.
- On the first Google sign-in, if no cloud document exists, the current browser's local progress is uploaded. If a cloud document already exists, that cloud copy becomes the active copy on that device. Export a JSON backup before first connecting if you have important local-only progress.
