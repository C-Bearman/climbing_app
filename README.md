# BearmanClimbs

A personal climbing training log — built as a PWA (Progressive Web App) using vanilla HTML, CSS and JavaScript.

**Live app:** https://c-bearman.github.io/climbing_app/

---

## What it does

Daily logging of training metrics, stored locally on your phone:

- Climbing day / Rest day toggle
- Sleep hours and water intake
- Physical and mental energy (1–10)
- Session rating and session notes (climbing days)
- Stretching / mobility toggle and flexibility rating (1–10)
- Optional nutrition (calories and protein)
- General notes

**Charts tab** — visualise trends over time: session ratings, sleep, water, energy, flexibility and stretching consistency. Includes goal lines for sleep and water targets.

**CSV export / import** — keeps a single master file you can hand to your coach or restore from at any time.

---

## Your data

All entries live in **localStorage** on your phone — nothing is sent anywhere. To back up or share with your coach, tap **Export CSV** in the Data section. To restore on a new device or after clearing your browser, tap **Import CSV** and select your file.

---

## Installing on Android

1. Open **Chrome** on your phone and go to the live URL above
2. Tap the three-dot menu → **Add to Home screen**
3. The app will appear on your home screen and open full-screen with no browser bar

---

## Updating the app

Whenever a change is pushed to `master`, GitHub Pages redeploys within ~60 seconds. The service worker will pick up the new version automatically on the next load. If changes don't appear, go to Chrome → Settings → Privacy and security → Clear browsing data → Cached images and files.

---

## Roadmap

### Recently shipped
- [x] `feature/notes-tooltips` — 40-char notes fields with live counter; two-line tooltips on Session Rating and Flexibility charts
- [x] `feature/workout-tracker` — third Workout tab; exercises with flexible field tracking (Reps / Weight / Duration); PB chips; sets with copy/hold-to-delete; full-screen save confirmation; CSV export & import
- [x] `feature/workout-visualisations` — Workout Progress section in Charts tab; exercise picker adds individual cards; metric pills (Session Max / Session Total); sleep/energy dot colour coding with dynamic legend; "Colour nodes by" selector on Session Rating, Flexibility and Workout charts; time range slider wired to workout charts

### Next up
- [ ] Workout data visualisations in Charts tab — refine the exercise picker UX; add PB milestone marker (dashed line at all-time best)
- [ ] Workout session notes — add a notes field to the workout tracker (per session, not per set) so users can log how a session felt; show these notes on hover in the workout charts
- [ ] Workout plan import — allow importing a saved workout template (e.g. "Pulling session: 5×pull-ups, 3×ring rows") that pre-populates the exercise list so the user doesn't have to build it from scratch each time
- [ ] Rest day data — decide how rest days interact with the workout tracker; currently the workout tab is always available regardless of the daily log climbing toggle. Consider whether rest day entries should be blocked, flagged, or used to show recovery context on workout charts
- [ ] History log UX — show 3 entries at a time, scrollable, rather than the full list
- [ ] Onboarding / tutorial overlay — first-launch walkthrough of Log, Workout and Charts tabs; must include how to rename or delete a misspelled exercise name (e.g. if a user saves "Jumpinh" they currently have no way to correct it)
- [ ] UX review: audit all info (ℹ︎) buttons across the app — check the text shown is accurate, helpful, and consistent in tone
- [ ] User-configurable dot colour thresholds — Session Rating, Flexibility, and Workout Progress charts all let users choose which metric colours the dots (sleep / mental / physical energy); extend this so users can set their own green/amber/red thresholds per metric (e.g. "for me, 7h+ sleep is good, not 8h+")

### Charts — UI polish
- [ ] **Draggable chart ordering** — allow users to reorder the chart accordion sections by holding and dragging, so frequently used charts (e.g. Workout Progress) can be pinned to the top; order should persist across sessions via localStorage
- [ ] **Session Rating x-axis** — currently shows session numbers (1, 2, 3…); switch to actual dates. Complexity: the ordinal axis was chosen specifically to avoid visual gaps on days with no climbing session; switching to dates needs gap-handling so the line does not break on rest days (Chart.js `spanGaps` or pre-filtering)
- [ ] **Tooltip content for colour-coded charts** — tooltip currently shows date and general notes; add a line showing the selected colour metric and its value for that session (e.g. "Sleep: 8h" or "Mental energy: 7/10"). This also acts as a sanity-check that the colour selector and dot colours are correct
- [ ] **Selective chart re-render on colour selector change** — changing "Colour nodes by" on one chart currently triggers a full `drawAllCharts()` redraw, causing all visible charts to re-animate; ideally only the chart whose selector changed should update
- [ ] **Minimum data threshold for workout charts** — a single data point in the selected time range renders a lone dot with no connecting line, which looks broken; show a "not enough data in this range" message instead when fewer than 2 data points exist

### Workout tab — UI polish
- [ ] **Workout entry management** — no way to rename a misspelled exercise or delete individual saved sets; needs a management screen or edit flow, and must be covered in the onboarding tutorial
- [ ] **Remove Exercise button** — the × button in the exercise block is easy to miss; consider labelling it "Remove Exercise" and giving it a red tint to follow standard convention for destructive actions
- [ ] **Workout date highlights** — in the workout tab date picker, highlight dates that have saved workout entries (e.g. a green underline or dot) so the user can easily spot and navigate to past sessions

### Log page — planned additions
- [ ] **Climbing session type tracking** — when logging a climbing day, capture what kind of session it was: discipline (bouldering / rope / both), session goal (max effort / projecting / technique / volume), and effort level. This enriches the Session Rating chart context and could unlock filters like "show only projecting sessions" or correlate session type with rating trends


- [ ] **Body measurements (optional, infrequent)** — weight (kg) and height (cm) stored as a separate profile, not a daily log field. Not something you fill in every session — more like a one-time or monthly update. Needs a dedicated section or modal, separate from the day-to-day log form
- [ ] **Strength-to-weight insights** — once body weight is stored, workout charts can express lifts as % of bodyweight (e.g. Pull-ups +60 kg at 90 kg = 167% BW). Climbing is a power-to-weight sport so this reframes raw numbers in a meaningful way
- [ ] **"Why track this?" info button** — a hold-to-reveal tooltip or info overlay on optional fields (weight, height, nutrition, supplements) explaining what insights that data unlocks. Keeps the UI clean for people who just want to log, but rewards curiosity
- [ ] **Nutrition quality slider** (1–10, self-rated — how well did you eat today?) alongside the existing calorie/protein fields
- [ ] **Supplement tracker** — user-defined tick-box list (creatine, vitamin D, protein shake, etc.); presence/absence per day is enough — no units needed. Configurable by the user, similar to how exercises are defined in the workout tracker

### Future branches
- [ ] Goal lines extended to more metrics beyond sleep and water
- [ ] Water reminder notifications during climbing sessions
- [ ] Auto-sync to Google Sheets via Google Apps Script

### Eventual v1.0
- [ ] Wrap as native APK with Capacitor → **Bearman Climbs** on the Play Store
