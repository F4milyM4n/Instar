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

## What's new in version 3

- **Belts.** Instars are grouped into White (1–2), Blue (3–5), Purple (6–7), Brown (8–9) and Black (10), split where the consequence of a failure changes. Each completed instar is a stripe. The diver's belt and stripes show beside their name; instar tiles carry a small belt-colored mark.
- **Detail levels follow the belt.** White = Basic, Blue = Standard, Purple and above = Full, so full planning tools arrive with doubles at Instar 6.

## What's new in version 2

- **Detail that grows with the diver.** The Dive Plan and the after action review show only the essentials at first (Basic), add gas rules, pO₂, gas density, ascent rate, gradient factors and root-cause review next (Standard), and unlock trimix and decompression planning last (Full) — by belt since version 3. A **Detail** menu (Auto / Basic / Standard / Full) overrides it. Hidden settings are still used and summarized in plain language; safety warnings always show.
- **Max depth from both limits.** The gas label shows the shallower of the pO₂ MOD and the gas-density limit, and names which one sets it.
- **Focused contingencies.** One deeper (+10 ft) and one longer (+5 min) recovery schedule — the next table increments, and the most likely planning errors.
- **Instar always set.** Plan and log instar menus list 1–10 only and default to the diver's or team's current instar.
- **New icon** in the header.

## Publishing an update

1. Replace the changed files in the repository.
2. In `sw.js`, change `VERSION` (for example `instar-v1` → `instar-v2`).
3. Installed copies show **"A new version of Instar is ready — Reload"** the next time they open online.

## Your data

Everything is stored on the device, in the browser's storage for this site. Nothing is uploaded anywhere.

- Use **Training → Backup & restore** to copy a backup before changing phones, clearing browser data or reinstalling.
- On iPhone, the installed home-screen app keeps **separate storage from Safari**. Data entered in Safari doesn't appear in the installed app, and the reverse. Restore a backup to move it across.
- The app asks the browser to keep its storage persistent, but a backup is the only guarantee.
