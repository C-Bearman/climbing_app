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
- [x] `chore/ui-polish` — single-dot chart empty state ("not enough data" message); Remove Exercise button styled red and labelled clearly; tooltip colour metric line on all colour-coded charts (Session Rating, Flexibility, Workout Progress); tooltip label reads "Max 22.5kg" / "Total 12 reps" etc.; consistent date format across all chart tooltips ("Fri 3 Apr"); Stretching Consistency tooltip reads "Stretched X times" with week label "w/c 20 Apr"; coloured square removed from all tooltips; tooltip spacing and styling unified across chart types; Sleep/Water/Energy Trends nodes filled and all four lines have area fill; Trends tooltip formatted with colour square and units ("Sleep: 8h", "Mental: 7/10"); goal line tooltip shows label only with no date
- [x] `feature/csv-validation` — workout data section styled to match log page; Save as new cancel bug fixed; import restricted to .csv files only; CSV validation overlay listing header and date format errors; re-upload bug after cancelling validation fixed; two-step confirmation on both log and workout imports; log import supports Merge (overwrite matching dates, keep the rest) or Replace all (wipe and reload) to support both personal sync and coach use-cases; `.gitignore` added
- [x] `feature/history-and-deletion` — log history panel now scrollable (all entries shown, capped height with native scroll); delete button per entry with inline confirmation (Delete / Cancel); Delete Application Data button on both log and workout data sections with confirmation overlay, backup prompt, and Save data option before proceeding
- [x] `feature/workout-refinements` — per-exercise session notes field (40-char, live counter) beneath the set controls; notes stored in workout CSV and surfaced as 📝 tooltip labels on workout progress charts; workout date picker replaced with a custom calendar grid showing a green tinge on dates with saved workout data; date badge shows an open/close chevron consistent with chart and exercise accordions

### Next up
- [ ] Workout data visualisations in Charts tab — refine the exercise picker UX; add PB milestone marker (dashed line at all-time best)
- [x] Workout session notes — per-exercise notes field (40-char) on the workout tracker; shown as 📝 tooltip labels on workout progress charts
- [ ] Workout plan import — allow importing a saved workout template (e.g. "Pulling session: 5×pull-ups, 3×ring rows") that pre-populates the exercise list so the user doesn't have to build it from scratch each time
- [ ] Rest day data — decide how rest days interact with the workout tracker; currently the workout tab is always available regardless of the daily log climbing toggle. Consider whether rest day entries should be blocked, flagged, or used to show recovery context on workout charts
- [x] History log UX — show 3 entries at a time, scrollable, rather than the full list
- [ ] Onboarding / tutorial overlay — first-launch walkthrough of Log, Workout and Charts tabs; must include how to rename or delete a misspelled exercise name (e.g. if a user saves "Jumpinh" they currently have no way to correct it); should also ask on first launch whether the user has existing data to import (supports the coach use-case where athletes export their CSV and hand it to a coach who can import and view their data)
- [ ] UX review: audit all info (ℹ︎) buttons across the app — check the text shown is accurate, helpful, and consistent in tone
- [ ] **User-configurable optional sections** — as more optional fields are added (finger health, nutrition, supplements, body measurements etc.), users should be able to hide sections they don't track and re-enable them later; a simple show/hide toggle per section stored in localStorage would keep the log form clean for users who only want the core fields
- [ ] User-configurable dot colour thresholds — Session Rating, Flexibility, and Workout Progress charts all let users choose which metric colours the dots (sleep / mental / physical energy); extend this so users can set their own green/amber/red thresholds per metric (e.g. "for me, 7h+ sleep is good, not 8h+")

