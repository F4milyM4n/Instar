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

## Versions

Instar uses **MAJOR.MINOR.PATCH** numbers, shown in the app's footer:
- **Major** (7.0) — a new capability, or a change to how plans are calculated or how progress is counted.
- **Minor** (6.1) — refinements and added content that don't change existing plans.
- **Patch** (6.1.1) — fixes only. Omitted when it's 0.

The number lives in one place in `index.html` (`APP_VERSION`); `sw.js` uses the same number for its cache name so installed apps update.

## What's new in 8.0

**No-stop limits from the model at GF high 90**
- The no-deco limit now comes only from the decompression model, at GF high 90 for no-stop dives (less 5 per risk factor, floor 70). The table is no longer part of the limit. With no stops only GF high matters, a direct ascent is available, and the safety stop adds margin the limit doesn't count.
- Air examples: 50 ft 76 min, 60 ft 53, 70 ft 39, 80 ft 29, 100 ft 18 (previously 64, 44, 31, 24, 15).
- **Gradual shift from no-stop to decompression diving.** Once a dive owes stops, they're first worked out at the no-stop GF high (90); GF high then slides toward the decompression GF high (80) as that obligation grows, reaching it at 20 min of stops. One extra minute past the limit owes about one extra minute of stops — at 60 ft on air: 53 min none, 54 min 1, 56 min 5, 60 min 12, 70 min 30, 80 min 51 (the full decompression margin). The same rule covers the plan, contingencies and earlier dives.
- Risk factors lower both ends by 5 each. "Team member new to planned decompression" lowers only the decompression end, so planning decompression never shortens the no-stop limit.
- A preset or custom gradient-factor choice (Instar 7 up) applies to no-stop dives too.

## What's new in 7.0

