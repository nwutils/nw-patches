# NW.js Patches

Understand how NW.js changes upstream behaviour.

## Versions

- NW: 0.111.1
- Chromium: 148.0.7778.97
- Node: 25.9.0
- V8: 14.8.178.14

## Patching process

The [`release`](.github/workflows/release.yml) workflow runs every 24 hours (or manually via `workflow_dispatch`). It:

1. Checks https://nwjs.io/versions.json for a new NW.js release and reads its Chromium and Node.js versions.
1. Reads the V8 version from https://github.com/nwjs/v8/blob/main/include/v8-version.h.
1. Updates the versions in `.github/patch` and the `Versions` header above (see [`.github/bump`](.github/bump)).
1. Regenerates the patches and opens a pull request on the `patches/nw-<version>` branch.

To update manually, run `bash .github/bump` (or edit the versions in `.github/patch` and above by hand) and push to `main`; the [`patch`](.github/workflows/patch.yml) workflow regenerates the patches.