### Charts — UI polish
- [ ] **Draggable chart ordering** — allow users to reorder the chart accordion sections by holding and dragging, so frequently used charts (e.g. Workout Progress) can be pinned to the top; order should persist across sessions via localStorage
- [ ] **Session Rating x-axis** — currently shows session numbers (1, 2, 3…); switch to actual dates. Complexity: the ordinal axis was chosen specifically to avoid visual gaps on days with no climbing session; switching to dates needs gap-handling so the line does not break on rest days (Chart.js `spanGaps` or pre-filtering)
- [ ] **Tooltip font rendering consistency** *(known limitation — investigated, no clean fix available)* — Session Rating and Flexibility Rating charts use a custom linear x-axis (to avoid gaps on non-climbing days), while Workout Progress uses a standard category axis. Chart.js renders Canvas tooltip text slightly differently between these two axis types. All tooltip config options (font, padding, bodySpacing, displayColors, callbacks) are now identical in code — the remaining visual difference is a Chart.js rendering artefact that cannot be controlled via the tooltip API. This is a PWA proof-of-concept constraint; a native app rewrite would not share this limitation.
- [ ] **Selective chart re-render on colour selector change** — changing "Colour nodes by" on one chart currently triggers a full `drawAllCharts()` redraw, causing all visible charts to re-animate; ideally only the chart whose selector changed should update

### Workout tab — UI polish
- [ ] **Workout entry management** — no way to rename a misspelled exercise or delete individual saved sets; needs a management screen or edit flow, and must be covered in the onboarding tutorial
- [x] **Log entry deletion** — delete button per entry with inline confirmation; entry removed from localStorage, streak and week counter update immediately
- [x] **Workout date highlights** — workout date picker replaced with a custom calendar grid; dates with saved entries shown with a green tinge; date badge shows open/close chevron
- [ ] **CSV import overlay UX** — the core import validation and Merge/Replace all flow is in place; revisit the wording, layout, and visual styling of the warning overlays on both Log and Workout tabs after real-world use to see if anything needs tightening up

### Log page — planned additions
- [ ] **Climbing session type tracking** — when logging a climbing day, capture what kind of session it was: discipline (bouldering / rope / both), session goal (max effort / projecting / technique / volume), and effort level. This enriches the Session Rating chart context and could unlock filters like "show only projecting sessions" or correlate session type with rating trends
- [ ] **Perceived session effort** — a simple 1–10 slider or rating for "how hard did today's session feel?", distinct from Session Rating (which captures quality/performance). Useful for tracking RPE trends and spotting when high effort isn't translating to good sessions (fatigue, overtraining signals)
- [ ] **Finger health tracking** *(optional field)* — a daily finger health rating (1–10) or a quick "any issues?" toggle with a notes field; useful for monitoring tweaks, pulley strains, and recovery over time. Could tie into the charts tab to overlay finger health against session ratings
- [ ] **Body measurements (optional, infrequent)** — weight (kg) and height (cm) stored as a separate profile, not a daily log field. Not something you fill in every session — more like a one-time or monthly update. Needs a dedicated section or modal, separate from the day-to-day log form
- [ ] **Strength-to-weight insights** — once body weight is stored, workout charts can express lifts as % of bodyweight (e.g. Pull-ups +60 kg at 90 kg = 167% BW). Climbing is a power-to-weight sport so this reframes raw numbers in a meaningful way
- [ ] **"Why track this?" info button** — a hold-to-reveal tooltip or info overlay on optional fields (weight, height, nutrition, supplements) explaining what insights that data unlocks. Keeps the UI clean for people who just want to log, but rewards curiosity
- [ ] **Nutrition quality slider** (1–10, self-rated — how well did you eat today?) alongside the existing calorie/protein fields
- [ ] **Supplement tracker** — user-defined tick-box list (creatine, vitamin D, protein shake, etc.); presence/absence per day is enough — no units needed. Configurable by the user, similar to how exercises are defined in the workout tracker

### Future branches
- [ ] **Desktop / responsive layout** *(optional — Play Store is the primary target)* — the app is designed for a mobile viewport and works on phone screens. On a laptop or monitor the layout is narrow and centred. A responsive pass could widen the layout at larger breakpoints, reflow the tab navigation, and make charts larger — useful if coaches want to review athlete data on a desktop. This is lower priority than the Play Store APK build (see Eventual v1.0 below), but could be a lightweight CSS-only change if the scope is kept narrow.
- [ ] Goal lines extended to more metrics beyond sleep and water
- [ ] Water reminder notifications during climbing sessions
- [ ] Auto-sync to Google Sheets via Google Apps Script

### Eventual v1.0
- [ ] Wrap as native APK with Capacitor → **Bearman Climbs** on the Play Store
