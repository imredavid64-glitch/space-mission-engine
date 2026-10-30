# How to legally use this library in the NASA Space Apps Challenge 2026

## The rule (read this first)

NASA Space Apps requires the **submitted project to be original work created during the hackathon**.
It does **not** prohibit using pre-existing open-source libraries, frameworks, or reusable components
— it prohibits submitting pre-built *project-specific* code as if it were hackathon work.

This library is the first thing. NASAMAP-the-app is the second.

## Strategy

1. **Publish this library as open source BEFORE the hackathon.**
   - Push this repo to GitHub as `imredavid64-glitch/space-mission-engine` (or a name you like).
   - Add a `LICENSE` (MIT, already included) and tag a release (e.g. `v0.1.0`).
   - Optionally publish to npm (`npm publish`) so the hackathon app can `npm install` it.
   - Do this **before** the hackathon clock starts. Commit timestamps are your evidence.

2. **During the hackathon, build a NEW app repo** (e.g. `nasamap-2026` or a challenge-specific name).
   - Fresh Next.js app. Consume this library via npm / git dependency / local link.
   - All routes, UI, game layer, new features, new datasets, new scenarios are written during the hackathon.
   - Do NOT copy NASAMAP's `src/app`, `src/components`, or app-specific data (scenarios, articles, personas) verbatim — rebuild them, and improve them.

3. **Disclose in the submission.**
   - In `SUBMISSION.md` / README, state clearly:
     > "Pre-existing open-source dependency: `space-mission-engine` (MIT, published <date>,
     >  https://github.com/.../space-mission-engine). All application code in this repository was
     >  written during the hackathon."
   - List which modules come from the library (engine + datasets) vs. built during hackathon (UI, routes, features).

4. **Keep the library general-purpose.**
   - It must read as a reusable library, not "NASAMAP's backend." Avoid project-specific names,
     challenge-specific scenarios, or app branding inside it. (Already the case: physics + data.)

## What counts as "built during hackathon" (must be new)

- The Next.js app shell, routing, layout, styling, all components.
- The game layer (scenarios, briefs, grading UX) — can reuse the library's scoring functions but the
  content/briefs should be (re)authored during hackathon.
- Any new feature you add for the chosen challenge.
- New datasets you curate during the hackathon.

## What can come from the library (pre-existing, disclosed)

- `src/lib/*` engine (astro, rocket, life, score, mission, trajectory, ...).
- `src/data/*` curated datasets and snapshots.
- Validation script + tests.

## Evidence checklist

- [ ] Library repo public on GitHub with commits dated before hackathon.
- [ ] Tagged release (v0.1.0) before hackathon.
- [ ] Hackathon app repo created fresh during hackathon (first commit during hackathon).
- [ ] README/SUBMISSION disclose the dependency + link.
- [ ] No copy-paste of NASAMAP's app/UI code into the hackathon app without disclosure.

## If judges ask "did you build this before?"

Answer honestly: "The physics engine is an open-source library I published before the hackathon
(MIT, link). The application, UI, game, and challenge-specific features were built during the
hackathon on top of it." That is legitimate and common.