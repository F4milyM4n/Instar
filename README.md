# Instar — diver development

Instar is an installable web app for divers who want to develop, not just collect cards:

- **Dive Plan** — team gas plan (rock bottom, turn pressures, 5-minute use), MOD and gas density limits, no-deco limits, an optional Bühlmann ZHL-16C decompression model with gradient factors, trimix and deco gas planning, contingency schedules, pre-dive checks and a copyable brief.
- **Dive Log** — an after action review for every dive, with calculated SAC, plan-vs-actual comparison, incidents, reflection prompts, site notes and training credit.
- **Training** — ten instars, each a report card of experiences, graded skills with measurable standards, and performance gates.

It runs entirely in the browser. No account, no server, and it works offline once installed.

> **Planning aid only.** Verify every plan against your training, your own tables and your dive computer. Cross-check every decompression schedule with an independent planner before diving it.

## Files

| File | Purpose |
|---|---|
| `index.html` | The whole app (HTML, CSS and JavaScript in one file) |
| `manifest.webmanifest` | Name, colors and icons used when installing |
| `sw.js` | Service worker — makes the app work offline |
| `icons/` | App icons (standard, maskable for Android, Apple touch icon, favicon) |
| `favicon.ico` | Browser tab icon |
| `.nojekyll` | Tells GitHub Pages to serve files as-is |

## Publish on GitHub Pages

1. Create a new repository on GitHub (for example `instar`).
2. Upload every file and the `icons` folder to the repository root.
3. In the repository, open **Settings → Pages**.
4. Under **Build and deployment**, choose **Deploy from a branch**, branch **main**, folder **/ (root)**, then **Save**.
5. After a minute, the app is live at `https://<your-username>.github.io/instar/`.

GitHub Pages serves over HTTPS, which installing and offline use both require.

## Install it

- **iPhone / iPad (Safari):** tap **Install app** in the header for steps, or **Share → Add to Home Screen**.
- **Android (Chrome):** tap **Install app** in the header and confirm.
- **Desktop (Chrome / Edge):** tap **Install app**, or use the install icon in the address bar.

## Publishing an update

1. Replace the changed files in the repository.
2. In `sw.js`, change `VERSION` (for example `instar-v1` → `instar-v2`).
3. Installed copies show **"A new version of Instar is ready — Reload"** the next time they open online.

## Your data

Everything is stored on the device, in the browser's storage for this site. Nothing is uploaded anywhere.

- Use **Training → Backup & restore** to copy a backup before changing phones, clearing browser data or reinstalling.
- On iPhone, the installed home-screen app keeps **separate storage from Safari**. Data entered in Safari doesn't appear in the installed app, and the reverse. Restore a backup to move it across.
- The app asks the browser to keep its storage persistent, but a backup is the only guarantee.
