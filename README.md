# PITUSHNYA-UPDATE

Public distribution/update repository for PITUSHNYA.

> [!IMPORTANT]
> Це **не source repository**. Перед зміною manifests або release assets прочитай [00_READ_FIRST.md](00_READ_FIRST.md), [AGENTS.md](AGENTS.md) і [docs/PROJECT_GUIDE.md](docs/PROJECT_GUIDE.md).

## Source repositories

- Windows stable source: `svtorovus-ai/PITUSHNYA-MCC`
- Mobile/Beta development: `svtorovus-ai/Pitushnya-Mobile`

## Windows update contracts

| Channel | Manifest | Fixed release tag | Asset |
|---|---|---|---|
| stable | `version.json` | `pitushnya` | `PITUSHNYA_MCC_Setup.exe` |
| beta | `beta-version.json` | `pitushnya-beta` | `PITUSHNYA_MCC_Setup.exe` |

Backup release tag `БЕКаП` is not an update channel and must not be repurposed casually.

## Android Mobile

Android PITUSHNYA Mobile uses a separate planned contract:
- `mobile-version.json`
- tag `pitushnya-mobile`
- `PITUSHNYA-Mobile.apk`

Do not reuse Windows manifests/tags for Android.

## Publication rule

Upload and verify the actual asset first. Update the manifest second. A manifest pointing to a missing/broken asset is a broken release even if source CI was green.
