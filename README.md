# Strength & Conditioning – WoW Forever-inspired PWA

A standalone, installable iPhone web app for James' three-day gym routine.

## Included
- Character/profession screen with Apprentice → Journeyman → Expert → Artisan ranks
- Upper Push, Upper Pull and Lower Body quest checklists
- Weekly quest log and completion bonus
- Exercise skillbook with weight/reps/sets records and simple personal-best tracking
- Achievement journal and reward goal
- Local device persistence via localStorage
- JSON export/import backup
- Service worker cache for offline use after the first successful load

## Important data notes
- Data stays in the browser storage on the device. It is not automatically synced between devices.
- Export a JSON backup regularly. Importing a backup replaces the data currently on the device.
- The app awards 10 XP for a completed workout, an additional 5 XP when the third different workout is completed in the same week, and 2 XP for a new logged exercise record. It awards no XP for a missed workout.
- A record is a simple load × reps-per-set comparison. It is not a scientifically complete measure for carries, timed holds, assisted movements, or unilateral work.
- The weekly quest view uses the device's local calendar week.
- The original Day 1 James variations are used: cable tricep pushdown and plank. Waiter's carry is configured as 3 rounds of 20–30 metres per side as a practical starting prescription; adjust to suit.

## Publish it so it can be installed
A PWA needs to be served from HTTPS (or localhost for development). Opening `index.html` directly from the Files app will not enable installation/offline service-worker support.

### Simple GitHub Pages route
1. Create or sign in to a GitHub account.
2. Create a new public repository, e.g. `strength-guild`.
3. Upload all files in this folder to the repository root (not the ZIP itself).
4. In the repository, open **Settings → Pages**.
5. Under **Build and deployment**, choose **Deploy from a branch**, select `main` and `/ (root)`, then Save.
6. Wait for GitHub Pages to publish the site. It will provide an HTTPS address.
7. Open that HTTPS address in Safari on your iPhone.

### Add to iPhone Home Screen
1. Open the published app URL in **Safari** (not an in-app browser).
2. Tap the Share icon.
3. Scroll and tap **Add to Home Screen**.
4. If shown, enable **Open as Web App**, then tap **Add**.
5. Launch the new Strength Guild icon from your Home Screen.

### Offline use
Open the app once while online so the service worker can cache its files. Then try it in Airplane Mode. Previously loaded app files and local data should remain available. iOS may evict website data under storage pressure, so backups are important.

## Updating the app
When replacing app files, update the cache name in `sw.js` (e.g. `strength-guild-v2`) so installed clients fetch the new version. Keep the same localStorage key in `app.js` to preserve user progress.

## Files
- `index.html` – app shell and styling
- `app.js` – workouts, state, XP, quest logic, backups
- `manifest.webmanifest` – install metadata
- `sw.js` – offline cache
- `icon.svg`, `icon-192.png`, `icon-512.png` – app icons
