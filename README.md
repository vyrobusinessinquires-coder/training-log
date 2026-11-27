# TRAIN LOG — Hybrid Roadmap Edition

A single-user, offline-first workout tracker.

## Included
- Three selectable training stages, each with a seven-day rotation.
- Stage 1 Foundation (weeks 1–6), Stage 2 Intermediate (weeks 7–14), Stage 3 Hybrid Development (month 4+).
- Today workout logger with set completion, weight/reps, steppers, previous-session values and per-exercise rest timer.
- Workout history, localStorage persistence, JSON export/import.
- Gym Mode / Field Mode labels, outdoor stopwatch and lap capture.
- Monthly performance check-ins with trend graph (vertical jump, 40m time, lifts, optional bodyweight).
- Tap exercise names for concise cues and links to exercise-demonstration searches.
- Optional camera preview and MediaPipe pose-landmark overlay; model loads from a CDN on first use and needs internet. It is not a form-safety certification.
- Food journal with quick meal check-ins and an offline rule-based training guide.
- Flexible food and recovery reminders and a food journal (no calorie target or restrictive scoring).
- PWA manifest, service worker and 192px/512px icons.

## Feature limitations
- The built-in guide is offline and rule-based, not a connected LLM. Do not put private API keys in browser code.
- The camera preview/landmarks are experimental visual references. No automatic rep validity, injury detection, or safe-lift verdict is claimed. Camera permission requires HTTPS; the MediaPipe model needs internet to download on first use.
- Meal entries are journal notes, not AI calorie/protein estimates or a diet plan.

## Safety notes
This build is a tracking utility, not medical or coaching advice. Use age-appropriate, manageable resistance with qualified supervision. Advanced gymnastics, tumbling, parkour, deep shoulder positions and loaded spinal mobility are marked coach-led rather than provided as unsupervised instructions. Do not progress by deadline; involve a parent/guardian and qualified coach.

## Publish on GitHub Pages
Upload the contents of this folder to the root of the repository, preserving the `icons/` folder. In Settings → Pages choose Deploy from a branch, `main`, `/(root)`.

## Install
Open the HTTPS GitHub Pages URL on your phone and choose Add to Home Screen / Install app.

## Data
Workout data is stored in localStorage on the device/browser. Export JSON backups regularly. Clearing browser data or changing devices can remove local logs unless restored from a backup.
