# Kanban Tasks für iOS

Eine iOS-Kanban-App auf Basis von Expo und React Native. Die App speichert Aufgaben lokal und kann mit Google Tasks synchronisiert werden.

## IPA über GitHub Actions bauen

Der Workflow [`.github/workflows/build-ios-ipa.yml`](.github/workflows/build-ios-ipa.yml) erzeugt auf einem macOS-GitHub-Runner eine **unsignierte iOS-IPA**. Sideloadly signiert diese IPA anschließend mit deiner Apple-ID.

1. Erstelle auf GitHub ein neues, leeres Repository (ohne README oder `.gitignore`).
2. Initialisiere das Projekt und lade es hoch:

   ```powershell
   git init
   git add .
   git commit -m "Initial iOS Kanban app"
   git branch -M main
   git remote add origin https://github.com/DEIN-NAME/DEIN-REPOSITORY.git
   git push -u origin main
   ```

3. Öffne im GitHub-Repository **Actions** → **Build Unsigned iOS IPA (Sideloadly / AltStore)** → **Run workflow**.
4. Warte auf den erfolgreichen Lauf und lade unter **Artifacts** `KanbanTasks-unsigned-ipa` herunter. Entpacke das Artifact; darin liegt `KanbanTasks.ipa`.

## Mit Sideloadly installieren

1. Installiere und öffne [Sideloadly](https://sideloadly.io/).
2. Verbinde dein iPhone per Kabel (oder aktiviere nach der ersten Installation WLAN-Synchronisierung in iTunes/Finder).
3. Wähle dein iPhone in Sideloadly aus und ziehe `KanbanTasks.ipa` in das Fenster.
4. Melde dich mit deiner Apple-ID an und starte die Installation.
5. Öffne auf dem iPhone **Einstellungen** → **Allgemein** → **VPN & Geräteverwaltung** und vertraue dem Entwicklerzertifikat.

Mit einer kostenlosen Apple-ID muss die App normalerweise spätestens nach sieben Tagen erneut per Sideloadly signiert werden. Ein kostenpflichtiges Apple-Developer-Konto verlängert die Gültigkeit in der Regel auf ein Jahr.

## Lokal entwickeln

Für die lokale Vorschau wird Node.js (LTS) benötigt:

```powershell
npm install
npm run start
```

Zum Erstellen der IPA ist kein Mac erforderlich: Der GitHub-Workflow übernimmt den iOS-Build auf macOS.
