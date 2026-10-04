# PITUSHNYA-UPDATE — distribution map

## Relationship

```text
PITUSHNYA-MCC source
       ↓ release workflow
PITUSHNYA-UPDATE
       ↓ manifests/assets
installed Windows clients
```

Mobile:
```text
Pitushnya-Mobile source
       ↓
Windows beta uses existing beta channel
Android uses separate mobile channel
```

## Current Windows state

Stable:
- version 1.1.44
- manifest `version.json`
- tag `pitushnya`
- URL ends `/pitushnya/PITUSHNYA_MCC_Setup.exe`.

Beta:
- version 1.1.44-beta.1
- manifest `beta-version.json`
- tag `pitushnya-beta`
- URL ends `/pitushnya-beta/PITUSHNYA_MCC_Setup.exe`.

Backup:
- tag `БЕКаП`
- separate from updater.

## Why fixed distribution tags

Installed clients can keep a stable URL while release workflow replaces asset and manifest version.

Do not create a new distribution tag for every update unless updater design is intentionally changed.

Source repo can still have versioned source tags such as `v1.1.44`.

## Two-phase publish

Asset first, manifest second.

Reason: manifest is discovery pointer. If manifest leads, clients can discover an unavailable/corrupt build.

## Beta version bump

Replacing beta asset while keeping identical version string does not make installed same-version beta see a newer version.

New beta build should bump prerelease number while retaining fixed `pitushnya-beta` distribution tag.

## Future Android Mobile

Reserved names:
- `mobile-version.json`;
- `pitushnya-mobile`;
- `PITUSHNYA-Mobile.apk`.

This is additive. Existing Windows contracts remain untouched.

## Recovery

If bad manifest is published:
1. stop further writes;
2. identify last known good asset/manifest;
3. verify asset hash/installer;
4. restore correct manifest;
5. verify raw GitHub URL;
6. verify client behavior.

Do not repurpose `БЕКаП` casually during incident response.
