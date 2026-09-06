---
'jest-watch-toggle-config-2': major
---

Ship ESM only.

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
