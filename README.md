# Model Launch Dashboard

A self-contained HTML dashboard for tracking model launch tasks, with Firebase auth/sync and Excel import support.

## Setup

This dashboard needs a Firebase project to handle login and data storage. Your real credentials are kept out of GitHub via `config.js`, which is gitignored.

1. Copy the template:
   ```bash
   cp config.example.js config.js
   ```
2. Open `config.js` and fill in your Firebase project's values (Firebase Console → Project Settings → General → Your apps → SDK setup and configuration).
3. Open `DASHBOARD_GITHUB.html` in a browser, or serve the folder with any static server.

`config.js` will never be committed — `.gitignore` already excludes it.

## Important: lock down Firestore before going further

The Firebase web API key in `config.js` is not a secret by Google's design — it identifies your project but doesn't grant access on its own. Real protection comes from your **Firestore Security Rules** and **Authentication settings**, not from hiding the key. Before relying on this dashboard with real data:

- Set Firestore rules so users can only read/write their own data (not open read/write).
- In Firebase Console → Authentication → Settings, restrict **Authorized domains** to where you'll actually host this.
- Decide whether sign-up should be open or invite-only.

## Files

- `DASHBOARD_GITHUB.html` — the dashboard itself
- `config.example.js` — template for your Firebase config (committed)
- `config.js` — your real Firebase config (gitignored, you create this locally)
- `.gitignore` — excludes `config.js` from version control
