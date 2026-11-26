# TRAIN LOG — private workout PWA

A single-user, static Progressive Web App. No account, server, analytics, external libraries, or cloud sync.

## Included
- Today screen opens directly on the current rotation day.
- Seven-day workout routine with ordered warm-up, primer, strength/accessory, and stretching phases.
- Set check-offs, numeric weight/reps fields, +/- steppers, and last-completed-session prefill.
- Adjustable per-exercise rest timer with +15 seconds, Skip, and a subtle Web Audio completion chime.
- Automatic localStorage persistence and session history.
- JSON backup export/import.
- PWA manifest, generated 192px/512px app icons, service worker, and iOS Add to Home Screen metadata.

## Run locally
For basic testing, serve this folder from a local HTTP server. For example, with Python installed:

```bash
python -m http.server 8000
```

Then open `http://localhost:8000` in a browser. Service workers and installability require HTTPS in production (localhost is allowed for local testing). Opening `index.html` directly with a `file://` URL will not enable PWA installation or offline service-worker caching.

## Publish as a static site
Upload the contents of this folder to a static host with HTTPS (GitHub Pages works). Keep `index.html`, `manifest.webmanifest`, `sw.js`, and the `icons` folder at the same relative paths. Once published, open the site in Safari/Chrome on your phone and choose **Add to Home Screen** / **Install app**.

## Data and backups
All workout records are stored in this browser's localStorage on this device. Browser storage can be cleared by device/browser cleanup, so use **Settings → JSON Backup → Export Data** periodically. Import replaces the current local data after confirmation. There is no server-side copy.

## Training and food notes
This app is a personal log, not medical advice. The routine uses conservative substitutions for some advanced acrobatic/high-risk movements: advanced skills are coach-supervised, speed work is controlled, and no all-out/max-effort prescriptions are included. Use appropriate adult/qualified-coach supervision for lifting and gymnastics. Stop if you experience pain or feel unwell.

The food reminders are flexible and food-first. Fixed calorie/protein goals and mass-gainer/whey schedules are not built in; nutrition needs during adolescence vary and supplement decisions should be discussed with a parent/guardian and qualified health professional.
