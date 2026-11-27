# TRAIN LOG

An offline-first workout tracker for the three-stage hybrid training roadmap.

## What's in the app
- Three stages with a seven-day workout rotation.
- Workout logging, previous-session values, rest timer, history and progress charts.
- Gym/Field mode and outdoor stopwatch with lap splits.
- On-device camera counter for bodyweight squats and push-ups. Counts are estimates, not a technique or safety check.
- Offline training guide.
- Optional live Gemini coach, activated only after you deploy the backend below.
- Simple food journal with notes only. No AI meal feature, calorie scoring or protein targets.
- Offline PWA support and JSON backup/restore.

## Important limitations
- The live AI coach is coded but will not respond until the Cloudflare Worker is deployed, its Gemini key is added as a secret, and its URL is saved in app Settings.
- The camera counter estimates repetitions from pose landmarks. It can miscount and does not assess form, detect injury or certify that an exercise is safe. Camera video stays in the browser.
- Workout data is stored in this browser on this device. Export a JSON backup regularly; clearing browser data or changing devices can remove local logs.
- This is a tracking tool, not medical advice or a replacement for an in-person qualified coach. Advanced gymnastics, tumbling and parkour need qualified in-person supervision.

## Open and install
Open the GitHub Pages URL over HTTPS:
https://vyrobusinessinquires-coder.github.io/training-log/

On a phone, use the browser's **Add to Home Screen** or **Install app** option.

## Live AI coach setup (optional)

**You do not need to do this to use the workout tracker.** The offline guide works without any accounts or API keys.

To turn on the live coach, a parent/guardian should help with these steps and review any provider usage or billing terms first.

### What you need
- A Google AI Studio API key.
- A Cloudflare account.
- Node.js installed on a computer.
- This GitHub repository downloaded or cloned to that computer.

### Steps on Windows
1. A parent/guardian creates or reviews the Gemini API key in Google AI Studio. Keep it private. Never paste it into GitHub, the app, or a chat.
2. Install Node.js from https://nodejs.org/ if it is not already installed.
3. Download this repository from GitHub and extract the ZIP.
4. Open the extracted `training-log` folder. Click the address bar in File Explorer, type `cmd`, and press Enter.
5. In the terminal, enter these commands one at a time:

   ```bat
   cd worker
   npx wrangler login
   ```

   A browser window will open. Sign in to the Cloudflare account and approve the connection.

6. Add the secret. In the same terminal, run:

   ```bat
   npx wrangler secret put GEMINI_API_KEY
   ```

   When asked, paste the Gemini key into the terminal prompt (not here, not in GitHub) and press Enter.

7. Deploy the backend:

   ```bat
   npx wrangler deploy
   ```

8. Cloudflare will show a Worker address. Copy it and add `/api/coach` to the end. It should look like:

   ```
   https://train-log-coach.YOUR-SUBDOMAIN.workers.dev/api/coach
   ```

9. Open TRAIN LOG → **Settings** → **Secure backend URL**. Paste that full address and press **Save coach URL**.
10. Open the Coach tab and test with a general question. If it does not connect, check the Worker deployment and URL.

### If you do not want to set up AI
Leave **Secure backend URL** empty. The offline training guide remains available. You can use the full workout app without Cloudflare or a Gemini key.

## Developer validation
GitHub Actions checks JavaScript syntax, Worker syntax, the PWA manifest, required icons and app-shell references. These automated checks do not replace testing on a real phone or deploying the optional AI backend.
