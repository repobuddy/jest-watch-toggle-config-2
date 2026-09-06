Please visit the [Releases page](https://github.com/jest-community/jest-watch-toggle-coverage/releases) for changelogs.

## 3.0.0

### Major Changes

- dc81149: Ship ESM only.
  
  The package is now `"type": "module"`; `src/index.js` uses `import` and
  `export default` instead of `require` and `module.exports`. The default export is
  what jest's `requireOrImportModule` reads off an imported namespace.
  
  **Migration**
  
  - Requires **jest >= 28**. Jest has loaded ESM watch plugins since 27, but it
    resolves the plugin path with the default `require`/`node`/`default` conditions
    and only honours `exports` from 28 — so the exports map deliberately points its
    `default` condition at the ESM entry, and jest 27 and older are no longer supported.
  - `require('jest-watch-toggle-config-2')` no longer works. Configure the plugin by
    name in `watchPlugins` as before; jest imports it for you.

### Patch Changes

- 9f3354f: Declare a supported Node range: `^20.19.0 || ^22.13.0 || >=24`.
  
  Every version in that range has unflagged `require(esm)`, so a CommonJS consumer's
  `require()` of this now-ESM-only package resolves rather than throwing `ERR_REQUIRE_ESM`.
  Node 18 (EOL April 2025) and Node 20.0–20.18 are excluded because `require()` hard-fails there.

## 2.1.1

### Patch Changes

- aa40c3e: Declare `jest-validate` as a runtime dependency. It has always been `require`d by
  the plugin but was resolved by accident through a hoisted `node_modules`; on a
  strict, non-hoisted layout (pnpm, or yarn PnP) the require fails.
  
  Stop shipping repository metadata in the tarball. Previous releases published
  `.github/`, `.vscode/` and `.changeset/`; the package now ships only `src/`, the
  README, the license and the changelog.
  
  Point `repository` and `bugs` at this fork rather than the upstream repository.

## 2.1.0

### Minor Changes

- 23d5832: Remove `jest-validate` from peer dependency.
