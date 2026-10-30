# Hackathon Build Plan — what to build DURING the hackathon

Companion to LEGALIZATION.md. The library (`space-mission-engine`) is the pre-built backend.
During the hackathon you build the **application** on top of it. This file is your playbook.

## 0. Pre-hackathon (do now, before clock starts)

- [ ] Push this library repo to GitHub, tag `v0.1.0`, (optional) `npm publish`.
- [ ] Pick your primary challenge lane (recommended: **Space Mission Design Game**, or pivot to
      whichever 2026 challenge fits). Re-read that challenge's prompt.
- [ ] Decide app name (could stay NASAMAP, or a challenge-specific name).
- [ ] Prepare a fresh empty repo for the hackathon app (do NOT commit code until hackathon starts).

## 1. Day 1 — Scaffold + core loop (hackathon day 1)

Goal: a working Mission Lab that uses the library.

- [ ] `npx create-next-app` (App Router, TS, Tailwind, ESLint). Add `space-mission-engine` dep.
- [ ] Layout + theme (dark space). Reuse UI primitives you write fresh (don't copy NASAMAP's components).
- [ ] `/mission` route: destination/rocket/crew/stay selectors → call `computeMission` from library →
      show Δv, mass, radiation, comms lag, consumables, ECLSS, GO/NO-GO, S–D grade.
- [ ] Permalink encoding (`design-link` from library) so a design is a shareable URL.
- [ ] Personal best per destination (localStorage) using library's `best-score`.
- [ ] `/play` route: at least 3 scenario briefs with constraints + 0–3 star grading (`scenarios` lib).
- [ ] Report card SVG download (`report-card` lib).

## 2. Day 2 — Fly + Live + Share

- [ ] `/fly`: Apollo 11 replay, Hohmann Moon, Earth–Mars Kepler; CSV export (`trajectory`, `export` lib).
- [ ] `/live`: ISS ground track + KML, Voyager (Horizons), APOD, NEO, space weather; snapshot fallback
      (`live` lib + `src/data/live-snapshots.json`).
- [ ] `/library` + `/search`: articles + MiniSearch index (`commons`, `search` lib).
- [ ] `/commons`: persona advice cards.
- [ ] `/challenges`: challenge aligner (map your shipped capabilities to official challenges).

## 3. Day 3 — Polish + differentiate

Pick 2–3 "wow" features that are genuinely new (not in NASAMAP), e.g.:

- [ ] A new challenge-specific tool (e.g., for your chosen challenge's unique ask).
- [ ] A new visualization (3D, chart) you build fresh.
- [ ] Multiplayer/collaborative sharing (community gallery) — library has `community.ts` helpers.
- [ ] Accessibility + responsive + print styles.
- [ ] Offline PWA (next-pwa) + service worker.
- [ ] Tests for your new app code + run library tests.

## 4. Submission

- [ ] README + SUBMISSION.md with 5-min judge tour, evidence map.
- [ ] Deploy to Vercel (zero env).
- [ ] Disclose `space-mission-engine` dependency (see LEGALIZATION.md).
- [ ] Record demo video.

## What NOT to spend hackathon time on (already in library)

- Physics: Kepler, Hohmann, rocket equation, ECLSS, radiation, surface solar, scoring.
- Data validation (`validate:data`).
- Trajectory solvers, SGP4, exports (CSV/KML).
- Artifact generators (passport, patch, report card) — reuse as-is.

## Notes / gotchas

- Next.js 16 + `--webpack` (next-pwa / OpenNext need webpack). Don't use Turbopack.
- `params` in dynamic routes is a Promise — `await params`.
- Streamed Suspense needs the `$RT` pre-seed script in root layout (see AGENTS.md).
- Windows: kill node + remove `.next` before rebuild.
- Keep the client boundary low; engine stays server/importable.
- Never fabricate numbers — tag documented/derived/estimate; live vs snapshot with date.

## Suggested "new work" ideas to stand out (pick 1)

- Real-time collaboration on a mission design (WebRTC / shared URL state).
- A new challenge-specific dataset you curate + validate during hackathon.
- An AI advisor that calls the engine (client-side, no backend) to explain trade-offs.
- A 3D mission replay you build fresh with R3F.
- Gamification: leaderboards, badges, shareable scorecards.

## Definition of done (quality gates)

```bash
npm run typecheck && npm run lint && npm test && npm run validate:data && npm run build
```
Plus a real-browser click-through of every route.