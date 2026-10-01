# EvtList

The Windows Event Log as folders in Total Commander.
A read-only file system plugin (WFX), 32- and 64-bit.

Deutsch: [LIESMICH.md](LIESMICH.md) · Русский: [README.ru.md](README.ru.md) · Українська: [README.uk.md](README.uk.md) · Dansk: [README.da.md](README.da.md)

<img width="1872" height="302" alt="2026-10-01_180034" src="https://github.com/user-attachments/assets/526002b2-1833-40db-9699-5b7f930bfc0a" />


## Why

The Windows Event Viewer stores everything, but it hides the answers behind
technical terms. EvtList starts from the questions people actually have:
*What went wrong? Why did my PC restart? Which program keeps crashing?*
Raw data is still there, one step further down, for those who want it.

## Folders

| Folder | Shows |
|---|---|
| `_Guide.txt` | Short guide in the language of Total Commander (F3) |
| Problems | Critical errors and errors from the Application and System logs |
| Restarts & Crashes | Unexpected restarts, blue screens, planned shutdowns, Windows start/stop |
| Program Crashes | Crashed and frozen programs, named by program (e.g. `AkelPad.exe crashed`) |
| All Logs | The complete logs: Programs (Application), Windows (System), Logons (Security) |

Known events are shown in plain language instead of source names,
for example `Unexpected restart (41)` instead of `Kernel-Power (41)`.
Each entry shows an error, warning or information icon.

## Keys

| Key | Action |
|---|---|
| F3 | Read the event: meaning, message, fields and details |
| Enter | Open the original in the Windows Event Viewer |
| Alt+Enter | Action menu (also: right-click > Properties) |
| Ctrl+S | Quick filter by name, source or event ID |

The action menu offers: search the web, copy for a forum, copy message,
*what happened at the same time?* (all readable logs ±5 minutes),
open in Event Viewer, settings.

Custom columns: Level, DateTime, Source, SourceFull, EventID, TaskCategory,
User, Computer, Log, Meaning.

## Settings

Right-click on *EvtList* in the network neighbourhood > Properties,
or Alt+Enter on an event > Settings.

- Period per folder group: 1 hour, 24 hours, 7/30/90 days, all
- Show or hide folders
- Search engine: Google, DuckDuckGo, Bing, Startpage, Ecosia or custom.
  For a custom engine, search there for the word `evtlist` and paste the address from the browser into the field.
- What *Copy for forum* includes, whether personal data is removed, `[code]` tags
- Language: like Total Commander or a fixed language (after restarting Total Commander)

The dialog can be resized; on small screens it shows scroll bars.

All settings are stored in `EvtList.ini` in the plugin folder; it is created on first start.
If the plugin folder is read-only, the file is stored next to `wincmd.ini` instead.
Reference (English, German, Russian, Ukrainian, Danish): [notes/settings](notes/settings/index.html).

## Privacy

EvtList only reads the local event logs. It sends nothing anywhere.
*Search the web* opens your browser with the source name and event ID only.
*Copy for forum* removes by default: user name, PC name, personal SIDs
and user profile paths (`C:\Users\<USER>\…`).

## Installation

Open the zip file in Total Commander and confirm the installation.
When updating, make sure `EvtList.lng` is replaced as well.
If an older version left a custom column view, delete the section
`[CustomFields_EvtList]` in `wincmd.ini` (with Total Commander closed).

## Requirements and limitations

- Windows Vista or later. Tested with Windows 11 and Total Commander 11.58 (64-bit).
- The *Logons* log (Security) is only readable when Total Commander runs as administrator.
- Event messages come from Windows in the language of Windows, not of Total Commander.
  Some Microsoft sources provide task categories in English only.
- The action menu works on the event under the cursor, not on a selection.
  Several events can be copied as text files with F5.
- *What happened at the same time?* opens in the default editor for `.txt` files.

## Translations

English, German, Russian, Ukrainian, Danish in `EvtList.lng`.
The Russian, Ukrainian and Danish texts have not yet been reviewed by native speakers;
corrections are welcome. A new language is a new section in `EvtList.lng`,
named after Total Commander's language file (`WCMD_POL.LNG` → `[pol]`).

## Building

MinGW-w64, see `build.bat`. Sources: `evtlist.cpp` (WFX), `evtsource.cpp` (event log access),
`settings.cpp` (ini and dialog), `lang.cpp` (translations).

## License

MIT. Author: Native2904.
