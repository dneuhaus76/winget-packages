# winget-packages
## requirements
- GitHub-Account, um das Repository zu hosten.
- GitHub CLI (optional), um die Repository-Verwaltung zu erleichtern.
- YAML-Kenntnisse, um Paketdefinitionen zu erstellen.

## Schritt 1: Repository ersetellen
z.B. bei Github

## Schritt 2: Erstellen von Paket-Manifests (YAML-Dateien)
Winget benötigt für jedes Paket eine YAML-Datei, die das Paket beschreibt.

Erstelle im Repository eine Verzeichnisstruktur wie folgt:

```
winget-packages/
├───manifests/
│   ├───Paketname/
│       └───Version/
│           └───Paketname.Version.yaml
```

Erstelle eine .yaml-Datei für jedes Paket mit folgendem Beispielinhalt:

```
Id: MeinUnternehmen.MeineApp
Name: Meine App
Version: 1.0.0
Publisher: Mein Unternehmen
InstallerType: exe
Installers:
  - Architecture: x64
    InstallerUrl: https://meinunternehmen.com/download/meineapp.exe
    InstallerSha256: <SHA256-Wert>
```

Berechne den SHA-256-Hash der Installationsdatei:
>Get-FileHash -Algorithm SHA256 -Path "PfadZurInstallationsdatei"

## Schritt 3: Veröffentlichen des Repositories
1. Push die Änderungen ins GitHub-Repository.
2. Optional kannst du CI/CD-Pipelines wie GitHub Actions konfigurieren, um automatisch neue Releases zu bauen und die YAML-Dateien zu validieren.

## Schritt 4: Verwenden des eigenen Repositories mit Winget
Um dein eigenes Repository mit Winget zu nutzen, musst du es lokal hinzufügen:

1. Führe folgendes PowerShell-Kommando aus, um das Repository hinzuzufügen:
>winget source add -n "MeinRepo" -a "https://github.com/DeinGitHubBenutzer/winget-packages"

2. Stelle sicher, dass dein Repository richtig hinzugefügt wurde:
>winget source list

## Schritt 5: Installieren eines Pakets
Sobald das Repository hinzugefügt ist, kannst du Pakete installieren, wie du es mit dem offiziellen Winget Repository tun würdest:
>winget install MeinUnternehmen.MeineApp

## z.B. In Microsoft ist es so eingerichtet
https://github.com/microsoft/winget-pkgs/tree/master/manifests/7/7zip/7zip
