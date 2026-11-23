# Project 30+ — Interview Sprint Dashboard (v4)

This release replaces the beginner-first preparation sequence with an experienced-engineer, 8-week interview sprint targeting both SDE-2 and Senior Software Engineer roles, with full coverage.

## What changed
- Weeks 1–7 schedule all 35 original InterviewKit topic lessons (five topic-days per week). Week 8 is dedicated to mock interviews, weak-area remediation and company-specific preparation.
- Three daily study blocks remain: 12:00–1:00 PM, 3:30–4:30 PM and 5:30–6:30 PM.
- Each day emphasizes advanced explanation, implementation/SQL/design practice, and exact mapped question prompts from the source kit.
- The dashboard includes all 37 original chapter Markdown files and their original Q&A wording.
- The 53 source-index questions that were not mapped to a topic are retained in a separate explorer section.
- System-design HLD/LLD and frontend/full-stack exercises are labelled as additional supplements; they are not represented as InterviewKit source material.
- Existing local progress, notes, job tracker and Firebase Google sign-in / Firestore cloud-sync code are retained.

## Source inventory and fidelity
The uploaded archive's `work/topics/` contains 35 topic-wise lessons; `work/md/` contains 37 source chapters; `work/index/ALL.txt` contains 1,520 index items. The dashboard retains the original topic-question mappings and adds the 53 items listed by the source status file as not linked to a topic. Original chapter markdown and topic markdown are embedded from the supplied ZIP.

The source archive's status file reports 1,456 completed question explanations and notes two duplicate source questions. These counts describe the source archive's explanation work, not a count of unique mapped question IDs.

## Run locally
Open `index.html` in a modern browser. For Google sign-in and Firestore sync, host on HTTPS (for example GitHub Pages) and complete the Firebase setup below.

## Firebase setup
1. Create a Firebase project and register a Web app.
2. Enable Authentication → Sign-in method → Google.
3. Create a Cloud Firestore database.
4. Add your GitHub Pages hostname (for example `saumyamakker.github.io`) under Authentication → Settings → Authorized domains.
5. Publish `firestore.rules` in Firestore Rules. These rules restrict each signed-in user to their own `users/{uid}/apps/{appId}` document.
6. Open dashboard Settings, enter the Firebase Web app config and sign in with Google.
7. Sign in with the same Google account on each device.

Firebase web config is client-side configuration, not a service-account secret. Do not put service-account keys or private credentials in the HTML. Keep the Firestore rules enabled.

## GitHub Pages
Upload `index.html`, `README.md` and `firestore.rules` to the repository root. In Settings → Pages, choose Deploy from a branch, `main`, `/(root)`, then Save.

## Progress safety
Progress is local-first. Export a JSON backup from Settings before connecting a cloud document for the first time. The dashboard keeps the existing storage schema and cloud-sync logic; cloud authentication/synchronization still requires your own Firebase project configuration and has not been verified against your Firebase project.
