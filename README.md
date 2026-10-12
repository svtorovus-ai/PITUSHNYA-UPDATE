# PITUSHNYA-UPDATE

Публічне сховище оновлень PITUSHNYA: тут лежать інсталятори та файли, за якими встановлені програми дізнаються про нову версію.

> [!IMPORTANT]
> Це **не source repository**. Перед зміною manifests або release assets прочитай [00_READ_FIRST.md](00_READ_FIRST.md), [AGENTS.md](AGENTS.md) і [docs/PROJECT_GUIDE.md](docs/PROJECT_GUIDE.md).

## Що тут опубліковано зараз

| Що | Версія | Manifest | Release tag | Файл |
|---|---|---|---|---|
| PITUSHNYA MCC для Windows, стабільна | 1.1.44 | `version.json` | `pitushnya` | `PITUSHNYA_MCC_Setup.exe` |
| PITUSHNYA MCC для Windows, бета | 1.1.44-beta.28 | `beta-version.json` | `pitushnya-beta` | `PITUSHNYA_MCC_Setup.exe` |
| PITUSHNYA Mobile для Android | 1.0.21 | `mobile-version.json` | `pitushnya-mobile` | `PITUSHNYA-Mobile.apk` |

Release `БЕКаП` — резервна копія перевіреного інсталятора. Це не канал оновлень, його не можна використовувати для інших цілей.

## Чим бета відрізняється від стабільної

Стабільна — перевірена версія для щоденної роботи на ПК.

Бета містить усе зі стабільної і додає нове:

- **керування з телефона** (PITUSHNYA Mobile): трансляція обраної області екрана, скріни з позначками, майстер цілі, перевірка і надсилання готового тексту; телефон і ПК мають бути в одній мережі Wi-Fi, усю роботу виконує ПК;
- **чат для подачі**: програма сама відкриває потрібний чат Signal перед вставкою;
- **розсилку Signal**: пересилання повідомлень із вкладеннями між обраними чатами, з умовами для кожного каналу;
- **режими подачі в майстрі цілі**: «Розвідка», «Коригування», «Ураження»; нові режими збираються з полів, які налаштовує користувач, з каталогом засобів і боєприпасів;
- **режим «тільки з буфера»**: робота без прив'язки Signal;
- оновлену довідку «Інфо», списки чатів із пошуком, масштабування інтерфейсу, прев'ю майстра.

Бета виходить частіше і проходить менше перевірок. Канал оновлень перемикається в налаштуваннях програми; дані й прив'язка Signal при цьому зберігаються.

## Як встановити

- **Windows.** Завантажте `PITUSHNYA_MCC_Setup.exe` з потрібного release ([стабільна](../../releases/tag/pitushnya) або [бета](../../releases/tag/pitushnya-beta)) і запустіть. Далі програма оновлюється сама зі свого каналу.
- **Android.** Найпростіше — з бета-версії для Windows: вікно «Remote 4 Android» показує QR-код для встановлення і підключення. APK також лежить у release [pitushnya-mobile](../../releases/tag/pitushnya-mobile). Потрібна PITUSHNYA MCC 1.1.44-beta.28 або новіша. Далі додаток оновлюється сам.

Як користуватися кожною функцією, описано у вкладці «Інфо» програми.

## Source repositories

- Windows stable source: `svtorovus-ai/PITUSHNYA-MCC`
- Mobile/Beta development: `svtorovus-ai/Pitushnya-Mobile`

## Три окремі контракти

Імена manifests, tags і файлів із таблиці вище зашиті у встановлені програми; їх не можна перейменовувати чи змішувати. Android має власний контракт і не використовує Windows manifests/tags.

`mobile-version.json` додатково містить `versionCode` і `sha256`: додаток перевіряє завантажений APK перед встановленням.

## Publication rule

Upload and verify the actual asset first. Update the manifest second. A manifest pointing to a missing/broken asset is a broken release even if source CI was green.
