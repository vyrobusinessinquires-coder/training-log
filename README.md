# TRAIN LOG — Hybrid Roadmap Edition

A single-user, offline-first workout tracker.

## Included
- Three selectable training stages, each with a seven-day rotation.
- Stage 1 Foundation (weeks 1–6), Stage 2 Intermediate (weeks 7–14), Stage 3 Hybrid Development (month 4+).
- Today workout logger with set completion, weight/reps, steppers, previous-session values and per-exercise rest timer.
- Workout history, localStorage persistence, JSON export/import.
- Gym Mode / Field Mode labels, outdoor stopwatch and lap capture.
- Monthly performance check-ins with trend graph (vertical jump, 40m time and lift markers).
- Tap exercise names for concise cues and links to exercise-demonstration searches.
- Optional camera preview and MediaPipe pose-landmark overlay; model loads from a CDN on first use and needs internet. It is not a form-safety certification.
- Food journal with quick meal check-ins and an offline rule-based training guide.
- Flexible food and recovery reminders and a food journal (no calorie target or restrictive scoring).
- PWA manifest, service worker and 192px/512px icons.

## Feature limitations
- The built-in guide is offline and rule-based, not a connected LLM. A live Gemini coach and AI meal-photo estimates are not implemented; do not put private API keys in browser code.
- The camera preview/landmarks are experimental visual references. No automatic rep validity, injury detection, or safe-lift verdict is claimed. Camera permission requires HTTPS; the MediaPipe model needs internet to download on first use.
- Meal entries are journal notes, not AI calorie/protein estimates or a diet plan. The journal intentionally avoids calorie/protein scoring and bodyweight tracking.

## Safety notes
This build is a tracking utility, not medical or coaching advice. Use age-appropriate, manageable resistance with qualified supervision. Advanced gymnastics, tumbling, parkour, deep shoulder positions and loaded spinal mobility are marked coach-led rather than provided as unsupervised instructions. Do not progress by deadline; involve a parent/guardian and qualified coach.

## Publish on GitHub Pages
Upload the contents of this folder to the root of the repository, preserving the `icons/` folder. In Settings → Pages choose Deploy from a branch, `main`, `/(root)`.

## Install
Open the HTTPS GitHub Pages URL on your phone and choose Add to Home Screen / Install app.

## Data
Workout data is stored in localStorage on the device/browser. Export JSON backups regularly. Clearing browser data or changing devices can remove local logs unless restored from a backup.


## Camera rep counter
- The on-device camera guide can estimate bodyweight squat and push-up repetitions from visible pose landmarks.
- Video processing stays in the browser; frames are not sent to the coach backend.
- Counts are approximate and may be wrong when joints are hidden or the camera angle changes. This is not form analysis, injury detection, or a safety verdict. Use a clear space and comfortable bodyweight movements only; ask a qualified coach to assess technique.

## Optional Gemini coach backend
The live coach is optional. The offline guide continues to work if no backend URL is configured.

A Cloudflare Worker proxy is included in `worker/`. It keeps the Gemini API key server-side, restricts browser requests to the GitHub Pages origin, limits request size and message history, and applies per-IP rate limits (6 requests/minute and 40/day). Rate limits reduce accidental overuse but do not guarantee a spending cap. Review provider billing and account limits with a parent/guardian before enabling a paid API.

### Deploy (parent/guardian assistance recommended)
1. Create or use a Google AI Studio API key and review its current billing, usage and data terms with a parent/guardian. Never paste the key into GitHub, this chat, or the PWA.
2. Install Node.js and Wrangler on a computer with access to the repository, then open a terminal in the repository root.
3. From the `worker` folder, run `npx wrangler login`.
4. Add the key as a Worker secret: `npx wrangler secret put GEMINI_API_KEY`. Paste it only into the secure terminal prompt.
5. Deploy from the `worker` folder with `npx wrangler deploy`.
6. Copy the resulting `https://train-log-coach.<your-subdomain>.workers.dev/api/coach` URL into TRAIN LOG → Settings → Secure backend URL, then save it.
7. Test with a general workout-planning question. If the Worker URL changes, update the saved endpoint.

The Worker uses Google's Gemini `gemini-3.5-flash` generateContent endpoint. Do not deploy the Worker until a parent/guardian has reviewed provider costs and account settings. If you do not want an AI service, leave the endpoint blank and use the offline guide.
