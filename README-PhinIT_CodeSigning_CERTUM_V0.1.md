# 🔐 PhinIT CERTUM Code Signing & EXE Creator

GUI-Tool zum Signieren von PowerShell-Skripten und Konvertieren zu signierten EXE-Dateien mit CERTUM Code Signing Zertifikaten.

GUI tool for signing PowerShell scripts and converting them to signed EXE files using CERTUM Code Signing certificates.

![PhinIT CERTUM Code Signing Tool](https://github.com/PS-easyIT/PowerShell_Certificate/blob/main/Screenshot_PhinIT%20CERTUM%20Code%20Signing%20%26%20EXE%20Creator%20V1.jpg)

---

## 📚 Inhalt / Table of Contents

- [🇩🇪 Deutsch](#-deutsch)
  - [✨ Features](#-features)
  - [📋 Voraussetzungen](#-voraussetzungen)
  - [🚀 Installation](#-installation)
  - [💡 Verwendung](#-verwendung)
  - [⚙️ Einstellungen](#️-einstellungen)
  - [🔧 Trust-Installation](#-trust-installation)
- [🇬🇧 English](#-english)
  - [✨ Features](#-features-1)
  - [📋 Requirements](#-requirements)
  - [🚀 Installation](#-installation-1)
  - [💡 Usage](#-usage)
  - [⚙️ Settings](#️-settings)
  - [🔧 Trust Installation](#-trust-installation)
- [🔐 Sicherheitshinweis / Security Notice](#-sicherheitshinweis--security-notice)

---

## 🇩🇪 Deutsch

### ✨ Features

**Code Signing:**
- ✅ PowerShell-Skripte signieren (PS1)
- ✅ EXE-Dateien signieren
- ✅ CERTUM Cloud Code Signing Support
- ✅ Timestamp-Server Integration (CERTUM)
- ✅ Signatur-Status-Anzeige

**EXE-Konvertierung:**
- ✅ PowerShell zu EXE mit PS2EXE
- ✅ Automatische Icon-Integration
- ✅ GUI/Console-Modus wählbar
- ✅ Administrator-Rechte konfigurierbar
- ✅ CPU-Architektur (x86/x64/AnyCPU)
- ✅ Versionsinformationen einbettbar

**Trust-Management:**
- ✅ Automatische Trust-Installation für signierte Skripte
- ✅ Lösung für "nicht vertrauenswürdig" Problem
- ✅ Administrator-Privilegien-Erkennung
- ✅ Self-Elevation Support

**Benutzerfreundlichkeit:**
- ✅ Moderne GUI mit Segoe UI Design
- ✅ Vereinfachte Dateiauswahl (Browse-Button)
- ✅ Registry-basierte Einstellungsspeicherung
- ✅ Detaillierte Statusmeldungen
- ✅ Integriertes Logging

---

### 📋 Voraussetzungen

**Erforderlich:**
- Windows 10/11 oder Windows Server 2016+
- PowerShell 5.1 oder höher
- .NET Framework 4.x
- CERTUM Code Signing Zertifikat (installiert in `Cert:\CurrentUser\My`)

**Optional:**
- SimplySign Desktop App (für Cloud-Zertifikate)
- PS2EXE Modul oder Script (für EXE-Konvertierung)
- Administrator-Rechte (für Trust-Installation)

**CERTUM Zertifikat:**
- Code Signing Zertifikat von CERTUM
- Installiert im persönlichen Zertifikatspeicher
- Gültig und nicht abgelaufen

---

### 🚀 Installation

**1. Repository klonen oder herunterladen:**
```powershell
git clone https://github.com/PS-easyIT/PowerShell_Certificate.git
cd PowerShell_Certificate
```

**2. PS2EXE installieren (für EXE-Konvertierung):**
```powershell
# Via PowerShell Gallery:
Install-Module PS2EXE -Scope CurrentUser

# Oder manuell:
# Lade ps2exe von https://github.com/MScholtes/PS2EXE
# Entpacke in den Ordner: PowerShell_Certificate\ps2exe\
```

**3. Tool starten:**
```powershell
# Als PowerShell-Script:
.\PhinIT_CodeSigning_CERTUM_V0.1.ps1

# Oder als EXE (wenn kompiliert):
.\PhinIT_CodeSigning_CERTUM_V0.1.exe
```

**Empfohlen:** Als Administrator starten für vollständige Trust-Verwaltung!

---

### 💡 Verwendung

**Schritt 1: Datei auswählen**
1. Klicke auf **"DATEI AUSWÄHLEN"**
2. Navigiere zu deiner PowerShell-Datei (.ps1)
3. Ausgewählte Datei wird angezeigt

**Schritt 2: Zertifikat auswählen**
1. Wähle dein CERTUM Code Signing Zertifikat aus der Dropdown-Liste
2. Optional: Deaktiviere "Timestamp Server" (nicht empfohlen)
3. Klicke auf "Aktualisieren" um Zertifikatsliste zu erneuern

**Schritt 3: Aktion wählen**

**PowerShell signieren:**
- Klicke auf **"PowerShell SIGNIEREN"**
- Signatur wird mit Timestamp erstellt
- Status wird in der Info-Box angezeigt

**PowerShell zu EXE konvertieren:**
- Klicke auf **"PowerShell zu EXE"**
- PS2EXE konvertiert die Datei
- EXE wird automatisch ausgewählt
- Optional: EXE anschließend signieren

**EXE signieren:**
- Wähle eine EXE-Datei aus
- Klicke auf **"EXE SIGNIEREN"**
- Signatur wird mit Timestamp erstellt

**SimplySign verbinden:**
- Klicke auf **"SimplySign"** für Cloud-Zertifikate
- Automatische Verbindung zur SimplySign Desktop App

---

### ⚙️ Einstellungen

Klicke auf **"Einstellungen"** im Header für erweiterte Optionen:

**Tab: Pfade**
- **PS2EXE Ordner:** Pfad zum PS2EXE Script/Modul
- **Standard-Ordner:** Startverzeichnis beim Öffnen
- **Icon-Datei:** Standard-Icon für EXE-Dateien

**Tab: Anwendung**
- **Autor:** Dein Name (für EXE-Metadaten)
- **Firma:** Firmenname
- **Produkt:** Produktname
- **Copyright:** Copyright-Text
- **Version:** Versionsnummer (z.B. 1.0.0.0)

**Tab: Optionen**
- **Administrator-Rechte:** EXE benötigt Admin-Rechte
- **Konsolen-Fenster ausblenden:** GUI-Modus (keine Console)
- **CPU-Architektur:** AnyCPU, x86 oder x64
- **Timestamp Server:** CERTUM Timestamp-URL

Alle Einstellungen werden in der Registry gespeichert: `HKCU:\Software\easyIT\PSS2ES`

---

### 🔧 Trust-Installation

**Problem:** Signierte PowerShell-Skripte werden als "nicht vertrauenswürdig" eingestuft

**Lösung:** Das Tool installiert automatisch das Code Signing Zertifikat als vertrauenswürdigen Publisher

**Voraussetzungen:**
- Administrator-Rechte erforderlich
- CERTUM Zertifikat muss ausgewählt sein

**Automatische Installation:**
1. Starte das Tool als Administrator
2. Wähle dein CERTUM Zertifikat aus
3. Signiere eine Datei
4. Das Zertifikat wird automatisch in `LocalMachine\TrustedPublisher` installiert

**Ergebnis:**
- Signierte Skripte werden ohne Warnung ausgeführt
- Gilt systemweit für alle Benutzer
- Keine "nicht vertrauenswürdig" Meldungen mehr

**Manuelle Prüfung:**
```powershell
# Zertifikat im TrustedPublisher Store prüfen:
Get-ChildItem Cert:\LocalMachine\TrustedPublisher
```

---

### 📜 Zusätzliche Zertifikate

Für die Verwendung von signierten Skripten aus den PhinIT easyIT Projekten:

**Enthaltene Dateien:**
- `OpenSource_CERTUM_Certificate.cer`  
  → Öffentliches CERTUM Zertifikat zum Import in den Zertifikatspeicher

- `PhinIT_TrustetScripts.ps1`  
  → PowerShell-Skript zum automatisierten Hinterlegen des Zertifikats  
  **Hinweis:** Skript **immer mit Admin-Rechten** ausführen!

**Manuelle Einrichtung:**
1. Lade `OpenSource_CERTUM_Certificate.cer` herunter
2. Starte `mmc.exe` → Snap-In *Zertifikate (Lokaler Computer)* hinzufügen
3. Importiere das Zertifikat in **beide Speicherorte**:
   - **Vertrauenswürdige Herausgeber** → Zertifikate
   - **Vertrauenswürdige Stammzertifizierungsstellen** → Zertifikate

**Automatisierter Import:**
```powershell
# Als Administrator ausführen:
.\PhinIT_TrustetScripts.ps1
```

Das Skript prüft die erforderlichen Speicherorte und importiert das Zertifikat für den lokalen Computerkontext.

---

## 🇬🇧 English

### ✨ Features

**Code Signing:**
- ✅ Sign PowerShell scripts (PS1)
- ✅ Sign EXE files
- ✅ CERTUM Cloud Code Signing support
- ✅ Timestamp server integration (CERTUM)
- ✅ Signature status display

**EXE Conversion:**
- ✅ PowerShell to EXE with PS2EXE
- ✅ Automatic icon integration
- ✅ GUI/Console mode selectable
- ✅ Administrator rights configurable
- ✅ CPU architecture (x86/x64/AnyCPU)
- ✅ Embeddable version information

**Trust Management:**
- ✅ Automatic trust installation for signed scripts
- ✅ Solution for "not trusted" problem
- ✅ Administrator privilege detection
- ✅ Self-elevation support

**User Experience:**
- ✅ Modern GUI with Segoe UI design
- ✅ Simplified file selection (Browse button)
- ✅ Registry-based settings storage
- ✅ Detailed status messages
- ✅ Integrated logging

---

### 📋 Requirements

**Required:**
- Windows 10/11 or Windows Server 2016+
- PowerShell 5.1 or higher
- .NET Framework 4.x
- CERTUM Code Signing Certificate (installed in `Cert:\CurrentUser\My`)

**Optional:**
- SimplySign Desktop App (for cloud certificates)
- PS2EXE Module or Script (for EXE conversion)
- Administrator rights (for trust installation)

**CERTUM Certificate:**
- Code Signing certificate from CERTUM
- Installed in personal certificate store
- Valid and not expired

---

### 🚀 Installation

**1. Clone or download repository:**
```powershell
git clone https://github.com/PS-easyIT/PowerShell_Certificate.git
cd PowerShell_Certificate
```

**2. Install PS2EXE (for EXE conversion):**
```powershell
# Via PowerShell Gallery:
Install-Module PS2EXE -Scope CurrentUser

# Or manually:
# Download ps2exe from https://github.com/MScholtes/PS2EXE
# Extract to folder: PowerShell_Certificate\ps2exe\
```

**3. Start tool:**
```powershell
# As PowerShell script:
.\PhinIT_CodeSigning_CERTUM_V0.1.ps1

# Or as EXE (if compiled):
.\PhinIT_CodeSigning_CERTUM_V0.1.exe
```

**Recommended:** Run as Administrator for full trust management!

---

### 💡 Usage

**Step 1: Select file**
1. Click **"DATEI AUSWÄHLEN"** (SELECT FILE)
2. Navigate to your PowerShell file (.ps1)
3. Selected file will be displayed

**Step 2: Select certificate**
1. Choose your CERTUM Code Signing certificate from dropdown
2. Optional: Disable "Timestamp Server" (not recommended)
3. Click "Aktualisieren" (Refresh) to update certificate list

**Step 3: Choose action**

**Sign PowerShell:**
- Click **"PowerShell SIGNIEREN"** (SIGN POWERSHELL)
- Signature will be created with timestamp
- Status displayed in info box

**Convert PowerShell to EXE:**
- Click **"PowerShell zu EXE"** (POWERSHELL TO EXE)
- PS2EXE converts the file
- EXE is automatically selected
- Optional: Sign EXE afterwards

**Sign EXE:**
- Select an EXE file
- Click **"EXE SIGNIEREN"** (SIGN EXE)
- Signature will be created with timestamp

**Connect SimplySign:**
- Click **"SimplySign"** for cloud certificates
- Automatic connection to SimplySign Desktop App

---

### ⚙️ Settings

Click **"Einstellungen"** (Settings) in header for advanced options:

**Tab: Paths**
- **PS2EXE Folder:** Path to PS2EXE script/module
- **Default Folder:** Start directory when opening
- **Icon File:** Default icon for EXE files

**Tab: Application**
- **Author:** Your name (for EXE metadata)
- **Company:** Company name
- **Product:** Product name
- **Copyright:** Copyright text
- **Version:** Version number (e.g. 1.0.0.0)

**Tab: Options**
- **Administrator Rights:** EXE requires admin rights
- **Hide Console Window:** GUI mode (no console)
- **CPU Architecture:** AnyCPU, x86 or x64
- **Timestamp Server:** CERTUM timestamp URL

All settings are stored in registry: `HKCU:\Software\easyIT\PSS2ES`

---

### 🔧 Trust Installation

**Problem:** Signed PowerShell scripts are classified as "not trusted"

**Solution:** The tool automatically installs the Code Signing certificate as trusted publisher

**Requirements:**
- Administrator rights required
- CERTUM certificate must be selected

**Automatic Installation:**
1. Start tool as Administrator
2. Select your CERTUM certificate
3. Sign a file
4. Certificate is automatically installed in `LocalMachine\TrustedPublisher`

**Result:**
- Signed scripts run without warning
- Applies system-wide for all users
- No more "not trusted" messages

**Manual Verification:**
```powershell
# Check certificate in TrustedPublisher store:
Get-ChildItem Cert:\LocalMachine\TrustedPublisher
```

---

### 📜 Additional Certificates

For using signed scripts from PhinIT easyIT projects:

**Included Files:**
- `OpenSource_CERTUM_Certificate.cer`  
  → Public CERTUM certificate for importing into certificate store

- `PhinIT_TrustetScripts.ps1`  
  → PowerShell script to automate certificate import  
  **Note:** Always run this script **with administrative privileges**!

**Manual Setup:**
1. Download `OpenSource_CERTUM_Certificate.cer`
2. Start `mmc.exe` → Add *Certificates* snap-in for *Local Computer*
3. Import the certificate into **both stores**:
   - **Trusted Publishers** → Certificates
   - **Trusted Root Certification Authorities** → Certificates

**Automated Import:**
```powershell
# Run as Administrator:
.\PhinIT_TrustetScripts.ps1
```

The script checks the required stores and imports the certificate for the local machine context.

---

## 🔐 Sicherheitshinweis / Security Notice

**Deutsch:**
Dieses Tool verwendet CERTUM Code Signing Zertifikate zum Signieren von PowerShell-Skripten und EXE-Dateien. Die Trust-Installation installiert das Zertifikat systemweit als vertrauenswürdigen Publisher. Verwenden Sie nur vertrauenswürdige Zertifikate!

**English:**
This tool uses CERTUM Code Signing certificates to sign PowerShell scripts and EXE files. Trust installation installs the certificate system-wide as trusted publisher. Only use trusted certificates!

---

## 📝 Lizenz / License

Dieses Projekt ist unter der MIT-Lizenz lizenziert.  
This project is licensed under the MIT License.

---

## 🔗 Links

- **PhinIT easyIT Projects:** [https://github.com/PS-easyIT](https://github.com/PS-easyIT)
- **PS2EXE:** [https://github.com/MScholtes/PS2EXE](https://github.com/MScholtes/PS2EXE)
- **CERTUM:** [https://www.certum.eu/](https://www.certum.eu/)

---

## 👨‍💻 Autor / Author

**Andreas Hepp / PhinIT**  
[GitHub](https://github.com/PS-easyIT) | [Website](https://phinit.de)
