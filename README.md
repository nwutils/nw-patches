# NW.js Patches

Understand how NW.js changes upstream behaviour.

## Versions

- NW: 0.118.0
- Chromium: 155.0.8059.40
- Node: 26.7.0
- V8: 15.5.35.20

## Patching process

The [`release`](.github/workflows/release.yml) workflow runs on every push to `main`, every 24 hours, and manually via `workflow_dispatch`. It:

1. Checks https://nwjs.io/versions.json for a new NW.js release and reads its Chromium and Node.js versions.
1. Reads the V8 version from https://github.com/nwjs/v8/blob/main/include/v8-version.h.
1. If the versions in `.github/patch` are not the latest, updates them and the `Versions` header above (see [`.github/bump`](.github/bump)) and opens a pull request on the `patches/nw-<version>` branch.
1. Generates the patches and commits them to that pull request. Patches are never generated on `main`.
