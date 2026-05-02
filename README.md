# NW.js Patches

Understand how NW.js changes upstream behaviour.

## Versions

- NW: 0.111.1
- Chromium: 148.0.7778.97
- Node: 25.9.0
- V8: 14.8.178.14

## Patching process

1. Go to https://github.com/nwjs/nw.js and find the latest NW.js and Chromium version being used.
1. Go to https://github.com/nwjs/node to find latest Node.js version being used
1. Go to https://github.com/nwjs/v8/blob/main/include/v8-version.h and find the latest version being used
1. Update the versions in `.github/patch` from line 3 to 16.
1. Also update the `Versions` header above accordingly.
1. Create a commit/pull request and after around 10 minutes the changes should be reflected in the repo.
