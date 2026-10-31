# Project State

Updated: 2026-10-31 15:05

## Done

- `dev` was rebased onto upstream `main` (`ec107022f`, 2026-10-31) and carries
  only the local review notes and shared-agent sync pointers.
- Reviewed the previous snapshot (`5d6029ea6`): all required upstream CI checks
  passed there; `tsc --noEmit` and 80/82 focused tests passed locally.
- Found and reproduced one defect: Android listed a known ZIP symlink in
  `unavailable_components` and reported `coverage.status: "partial"`.
  Harmony had the same asymmetry fixed in `553f19590` (#7886); Android did not.
- Fixed it on `fix/android-unavailable-symlinks` and pushed to the fork
  `Gaazi/rea`. Draft PR: https://github.com/morluto/rea/pull/8286
- Follow-up refactor in the same branch: `projectedContentEntries` and
  `projectedUnavailableComponents` now own the "file/slice carries content"
  rule for Android, Harmony and Apple.
- Built the shareable Windows application in `Gaazi/rea-reverse-engineer`
  (private): `rea.exe` launcher, embedded Node.js runtime, published
  `rea-agents` 6.8.0, SHA-256 manifest, `npm run check`, and an
  `AGENT_COMMANDS.md` sheet that agents read instead of exploring the tree.

## Pending

- `morluto/rea` denies push to this account (403); all work goes through the
  `Gaazi/rea` fork.
- `native/windows/build/manifest.json` is absent, so `npm run test:focused`
  refuses to run on this host; direct `vitest run` works.
- CLI/MCP acceptance lanes need a built `dist/`, which this checkout lacks.

## Next Step

- Wait for maintainer review on #8286. Do not change REA source here for the
  application; that work belongs in `Gaazi/rea-reverse-engineer`.
- Decide whether to freeze this folder for agents (permission deny and/or
  read-only ACL); not applied yet.
