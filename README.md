# NW.js Patches

Understand how NW.js changes upstream behaviour.

## Versions

- NW: 0.119.2
- Chromium: 156.0.8078.48
- Node: 26.12.1
- V8: 15.6.75.19

## Patching process

[`.github/patch`](.github/patch) clones NW.js's forks of [Chromium](https://github.com/nwjs/chromium.src), [Node.js](https://github.com/nwjs/node) and [V8](https://github.com/nwjs/v8) (at the `nw-v<version>` tag if there is one, otherwise `main`), downloads the matching upstream release sources, and writes the difference to `patches/<project>.patch` with `git diff --no-index`. Files added by NW.js are included in full and files it removes are listed without their contents. The script fails without writing patches if either tree's version does not match the pinned version, for example when NW.js's `main` has already moved past or not yet reached a release.

The [`release`](.github/workflows/release.yml) workflow runs on every push to `main`, daily at 00:00 UTC, and manually via `workflow_dispatch`. It:

1. Checks https://nwjs.io/versions.json for a new NW.js release and reads its Chromium and Node.js versions.
1. Reads the V8 version from https://github.com/nwjs/v8/blob/main/include/v8-version.h.
1. If the versions in `.github/patch` are not the latest, updates them and the `Versions` header above (see [`.github/bump`](.github/bump)), regenerates the patches, and opens a pull request on the `patches/nw-<version>` branch.

The [`patch`](.github/workflows/patch.yml) workflow runs on every pull request to `main`. It regenerates the patches from the versions in `.github/patch` and commits them to the pull request branch if they changed. Pull requests opened by the `release` workflow do not trigger it, so that workflow generates the patches itself.
