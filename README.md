# NW.js Patches

Understand how NW.js changes upstream behaviour.

## Versions

- NW: 0.102.1
- Chromium: 139.0.7258.128
- Node: 24.5.0
- V8: 13.9.205.19

## Patching process

1. Go to https://github.com/nwjs/nw.js and find the latest NW.js and Chromium version being used.
1. Go to https://github.com/nwjs/node to find latest Node.js version being used
1. Go to https://github.com/nwjs/v8/blob/main/include/v8-version.h and find the latest version being used
1. Update the versions in `.github/patch` from line 3 to 16.
1. Also update the `Versions` header above accordingly.
1. Create a commit/pull request and after around 10 minutes the changes should be reflected in the repo.
