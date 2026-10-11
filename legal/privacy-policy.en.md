# Privacy Policy for PastPaths

**Version 1.1 — effective from PastPaths 1.9.0**

## Summary

**PastPaths stores all your genealogical research locally on your own computer. Nothing is sent to me or anyone else without you choosing to do so yourself. The program only uses the network when you yourself open the Map page, open the Place Library page or import from it, or import from WordPress (see section 3).**

This document explains in detail what that means.

## 1. Who is responsible for the data?

PastPaths is a local program — it runs on your computer, saves all data on your computer and never sends your genealogical data to me. The only thing the program fetches from a server operated by me is the Place Library packages (see section 3.5).

This means that **you** are the data controller for the genealogical data you enter into the program, not me as its developer. I never handle your genealogical data and cannot access it.

This design is a deliberate choice. It gives you:

- Full control over your data
- Protection from policy changes at a service provider
- Protection should the developer of PastPaths disappear — the data is yours and works in other programs via GEDCOM export

## 2. What is stored, where, and how

### 2.1 What is stored

PastPaths can store:

- Personal data you enter yourself (names, dates, places, notes)
- Photos and documents you upload
- Source citations
- Blog posts and stories
- Settings for the program

### 2.2 Where the data is stored

All data is stored locally on your computer. Currently only Windows is supported as a platform.

The program and your data are in the same folder. Unless you chose a different folder during installation, it is:

- **Windows:** `C:\Users\YOUR_USERNAME\AppData\Local\PastPaths`

The folder contains:

