# Project State

Updated: 2026-10-31 11:05

## Done

- `dev` was rebased onto upstream `main` (`ec107022f`, 2026-10-31) and carries
  only two local commits: the review notes and the shared-agent sync pointers.
- Reviewed the previous snapshot (`5d6029ea6`): all required upstream CI checks
  passed there; `tsc --noEmit` and 80/82 focused tests passed locally.
- Found and reproduced one defect in that snapshot: Android lists a known ZIP
  symlink in `unavailable_components` and reports `coverage.status: "partial"`.
  Harmony was fixed upstream in `553f19590` (#7886); Android was not.
- Built the shareable Windows application in a separate repository,
  `Gaazi/rea-reverse-engineer`: `rea.exe` launcher, embedded Node.js runtime,
  published `rea-agents` 6.8.0 with production dependencies, SHA-256 manifest
  and `rea.exe verify`. Smoke test, tamper detection and the minified build pass.

## Pending

- The Android symlink asymmetry is still unfixed here; it needs a fork because
  this clone has no push access to `morluto/rea`.
- `native/windows/build/manifest.json` is absent, so `npm run test:focused`
  refuses to run on this host; direct `vitest run` works.
- Two focused tests remain host-blocked: Windows symlink `EPERM` and a missing
  `dist/` for the CLI/MCP acceptance lane.

## Next Step

- Stop changing REA source here. Further application work happens in
  `Gaazi/rea-reverse-engineer`; decide separately whether to propose the
  Android fix upstream from a fork.
