# EvtList

Die Windows-Ereignisanzeige als Ordner im Total Commander.
Ein Dateisystem-Plugin (WFX), nur lesend, 32 und 64 Bit.

English: [README.md](README.md) · Русский: [README.ru.md](README.ru.md) · Українська: [README.uk.md](README.uk.md) · Dansk: [README.da.md](README.da.md)

<img width="1872" height="302" alt="2026-10-01_180034" src="https://github.com/user-attachments/assets/526002b2-1833-40db-9699-5b7f930bfc0a" />

## Wozu

Die Windows-Ereignisanzeige speichert alles, versteckt die Antworten aber hinter
Fachbegriffen. EvtList geht von den Fragen aus, die man tatsächlich hat:
*Was ist schiefgelaufen? Warum hat mein PC neu gestartet? Welches Programm stürzt immer wieder ab?*
Die Rohdaten sind trotzdem da, eine Ebene tiefer, für alle, die sie brauchen.

## Ordner

| Ordner | Zeigt |
|---|---|
| `_Anleitung.txt` | Kurzanleitung in der Sprache des Total Commander (F3) |
| Probleme | Kritische Fehler und Fehler aus den Protokollen Anwendung und System |
| Neustarts & Abstürze | Unerwartete Neustarts, Bluescreens, geplantes Herunterfahren, Windows-Start/-Ende |
| Programmabstürze | Abgestürzte und hängende Programme, mit Programmnamen (z. B. `AkelPad.exe abgestürzt`) |
| Alle Protokolle | Die vollständigen Protokolle: Programme (Anwendung), Windows (System), Anmeldungen (Sicherheit) |

Bekannte Ereignisse erscheinen im Klartext statt mit dem Quellnamen,
zum Beispiel `Unerwarteter Neustart (41)` statt `Kernel-Power (41)`.
Jeder Eintrag zeigt ein Fehler-, Warnungs- oder Info-Symbol.

## Tasten

| Taste | Aktion |
|---|---|
| F3 | Ereignis lesen: Bedeutung, Meldung, Felder und Details |
| Enter | Original in der Windows-Ereignisanzeige öffnen |
| Alt+Enter | Aktionsmenü (auch: Rechtsklick > Eigenschaften) |
| Strg+S | Schnellfilter nach Name, Quelle oder Ereignis-ID |

Das Aktionsmenü bietet: im Web suchen, fürs Forum kopieren, Meldung kopieren,
*Was geschah zur gleichen Zeit?* (alle lesbaren Protokolle ±5 Minuten),
in der Ereignisanzeige öffnen, Einstellungen.

Benutzerdefinierte Spalten: Level, DateTime, Source, SourceFull, EventID, TaskCategory,
User, Computer, Log, Meaning.

## Einstellungen

Rechtsklick auf *EvtList* in der Netzwerkumgebung > Eigenschaften,
oder Alt+Enter auf einem Ereignis > Einstellungen.

- Zeitraum je Ordnergruppe: 1 Stunde, 24 Stunden, 7/30/90 Tage, Alles
- Ordner ein- oder ausblenden
- Suchmaschine: Google, DuckDuckGo, Bing, Startpage, Ecosia oder eigene.
  Für eine eigene Suchmaschine dort nach dem Wort `evtlist` suchen und die Adresse aus dem Browser ins Feld einfügen.
- Was *Fürs Forum kopieren* enthält, ob persönliche Daten entfernt werden, `[code]`-Tags
- Sprache: wie Total Commander oder fest eingestellt (nach Neustart von Total Commander)

Der Dialog ist in der Größe veränderbar; auf kleinen Bildschirmen zeigt er Rollbalken.

Alle Einstellungen stehen in `EvtList.ini` im Plugin-Ordner; sie wird beim ersten Start angelegt.
Ist der Plugin-Ordner schreibgeschützt, liegt die Datei stattdessen neben der `wincmd.ini`.
Referenz (Deutsch, Englisch, Russisch, Ukrainisch, Dänisch): [notes/settings](notes/settings/index.de.html).

## Datenschutz

EvtList liest nur die lokalen Ereignisprotokolle und sendet nichts.
*Im Web suchen* öffnet den Browser nur mit Quellname und Ereignis-ID.
*Fürs Forum kopieren* entfernt standardmäßig: Benutzername, PC-Name, persönliche SIDs
und Benutzerprofilpfade (`C:\Users\<USER>\…`).

## Installation

Die Zip-Datei im Total Commander öffnen und die Installation bestätigen.
Bei einem Update darauf achten, dass auch `EvtList.lng` ersetzt wird.
Hat eine ältere Version eine Spaltenansicht hinterlassen, den Abschnitt
`[CustomFields_EvtList]` in der `wincmd.ini` löschen (bei geschlossenem Total Commander).

## Voraussetzungen und Grenzen

- Windows Vista oder neuer. Getestet mit Windows 11 und Total Commander 11.58 (64 Bit).
- Das Protokoll *Anmeldungen* (Sicherheit) ist nur lesbar, wenn Total Commander als Administrator läuft.
- Ereignismeldungen liefert Windows in der Sprache von Windows, nicht in der des Total Commander.
  Manche Microsoft-Quellen haben Aufgabenkategorien nur auf Englisch.
- Das Aktionsmenü wirkt auf das Ereignis unter dem Cursor, nicht auf eine Markierung.
  Mehrere Ereignisse lassen sich mit F5 als Textdateien kopieren.
- *Was geschah zur gleichen Zeit?* öffnet im Standard-Editor für `.txt`-Dateien.

## Übersetzungen

Englisch, Deutsch, Russisch, Ukrainisch, Dänisch in `EvtList.lng`.
Die russischen, ukrainischen und dänischen Texte sind noch nicht von Muttersprachlern geprüft;
Korrekturen sind willkommen. Eine neue Sprache ist ein neuer Abschnitt in `EvtList.lng`,
benannt nach der Sprachdatei des Total Commander (`WCMD_POL.LNG` → `[pol]`).

## Bauen

MinGW-w64, siehe `build.bat`. Quellen: `evtlist.cpp` (WFX), `evtsource.cpp` (Zugriff auf die Protokolle),
`settings.cpp` (INI und Dialog), `lang.cpp` (Übersetzungen).

## Lizenz

MIT. Autor: Native2904.
