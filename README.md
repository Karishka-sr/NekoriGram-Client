## NekoriGram for Android

NekoriGram is a messaging app based on the open-source [Telegram for Android](https://github.com/TelegramOrg/Telegram-Android) client.
It keeps the speed, security and feature set of the original client, with its own branding and package name.

This repository is a **fork**. All credit for the underlying application belongs to the Telegram
open-source project and its contributors — see [Credits and licence](#credits-and-licence) below.

## Creating your NekoriGram Application

We welcome all developers to use this API and source code to create applications on our platform.
There are several things we require from **all developers** for the moment.

1. [**Obtain your own api_id**](https://core.telegram.org/api/obtaining_api_id) for your application.
2. Please **do not** use the Telegram name for your app — or make sure your users understand that it is unofficial.
3. Kindly **do not** use Telegram's standard logo (white paper plane in a blue circle) as your app's logo.
4. Please study our [**security guidelines**](https://core.telegram.org/mtproto/security_guidelines) and take good care of your users' data and privacy.
5. Please remember to publish **your** code too in order to comply with the licences.

### API, Protocol documentation

Telegram API manuals: https://core.telegram.org/api

MTproto protocol manuals: https://core.telegram.org/mtproto

### Compilation Guide

**Note**: In order to support [reproducible builds](https://core.telegram.org/reproducible-builds), this repo contains dummy release.keystore, google-services.json and filled variables inside BuildVars.java. Before publishing your own APKs please make sure to replace all these files with your own.

You will require Android Studio 2025.1.4, Android NDK 27.2.12479018 and Android SDK 36.

1. Clone the NekoriGram source code with its submodules:
   ```bash
   git clone --recursive --shallow-submodules https://github.com/Karishka-sr/NekoriGram-Client.git NekoriGram
   ```
   In case you forgot the `--recursive` flag, change to the `NekoriGram` directory and run:
   ```bash
   git submodule init && git submodule update --init --recursive --depth=1
   ```
2. Copy your release.keystore into TMessagesProj/config
3. Fill out RELEASE_KEY_PASSWORD, RELEASE_KEY_ALIAS, RELEASE_STORE_PASSWORD in gradle.properties to access your release.keystore
4. Go to https://console.firebase.google.com/, create two android apps with application IDs `com.nekori.gram` and `com.nekori.gram.beta`, turn on firebase messaging and download google-services.json, which should be copied to the same folder as TMessagesProj.
5. Open the project in the Studio (note that it should be opened, NOT imported).
6. Fill out values in TMessagesProj/src/main/java/org/telegram/messenger/BuildVars.java – there's a link for each of the variables showing where and which data to obtain.
7. You are ready to compile.

### Localization

We moved all translations to https://translations.telegram.org/en/android/. Please use it.

### Branding

NekoriGram uses its own application ID (`com.nekori.gram`) and its own launcher icon. The
application name and the icons live in the standard Android resources, so they can be changed
without touching the client logic:

- App name: `TMessagesProj/src/main/res/values/strings.xml` (`AppName`)
- Application ID: `APP_PACKAGE` in `gradle.properties`
- Launcher icons: `TMessagesProj/src/main/res/mipmap-*` and `TMessagesProj_AppStandalone/src/main/res/mipmap-*`
- Monochrome (themed) icon: `TMessagesProj/src/main/res/drawable/icon_cat.xml`

### Credits and licence

NekoriGram is based on the Telegram for Android open-source client:
https://github.com/TelegramOrg/Telegram-Android

The original application, its API and protocol documentation are the work of the Telegram
project and its contributors. NekoriGram is not affiliated with or endorsed by Telegram.

This project is distributed under the GNU General Public License, version 2 — see [LICENSE](LICENSE).
As required by the licence, the full corresponding source code is published in this repository.