- `pastpaths.db` — an SQLite database with all your genealogical data (people, events, places, relationships, sources, blog posts, etc.). Next to it, the files `pastpaths.db-wal` and `pastpaths.db-shm` may exist. They belong to the database.
- `uploads\` — your uploaded photos and documents in their original format. The subfolder `imports` may contain copies of files you have imported.
- `webview_data\` — the program's own settings (for example the selected language) and a cache where map images, among other things, may be stored.
- `logs\` — the program's log files (see section 2.4).
- `_internal\` and other program files from the installation.

The log files are always located in `C:\Users\YOUR_USERNAME\AppData\Local\PastPaths\logs`, even if you chose a different folder during installation.

If you move or copy the `PastPaths` folder, your entire database and all your files move with it. You can move the entire folder to another computer if you wish. Close PastPaths first, so that the database is complete.

Versions for Linux and Android are planned but not yet released. When they exist, this policy will be updated with their paths.

#### Files outside the program folder

Some features save files elsewhere on your computer. They remain until you delete them yourself, even if you uninstall PastPaths:

- **Backups** that you create on the Import/Export page are saved as ZIP files in `Documents\PastPaths\Backups`. They contain the database and your uploaded files.
- **GEDCOM exports** are saved in `Documents\PastPaths\GEDCOM`.
- **PDF reports** and the family tree PDF are saved in `Documents\PastPaths\Reports`. Reports from earlier versions remain in `Documents\PastPaths\Rapporter`.
- **When you restore a backup**, a copy of the current database is first saved in `Documents\PastPaths-Backups\pre-restore`.
- **The installer's backups** are only created when you upgrade PastPaths, and only if you have chosen to. The backup of the database and uploaded files is selected by default. A full copy of the entire program folder is only made if you select it. You choose the folder yourself. The suggestion is `Documents\PastPaths-Backups`. A new folder with the date and time is created each time. Old copies are never removed automatically.

The Documents folder is the one Windows specifies. If Windows has moved it to OneDrive, the files are saved there and synced to OneDrive.

### 2.3 Login

PastPaths has no login. The program runs locally on your computer and anyone with access to your user account in Windows can start the program and see your genealogical data.

If you need to protect your data from others who have access to the same computer — use disk encryption (see section 9) or separate Windows user accounts.

A future version may introduce optional password protection, but currently security depends on your computer and your Windows user account.

### 2.4 Log files

PastPaths writes a technical log that is used for troubleshooting. It is saved in `C:\Users\YOUR_USERNAME\AppData\Local\PastPaths\logs\pastpaths.log`.

- Among other things, the log contains the program version, paths to the program's folders (which include your Windows username), the number of records in imports, and technical error messages.
- During normal use, no names, search terms or file names are written to the log. When errors occur, however, the log may contain paths to files on your computer.
- The log does not grow indefinitely. When the file reaches 1 MB, it is set aside and a new file is started. At most five files are kept, that is, about 5 MB.
- The log stays on your computer and is never sent anywhere. If you report a bug, you can choose to send it to me yourself.

### 2.5 Uninstalling

When you uninstall PastPaths, you first get to choose whether to also delete data that the program has stored in the program folder:

- **The database** — `pastpaths.db` with its associated files
- **Uploaded files** — the `uploads` folder
- **Log files and app settings** — the `logs` and `webview_data` folders

The database and the uploaded files are never selected by default. Log files and settings are selected by default. Anything left unchecked is kept. If you choose Cancel, the entire uninstallation is cancelled and nothing is removed.

The program files are always removed. Files that PastPaths has saved outside the program folder (see section 2.2) are never removed by the uninstallation. In a silent uninstallation, for example from the command line, no data is deleted.

## 3. The data does not leave your computer — exceptions

PastPaths does not communicate with external servers for normal use.

**Note:** Importing GEDCOM files from programs such as Ancestry, MyHeritage, TNG (The Next Generation), and Disgen happens entirely locally. You export a GEDCOM file yourself from the other program and select that file in PastPaths — the program never contacts these services directly.

The only situations where the program uses the network are:

### 3.1 You import from WordPress

If you import a WordPress export, PastPaths downloads the images from your WordPress site to your local computer. The traffic occurs between your computer and your WordPress server — not via me.

### 3.2 You export and share manually

If you yourself export GEDCOM, create PDF reports, or share images, that is your own active action. PastPaths never sends anything automatically.

### 3.3 Software updates

PastPaths does not automatically check for new versions of the program and does not send any version information anywhere. You need to visit [pastpaths.se](https://pastpaths.se) yourself to see if a newer version is available and, if so, download it.

The Place Library shows whether newer versions of the place packages are available, but only when you yourself open the Place Library page (see section 3.5).

### 3.4 Map feature

If you open the **Map** page, the program fetches map images (so-called *tiles*) from OpenStreetMap's public server (`tile.openstreetmap.org`). The traffic occurs between your computer and OpenStreetMap — not via me. What is sent is the coordinates of the map tile being displayed (i.e., which geographic area you are looking at), your IP address, and standard browser information. No data from your database — neither names, coordinates, nor search terms — is sent onward. The search box on the Map page only filters among already-loaded local places.

PastPaths contains **no geocoding functionality**. Coordinates for places are entered manually or imported from GEDCOM — no calls are made to look up addresses against external services. If you never open the Map page, no requests are sent to OpenStreetMap. Processing at OpenStreetMap is governed by their own [privacy policy](https://wiki.openstreetmap.org/wiki/Privacy_Policy).

### 3.5 The Place Library

The Place Library contains ready-made packages of places, for example the counties of Sweden, that you can import. The packages are hosted on pastpaths.se.

- When you open the **Place Library** page, the program fetches a list of available packages from pastpaths.se.
- When you import a package, the list is fetched again, followed by the package file itself.

What is sent is your IP address, which file is being fetched, and the program's name (`PastPaths-PlaceLibrary/1`). No data from your database is sent. The program does not contact pastpaths.se when it starts. If you never open the Place Library page, no requests are sent.

Like all web servers, the web server for pastpaths.se records technical details about the requests in server logs. This is described on the [website privacy page](https://pastpaths.se/en/website-privacy/).

## 4. Telemetry, statistics, and analytics

**PastPaths does not collect user statistics, anonymous or otherwise.** I do not know how you use the program, how often you start it, or which features you use. I have no "anonymous usage figures" to refer to.

This is a deliberate choice. For genealogical research — where the data is personal and often sensitive — I consider privacy by design more important than product-optimization data.

## 5. Third parties

PastPaths is built on open-source libraries (a list is available in `THIRD-PARTY-LICENSES.md`). These run as part of the program on your computer and do not have separate access to your data.

PastPaths does not integrate with:

- Social media
- Advertising networks
- Tracking services
- External cloud services (beyond what you actively choose yourself)

> *Exception: the map feature contacts OpenStreetMap and the Place Library fetches packages from pastpaths.se, see sections 3.4 and 3.5.*

## 6. Your responsibility for other people's data

When you enter information about relatives — especially currently living relatives — **you** become responsible for that processing under GDPR.

PastPaths helps you by keeping all data local, which carries a lower risk than cloud services.

PastPaths does not hide information about living people in reports or in the GEDCOM export. Keep this in mind before you share a report or an export file.

You need to:

- Consider whether you have a lawful basis to process the data
- Inform the persons concerned to a reasonable extent
- Be careful about what you share and with whom
- Respect relatives' wishes if they want to be "removed"

## 7. Your rights under GDPR

Since you yourself are the data controller for your genealogical data, you **already have full technical control** over your rights:

- **Right of access:** all your data is available in the program and in the local folder
- **Right to rectification:** you can edit at any time
- **Right to erasure:** you can delete people, events, the entire database
- **Right to data portability:** GEDCOM export gives you your data in a standard format
- **Right to restriction:** you yourself control who has access to your computer

As for the developer of PastPaths — I have no data about you to delete or disclose.

## 8. Children

If your genealogical research includes currently living children (under 13 according to GDPR practice), you should exercise extra caution. Such data has special protection and usually requires guardian consent. PastPaths does not technically prevent you from entering such information, but it is your responsibility to do so correctly.

## 9. Security

The program's security largely depends on your computer's security. I recommend:

- Using a strong password for your computer
- Keeping your operating system updated
- Using a reliable backup solution
- Being careful about who gets physical access to your computer

The program's database is not encrypted by itself. If someone gains access to your folder, they can read the database. If you need stronger protection — use disk encryption (BitLocker is built into Windows Pro and Enterprise; for Windows Home, Device Encryption is available on most modern computers).

## 10. Backups and data loss

Since the data is stored locally, it disappears if your computer breaks and you have no backups. I have no copy. This is the price of full privacy — you must take responsibility for backups yourself.

PastPaths helps you in two ways:

- On the Import/Export page, you can create a backup of the database and your uploaded files at any time.
- When you upgrade PastPaths, the installer offers to make a backup before the new version is installed.

The backups are saved on your computer (see section 2.2). Consider also keeping a copy on another device, for example an external hard drive.

Backup advice is available in the program's documentation.

## 11. What happens if PastPaths ceases to exist?

If I as the developer disappear one day — the data is still yours. It resides on your computer in:

- An SQLite database (an open, documented format that can be read by many programs)
- A folder with your photos and documents (in their original format)

You can export to GEDCOM and import into other genealogy programs. Photos and documents are not currently included in the GEDCOM export, but they are available in their original format in the `uploads` folder. You are never "locked in" to PastPaths.

## 12. Changes to this policy

When this policy is updated, the new version is published on [pastpaths.se](https://pastpaths.se) along with information about what has changed. The version of the policy that came with your installation continues to apply to that version — you are therefore not bound to future policy changes simply because you have the program installed.

## 13. Contact

Questions or concerns about privacy and PastPaths:

- Email: **[Support](mailto:support@pastpaths.se)**
- Web: **[https://pastpaths.se](https://pastpaths.se)**

For questions about GDPR in general, or if you need to file a complaint about the processing of your personal data, you can contact the Swedish Authority for Privacy Protection (Integritetsskyddsmyndigheten, IMY): [imy.se](https://www.imy.se).

---

*Last updated: 2026-10-10*