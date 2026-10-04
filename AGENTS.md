# PITUSHNYA-UPDATE — правила для агентів

## 1. Роль

Repo є public distribution store.

Він НЕ містить канонічний source Windows app.

Source:
- `PITUSHNYA-MCC`;
- Mobile fork `Pitushnya-Mobile`.

Зміна manifests тут впливає на реальні installed clients.

## 2. Stable contract

Manifest:
`version.json`

Distribution tag:
`pitushnya`

Asset:
`PITUSHNYA_MCC_Setup.exe`

На момент аудиту:
version 1.1.44, channel stable.

Не:
- rename manifest;
- rename tag;
- rename asset;
- point stable на beta build;
- replace stable asset випадковим local EXE.

## 3. Beta contract

Manifest:
`beta-version.json`

Distribution tag:
`pitushnya-beta`

Asset:
`PITUSHNYA_MCC_Setup.exe`

На момент аудиту:
1.1.44-beta.1.

Не змішувати з stable.

## 4. Backup

Tag:
`БЕКаП`.

Це резервний перевірений installer.

Він не є update channel.

Не використовувати як temporary upload slot.
Не перезаписувати без прямої команди власника.

## 5. Manifest atomicity

Correct publication:
1. build/smoke installer у source repo;
2. upload installer asset;
3. verify asset URL and size;
4. only then update manifest;
5. verify raw manifest;
6. test installed client update.

Ніколи не оновлюй manifest раніше, ніж asset реально доступний.

## 6. Manifest fields

Windows manifests:
- version;
- channel;
- url;
- notes.

`channel` має відповідати manifest file.

`url` має відповідати fixed tag/asset.

## 7. Installer validation

Source workflow очікує Windows installer >100MB і real executable.

Distribution repo не є місцем для "маленької заглушки" під тим самим asset name.

## 8. Android Mobile — окремий третій контракт

Коли PITUSHNYA Mobile APK реально готовий, він має окремі names:
- manifest `mobile-version.json`;
- tag `pitushnya-mobile`;
- asset `PITUSHNYA-Mobile.apk`.

НЕ використовувати `version.json`, `beta-version.json`, `pitushnya` або `pitushnya-beta` для Android.

Не створювати `mobile-version.json` із фейковим URL до появи реального APK.

## 9. Android manifest

Запланований мінімум:
- version;
- versionCode;
- channel=mobile;
- url;
- sha256;
- minProtocolVersion;
- notes.

Android client повинен verify SHA-256 + Android signing identity through platform update compatibility.

## 10. Secrets

Цей repo public.

НІКОЛИ не комітити:
- update PAT;
- telemetry token;
- signing key;
- Signal profile;
- private config.

Source GitHub Actions пишуть сюди через repository secret/token.

## 11. Release titles не є API

API contract — tag/asset/manifest URL.

Release title можна синхронізувати для людини, але не будувати client parsing на title.

## 12. Якщо source release успішний, а manifest старий

Release chain НЕ завершений.

Не казати "готово", поки distribution asset і manifest не синхронізовані.

## 13. Заборонено

- cleanup old tags без impact analysis;
- force-delete backup;
- stable↔beta swap;
- Android asset під Windows tag;
- manifests з 404;
- manifests з неправильним channel;
- secrets у notes/files.
