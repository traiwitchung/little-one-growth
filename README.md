# Little One · Growth Tracker

Offline-first PWA for tracking newborn weight, length, and head circumference against WHO and CDC percentile curves. Pure static HTML / CSS / JS — no build step, no backend, no accounts. Data lives only on your device.

## Deploy to GitHub Pages

From inside this folder:

    git init
    git add .
    git commit -m "initial commit"
    git branch -M main
    git remote add origin https://github.com/USERNAME/REPO-NAME.git
    git push -u origin main

Then on github.com → the repo → **Settings → Pages → Source: `main` branch, `/ (root)` → Save**.

The site will be live at `https://USERNAME.github.io/REPO-NAME/` after a minute or two.

## Install on iPhone

1. Open the URL in **Safari** (Chrome/Firefox on iOS can't install PWAs — only Safari).
2. Tap the **Share** button → **Add to Home Screen**.
3. Tap the new icon on your home screen — the app opens full-screen, no browser chrome.

First load needs the internet so the service worker can cache all assets; after that it works fully offline.

## Backup your data

All data (baby profile, measurements, theme preference) lives only on this device in `localStorage`. If you lose the phone or clear Safari data, it's gone.

- Tap **⤓ Export** to download a JSON backup of everything in `localStorage`.
- Tap **⤒ Import** to restore from a backup file.

Do this regularly.

## Updating the app

After editing any HTML/CSS/JS/icon, bump the cache version in [`sw.js`](sw.js):

    const CACHE = 'little-one-v1';   // → 'little-one-v2', etc.

Without this bump, installed devices will keep serving the old cached assets and your changes won't appear.

## Files

- `index.html` — the entire app (single page, vanilla JS)
- `manifest.json` — PWA manifest (name, icons, theme colors)
- `sw.js` — service worker (offline cache)
- `icon-180.png`, `icon-192.png`, `icon-512.png` — placeholder app icons (replace with real artwork anytime)

## Stack

Vanilla HTML/CSS/JS, Tailwind (CDN), Chart.js + chartjs-plugin-zoom (CDN), Fraunces + Nunito fonts (Google Fonts). Everything is cached by the service worker after first load.
