# Sophie's Money: offline budget app

A small web app (PWA) that installs to the home screen and works with no signal.
Everything is saved on the phone itself. It has no server, no account and no tracking.

## 1. Host it (one-off, about 5 minutes)

It needs to be served over HTTPS once so the phone can install it. After that it runs offline.

**Option A: Cloudflare Pages or Netlify (the URL isn't public in a repo)**
1. Go to https://app.netlify.com/drop, or Cloudflare Pages and choose "Upload assets".
2. Drag this whole folder in.
3. Sign in or create a free account so the site isn't deleted, and rename it to something unguessable,
   e.g. `sophie-money-7k2q`.

**Option B: GitHub Pages**
Push this folder to a repo, then go to Settings → Pages → Deploy from branch → `main` / root.
A free account needs a public repo, but the code contains no personal figures.

Her figures are not in these files. They load from the setup file or code on her phone.

## 2. Install on Sophie's phone
1. Open the site URL. On iPhone use **Safari**; on Android use **Chrome**.
2. Add it to the home screen *before* setting anything up:
   - iPhone: Share → Add to Home Screen.
   - Android: ⋮ → Install app.
3. Open **Money** from the home screen, then on the Today tab either:
   - paste the setup code (`setup-code.txt`, send it to her on WhatsApp), or
   - choose `sophie-plan.json`.
4. Enter her current balance in "Money in your account now".

## 3. Updating later
Change the files, **bump `VERSION` in `sw.js` and `APP_VERSION` in `index.html`**, then re-upload.
The next time she opens the app with signal, it shows "A new version is ready → Update now".
Her data is kept.

## Backups
Plan tab → **Back up my data** opens the share sheet. She can save to Files or send to you.
Restore from the same card. The app nags if no backup has been made for 30 days.

## Month logic
- Usual payday is the 27th, moved to the previous working day for weekends and England & Wales bank holidays (to 2028).
- The one-off payday box replaces the payday for that calendar month only (e.g. an early December pay).
- "Until your first payday" mode runs until `bridge.until`, then switches to the weekly view.
- Payday ticks reset each pay month.
