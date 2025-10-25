# 📜 Zusätzliche Zertifikate

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

# 📜 Additional Certificates

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