**Repetitive dives**
- A **Repetitive dive** checkbox in the profile opens an **Earlier dives today** card. Enter each earlier dive (max depth, bottom time, O₂, and helium from Instar 10) and the surface interval that followed it. Nothing depends on the log; **Fill from log** can copy a logged dive in.
- Each earlier dive is rebuilt from its profile, ascended with any stops the model requires, and off-gassed on air through its surface interval. The plan starts from what is left, so its no-deco limit, stops and gas change with it.
- Profiles: **Square** (all at max depth) and **From average depth** (two levels that match your computer's average) at every instar; **Deep-weighted** and **Shallow-weighted** multilevel estimates and **Enter levels** from Instar 3.
- The card shows the no-deco limit now vs a first dive (and vs square when a multilevel shape is used), the extra surface time that returns it to within 5% of a first dive, CNS and OTU carried into this dive, and a common before-flying guideline (18 h after repetitive dives, 24 h after decompression). The brief adds a repetitive line.
- The checkbox replaces "Repetitive dive today" in the gradient-factor risk list; it now both models the leftover gas and lowers GF high.
- Below Instar 7, a plain-language **Things that shorten today's no-deco limit** list (workload, flying after, feeling unwell, plus cold, current and repetitive from the plan) shows the no-deco limit with and without them. Gradient-factor numbers stay hidden until Instar 7.

## What's new in 6.0

**Knowledge topics in every instar**
- The physics and physiology each instar's skills depend on — from pressure, Boyle and Archimedes at Instar 1 to helium, blending and bubble models at Instar 10 — are listed in the report card under the principle they support, marked **KNOW**, next to the skills they explain. Topics are introduced where a skill first depends on them and revisited in more depth later.
- Each topic is graded Developing / Performing / Excelling. Performing means explaining it, naming the skill or rule it drives, and working the numbers.
- Each instar has one problem done by hand, with a worked answer to check against, placed under its principle.
- Knowledge counts toward completing an instar (shown with skills as "Skills & knowledge"): every topic and the by-hand problem need Performing.

**Dive Plan refinements**
- Travel gas moved to the profile section, next to the bottom gas. When the bottom gas is hypoxic, the requirement shows right there, and it is no longer tied to the stages switch.
- Gas extension now covers bottom stages only.
- Instar readiness warnings (limits, prerequisites, credentials) moved to the Team section, so the profile shows only gas and depth problems.
- Advanced planning appears only from the instar that teaches it: doubles from 6, planned decompression, deco gases and travel gas from 7, overhead planning from 8, bottom stages from 9, mixed gas from 10. Below that, the section stays hidden and a failing plan is told to shorten the dive, go shallower or use a larger cylinder. A switch already turned on in a saved plan stays visible so it can be turned off.
- Direct-ascent instars (1–5) have no turn pressure: the plan ascends at rock bottom and shows **Time to rock bottom**. The gas rule (halves or thirds) appears from Instar 6, where the time shown is **Time to turn** and names the teammate whose usable gas the turn is matched to.
- Planned decompression turns on by itself (marked "required") once a dive from Instar 7 up passes the no-deco limit; it can't be switched off while the plan needs it.
- Overhead plans always use a turn rule (thirds by default); "ascend at rock bottom" is unavailable in an overhead. The time inside is solved together with the decompression it creates, since deco breathed on bottom gas raises rock bottom. A red alert shows when the gas leaves almost no time inside.
- The Basic brief (Instars 1–2) is shorter: one profile line with the no-deco limit, each diver's ascend-at pressure, and a single line for the deeper/longer contingency when it still needs no stops.

## What's new in 5.0

**Instar groups**
- Instars are grouped by what stands between the diver and the surface: **Foundations** (1–2), **Conditions** (3–5), **Virtual ceiling** (6–7) and **Overhead** (8–10).
- Each group shows as a bar in its water color with one dot per instar (filled = complete). The instar list is split under group headings.
- Detail levels follow the group: Foundations = Basic, Conditions = Standard, Virtual ceiling and Overhead = Full.

**Dive Plan reads top to bottom**
- Sections are in the order a plan fails and gets fixed: profile and bottom gas → no-deco limit and decompression → back gas → gas extension → overhead route → dive run → contingencies → checks → brief.
- The advanced switches moved into the section they fix (mixed gas under the profile, planned decompression under the no-deco limit, travel gas and stages under gas extension). They appear when the section above fails, and always at Full detail.
- Sections are numbered as they appear.

**Overhead planning** (venue: Overhead site)
- Time to turn comes from the gas: stages out, then back gas to turn, with an optional cap. The exit mirrors it, scaled by one flow factor per dive (exit time ÷ entry time).
- Gas is drawn by phase: going in, coming out (back-gas return share to the nearest stage, then each stage's return third), then the ascent.
- Sharing check for every exit leg: the gas in hand (back gas, then the teammate's own stage) must get two divers to the next gas at their normal rates. Short legs show red.
- Rock bottom starts at the exit (entrance depth) and runs to the first gas switch.
- The model's ascent on bottom gas is set aside before the gas rule, so the normal ascent never comes out of the spare.

## What's new in 4.0

**Travel gas and stages**
- Travel gas for the descent, with an automatic switch depth (the deepest 10 ft step within pO₂, density and END limits), reused on the ascent.
- Bottom stages filled with the bottom gas. Rules: thirds and dropped (⅓ out, ⅓ back, ⅓ kept), or carried to ⅓ or to 500 psi.
- Rock bottom stays on back gas, to the first depth where a different gas is available.

**Dive run**
- Every gas in the order you breathe it: travel → stages out → back gas to turn → stages back → back-gas return → deco gases.
- The team switches together on run time. The diver whose gas runs out first sets each time; each diver sees their own expected pressure.
- Drop, return and turn pressures can be edited in the run to find where a plan falls short.
- The brief lists the dive run as numbered steps.

**Warnings**
- Red: would kill if not fixed (running out of gas, hypoxic gas).
- Amber: dangerous, escalating, or affects divers differently (pO₂, density, narcosis, oxygen exposure, no-deco limits, gas past the planned return portion, training readiness).

**Training**
- Stage skills with measurable standards: two-cylinder handling and time-based switches (Instar 7), open-water stage practice (Instar 8), a single bottom stage and missing-stage response (Instar 9), multiple stages and travel gas for hypoxic mixes (Instar 10).

## What's new in 3.0

- **Instar groups.** Instars are grouped where the consequence of a failure changes (renamed and regrouped in version 5).
- **Detail levels follow the group,** so full planning tools arrive with doubles at Instar 6.

## What's new in 2.0

- **Detail that grows with the diver.** The Dive Plan and the after action review show only the essentials at first (Basic), add gas rules, pO₂, gas density, ascent rate, gradient factors and root-cause review next (Standard), and unlock trimix and decompression planning last (Full) — by group since version 3. A **Detail** menu (Auto / Basic / Standard / Full) overrides it. Hidden settings are still used and summarized in plain language; safety warnings always show.
- **Max depth from both limits.** The gas label shows the shallower of the pO₂ MOD and the gas-density limit, and names which one sets it.
- **Focused contingencies.** One deeper (+10 ft) and one longer (+5 min) recovery schedule — the next table increments, and the most likely planning errors.
- **Instar always set.** Plan and log instar menus list 1–10 only and default to the diver's or team's current instar.
- **New icon** in the header.

## Publishing an update

1. Replace the changed files in the repository.
2. Set the new number in `APP_VERSION` (`index.html`) and `VERSION` (`sw.js`) — for example `6.1` and `instar-6.1`.
3. Add a "What's new" section above.
4. Installed copies show **"A new version of Instar is ready — Reload"** the next time they open online.

## Your data

Everything is stored on the device, in the browser's storage for this site. Nothing is uploaded anywhere.

- Use **Training → Backup & restore** to copy a backup before changing phones, clearing browser data or reinstalling.
- On iPhone, the installed home-screen app keeps **separate storage from Safari**. Data entered in Safari doesn't appear in the installed app, and the reverse. Restore a backup to move it across.
- The app asks the browser to keep its storage persistent, but a backup is the only guarantee.
