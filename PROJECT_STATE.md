# Project State

Updated: 2026-10-31 10:15

## Done

- Reviewed the five latest `dev`/`main` commits at `5d6029ea6` (Apple bundle
  anatomy, launchd domains, mobile component/unavailable/runtime-hint fixes).
  Upstream required CI checks all passed on that commit (38 check runs).
- Installed the locked toolchain (`npm ci`, 540 packages) and verified the
  local copy: `tsc --noEmit` passes; 80 of 82 focused application-projection
  tests pass.
- Found one real defect in the snapshot: Android counts a known ZIP symlink as
  an unavailable component and downgrades `coverage.status` to `partial`
  (reproduced with a symlink APK). Harmony had the same defect; upstream fixed
  Harmony in `553f19590` (#7886, issue #7545) but Android still does it.

## Pending

- Local clone is 2,675 commits behind `origin/main` (local HEAD 2026-10-17,
  upstream 2026-10-31); no fetch since the clone.
- Two focused tests are environment-blocked on this host: a boundary test needs
  Windows symlink privilege (EPERM) and a CLI/MCP acceptance test needs `dist/`
  (not built).
- `native/windows/build/manifest.json` is absent, so the `test:focused` gate
  refuses to run; direct `vitest run` works.
- Uncommitted agent-sync files (`.agents/global-sync.json`, `CLAUDE.md`,
  `GEMINI.md`, `.clinerules`, `.roo/`, `.kilocode/`, `copilot-instructions.md`)
  plus the `AGENTS.md` pointer and `.trash/` ignore rule are not committed.

## Next Step

- Decide whether to fetch/update to upstream `main`, and whether to fix the
  Android unavailable-symlink asymmetry with a regression test.
