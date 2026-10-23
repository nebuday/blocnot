# Блокнот трат и заработка: проект Capacitor

Страница приложения лежит в `www/index.html`. Остальное Capacitor создаст сам.

## Что нужно на компьютере
- Node.js (актуальная LTS-версия)
- Android Studio (вместе с ним ставятся Android SDK и JDK)

## Сборка APK
Открой терминал в этой папке и выполни:

    npm install @capacitor/core @capacitor/android
    npm install -D @capacitor/cli
    npx cap add android
    npx cap sync
    npx cap open android

В Android Studio дождись окончания синхронизации Gradle, затем:
**Build → Build Bundle(s) / APK(s) → Build APK(s)**.

Готовый файл: `android/app/build/outputs/apk/debug/app-debug.apk`.

Без Android Studio, только из терминала (нужны JDK и Android SDK):

    cd android
    ./gradlew assembleDebug      # на Windows: gradlew.bat assembleDebug

## Установка на телефон
Скопируй `app-debug.apk` на телефон и открой его. Android попросит разрешить
установку из этого источника. Debug-APK подходит для личного использования.
Для Google Play нужна подписанная release-сборка (Build → Generate Signed Bundle / APK).

## Если меняешь страницу
Правь `www/index.html`, затем `npx cap sync` и снова собери APK.

## Заметки
- Записи хранятся в памяти приложения на телефоне. Синхронизации между устройствами нет.
- Шрифт Caveat подгружается из интернета. Без сети подставится системный.
- Название и идентификатор пакета меняются в `capacitor.config.json`
  (делай это до `npx cap add android`).
