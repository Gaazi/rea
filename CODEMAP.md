# Code Map

REA: one MCP server for reverse engineering across binaries, applications and runtime
behavior. TypeScript monorepo driven by turbo.

- `src/` — product source; `tests/` — vitest suites (boundary, acceptance, conformance).
- `bridge/`, `native/`, `third_party/`, `patches/` — native bridges and integrated third-party parts.
- `scripts/` — build, verification and CI helpers; the maintained commands are the
  `package.json` scripts (`build`, `check`, `check:fast`, `test:run`, `verify:*`).
- `docs/` — VitePress documentation; `website/` — site; `examples/` — sample inputs.
- `assets/`, `licenses/` — static assets and third-party notices.
- Config: `package.json`, `turbo.json`, `tsconfig*.json`, `vitest*.config.ts`,
  `.oxlintrc.json`, `.oxfmtrc.json`, `knip*.json`, `.jscpd.json`.
