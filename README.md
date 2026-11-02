# Гибрид Сейф — сайт + Android қосымша

Бұл ZIP ішінде **жүктелген HTML сайты**, **GitHub Pages үшін PWA**, және **Android APK жинауға арналған Android Studio жобасы** бар.

## 1. GitHub-қа жүктеу
1. GitHub-та жаңа **public repository** жасаңыз (мысалы, `gibrid-seif`).
2. ZIP-ті ашыңыз. Ішіндегі **барлық файлдар мен папкаларды** репозиторийдің түбіріне жүктеңіз (ZIP-тің сыртқы папкасын жеке салмаңыз).
3. `Settings → Pages → Build and deployment → Deploy from a branch` таңдаңыз. Branch: `main`, folder: `/docs`, Save.
4. Сайт: `https://СІЗДІҢ-ЛОГИН.github.io/gibrid-seif/` (нақты URL-ді Pages көрсетеді).
5. Android Chrome браузерінен сайтты ашып, менюдегі **Add to Home screen / Install app** пәрменін таңдаңыз. Қолданба тәрізді жеке терезеде ашылады (PWA).

## 2. GitHub Actions арқылы APK шығару (компьютерге Android Studio орнатпай)
1. GitHub-та репозиторийдің **Actions** бөліміне кіріңіз.
2. **Android APK құрастыру** workflow-ын ашып, **Run workflow** басыңыз (немесе `main` branch-қа push жасаңыз).
3. Жасыл құс белгісі пайда болған соң workflow run парағына өтіңіз, төмендегі **Artifacts → Gibrid-Seif-debug-APK** архивін жүктеңіз.
4. Архив ішінен `app-debug.apk` алыңыз, Android телефонға орнатыңыз. Бұл тестілеуге арналған debug APK, Play Store релизі емес.

## 3. Android Studio-да жинау
1. **Open** → `android-app` папкасын таңдаңыз.
2. Gradle Sync біткен соң **Build → Build APK(s)** басыңыз.
3. Файл: `android-app/app/build/outputs/apk/debug/app-debug.apk`.
4. Android SDK 35 және JDK 17 керек. Бастапқы Gradle тәуелділіктерін алу үшін интернет қажет.

## Маңызды
- Сайттың AES/RSA логикасы браузердің **Web Crypto API** арқылы жұмыс істейді, сондықтан HTTPS міндетті. Android нұсқасы жергілікті HTML-ды **WebViewAssetLoader HTTPS origin** арқылы ашады.
- 3D Three.js кітапханасы және Google Fonts **интернеттегі CDN** арқылы алынады. Офлайн кезде 3D көрініс/қаріптер жұмыс істемеуі мүмкін, бірақ криптография зертханасы WebView қолдаса жұмыс істейді.
- Android тексеру үшін **Android System WebView жаңартылған** болуы керек.
- Бұл **оқу демонстрациясы**, дайын қауіпсіз хабарлама алмасу сервері емес. Жеке кілт сессия кезінде жадта сақталады.
- APK осы ортада компиляциядан өткізілген жоқ: ZIP — жинауға арналған толық бастапқы жоба. GitHub Actions қадамдары APK-ны жасайды.
- iPhone үшін APK жарамайды: iPhone-да GitHub Pages веб-қосымшасын Safari арқылы басты экранға қосуға болады.
