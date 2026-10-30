# space-mission-engine

**Pure, unit-tested science engine for space mission design.** No database, no backend, no API keys.

This is the reusable "main backend" extracted from NASAMAP: orbits, Kepler, Hohmann transfers,
life support (ECLSS), radiation, surface ops, scoring, trajectories, live-feed snapshots, and
the curated datasets that back them. Everything is side-effect free and covered by 272 tests.

## Why this exists

Built ahead of the NASA Space Apps Challenge 2026 as a general-purpose, open-source library so
that during the hackathon the focus can be on the *application* (UI, game layer, new features)
instead of re-deriving physics. Published as MIT so any team can build on it.

## Use it

```bash
npm install space-mission-engine   # or: git dependency / local link during hackathon
```

```ts
import { computeMission } from "space-mission-engine/lib/mission";
import { hohmannTransfer } from "space-mission-engine/lib/rocket";
```

Subpath imports always work: `space-mission-engine/lib/<module>` and `space-mission-engine/data/<dataset>`.

## Modules

See `src/lib/*` — one file per concern (astro, rocket, rocket-builder, comm, life, surface,
mission, score, trajectory, orbit, export, design-link, passport, patch, commons, search, ...).

## Datasets

All curated + snapshotted data lives in `src/data/*.json` (and a few `.ts`). Validated by
`npm run validate:data`.

## Quality gates

```bash
npm run typecheck
npm test            # 272 tests
npm run validate:data
```

## License

MIT — see LICENSE. Free to use, modify, and ship in hackathon projects; credit appreciated.