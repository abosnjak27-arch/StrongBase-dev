# StrongBase — first working version

A mobile-friendly single-page workout tracker. No build tools or paid hosting required.

## Try it locally
Open `index.html` in a browser. For full clipboard and cloud functionality, host it over HTTPS (e.g. GitHub Pages). Import a workout via the Import tab, log sets in Today, review History, and copy the Export summary into ChatGPT.

## Publish for free with GitHub Pages
1. Create a GitHub account (if needed) and a new public repository named `strongbase`.
2. Upload `index.html` to the repository root and commit.
3. Open **Settings → Pages → Build and deployment** and choose **Deploy from a branch**, branch **main**, folder **/(root)**, then save.
4. Once published, visit `https://YOUR-USERNAME.github.io/strongbase/` on your phone. In Safari, use **Share → Add to Home Screen**.

**Privacy warning:** A public GitHub Pages repository makes the app's source code public, but not your locally stored workout history. Do not put passwords or private API keys in the repository.

## Optional cloud sync with Supabase
1. Create a free Supabase project.
2. In **SQL Editor**, run the contents of `supabase.sql` once. (If re-running after policies exist, remove or rename the existing policies first.)
3. In **Project Settings / API**, copy the project URL and **publishable** (or legacy anon) key. Never use a secret/service-role key.
4. In the app's Sync tab, enter those values, your email and a new password, then **Sign up**. Confirm email if required, then **Sign in**.
5. Choose **Upload to cloud** on the first device. On a second device, sign in and choose **Download from cloud**. Changes upload automatically while signed in, but other devices do **not** refresh automatically.

**Current limitations:** This prototype uses browser localStorage and stores the login token in localStorage; use a strong unique password and a trusted device. Cloud sync is last-write-wins (not real-time or conflict-safe). Login sessions may expire and require signing in again. Back up before switching devices. Avoid simultaneous edits on multiple devices. There is no offline sync queue, automated progression, or editable logged session yet. Future versions should use a proper auth client with token refresh, conflict-aware per-session sync, and stronger security.

## Import schema
Paste a single workout or an array of workouts as JSON:
```json
{"name":"Workout A","exercises":[{"name":"Hamstring curl","sets":3,"target":"10–12 reps @ RPE 7"}]}
```

Prompt for ChatGPT: `Convert my workout into StrongBase import JSON with name and exercises (name, sets, target). Output JSON only.`

## Costs
GitHub Pages and Supabase both offer free tiers with usage limits subject to change. This lightweight personal prototype should normally fit within those tiers, but check current provider terms before deployment.
