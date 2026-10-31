## 2026-10-31 15:05 - Android symlink fix + draft PR (OpenCode, DeepSeek V4.1 Flash Free)

- Branch fix/android-unavailable-symlinks from origin/main ec107022f; pushed to
  fork Gaazi/rea. Draft PR https://github.com/morluto/rea/pull/8286.
- Commit ee5743d59: Android selects file and slice occurrences before building
  unavailable_components; new APK-with-symlink control fails before the change
  and passes after it.
- Commit 4877c3f2f: shared projectedContentEntries /
  projectedUnavailableComponents helpers now serve Android, Harmony and Apple.
- Checks: Android boundary 12/12, shared + Harmony 46/46, Apple 63 passed with
  two host EPERM symlink failures, tsc --noEmit, oxlint, module boundaries.
- App repo Gaazi/rea-reverse-engineer: added AGENT_COMMANDS.md, AGENTS.md,
  scripts/check.mjs and npm run check; pushed to main.
