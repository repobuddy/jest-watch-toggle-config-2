Please visit the [Releases page](https://github.com/jest-community/jest-watch-toggle-coverage/releases) for changelogs.

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
