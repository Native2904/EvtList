# EvtList

Windows-hændelsesloggen som mapper i Total Commander.
Et filsystem-plugin (WFX), kun læsning, 32 og 64 bit.

English: [README.md](README.md) · Deutsch: [LIESMICH.md](LIESMICH.md) · Русский: [README.ru.md](README.ru.md) · Українська: [README.uk.md](README.uk.md)

## Hvorfor

Windows Logbog gemmer alt, men gemmer svarene bag tekniske begreber.
EvtList tager udgangspunkt i de spørgsmål, man faktisk har:
*Hvad gik galt? Hvorfor genstartede min pc? Hvilket program bliver ved med at gå ned?*
Rådata er der stadig, et niveau længere nede, for dem der har brug for dem.

## Mapper

| Mappe | Viser |
|---|---|
| `_Vejledning.txt` | Kort vejledning på Total Commanders sprog (F3) |
| Problemer | Kritiske fejl og fejl fra logfilerne Program og System |
| Genstarter & nedbrud | Uventede genstarter, blå skærme, planlagte lukninger, Windows start/stop |
| Programnedbrud | Programmer, der er gået ned eller hænger, med programnavn (f.eks. `AkelPad.exe gik ned`) |
| Alle logge | De komplette logge: Programmer (Program), Windows (System), Logon (Sikkerhed) |

Kendte hændelser vises i klar tekst i stedet for kildenavnet,
for eksempel `Uventet genstart (41)` i stedet for `Kernel-Power (41)`.
Hver post viser et fejl-, advarsels- eller informationssymbol.

## Taster

| Tast | Handling |
|---|---|
| F3 | Læs hændelsen: betydning, meddelelse, felter og detaljer |
| Enter | Åbn originalen i Windows Logbog |
| Alt+Enter | Handlingsmenu (også: højreklik > Egenskaber) |
| Ctrl+S | Hurtigfilter efter navn, kilde eller hændelses-id |

Handlingsmenuen tilbyder: søg på nettet, kopiér til forum, kopiér meddelelse,
*Hvad skete der samtidig?* (alle læsbare logge ±5 minutter),
åbn i Logbog, indstillinger.

Brugerdefinerede kolonner: Level, DateTime, Source, SourceFull, EventID, TaskCategory,
User, Computer, Log, Meaning.

## Indstillinger

Højreklik på *EvtList* i netværksomgivelser > Egenskaber,
eller Alt+Enter på en hændelse > Indstillinger.

- Periode for hver mappegruppe: 1 time, 24 timer, 7/30/90 dage, alle
- Vis eller skjul mapper
- Søgemaskine: Google, DuckDuckGo, Bing, Startpage, Ecosia eller egen.
  For en egen søgemaskine: søg efter ordet `evtlist` der, og indsæt adressen fra browseren i feltet.
- Hvad *Kopiér til forum* indeholder, om personlige data fjernes, `[code]`-tags
- Sprog: som Total Commander eller et fast sprog (efter genstart af Total Commander)

Dialogens størrelse kan ændres; på små skærme vises rullepaneler.

Alle indstillinger gemmes i `EvtList.ini` i plugin-mappen; filen oprettes ved første start.
Er plugin-mappen skrivebeskyttet, gemmes filen i stedet ved siden af `wincmd.ini`.
Reference (dansk, engelsk, tysk, russisk, ukrainsk): [notes/settings](notes/settings/index.da.html).

## Privatliv

EvtList læser kun de lokale hændelseslogge og sender intet nogen steder hen.
*Søg på nettet* åbner browseren kun med kildenavn og hændelses-id.
*Kopiér til forum* fjerner som standard: brugernavn, pc-navn, personlige SID'er
og brugerprofilstier (`C:\Users\<USER>\…`).

## Installation

Åbn zip-filen i Total Commander, og bekræft installationen.
Ved en opdatering skal du sikre dig, at `EvtList.lng` også bliver erstattet.
Har en ældre version efterladt en kolonnevisning, så slet afsnittet
`[CustomFields_EvtList]` i `wincmd.ini` (med Total Commander lukket).

## Krav og begrænsninger

- Windows Vista eller nyere. Testet med Windows 11 og Total Commander 11.58 (64 bit).
- Loggen *Logon* (Sikkerhed) kan kun læses, når Total Commander kører som administrator.
- Hændelsesmeddelelser leveres af Windows på Windows' sprog, ikke på Total Commanders.
  Nogle Microsoft-kilder har kun opgavekategorier på engelsk.
- Handlingsmenuen virker på hændelsen under markøren, ikke på en markering.
  Flere hændelser kan kopieres som tekstfiler med F5.
- *Hvad skete der samtidig?* åbnes i standardeditoren for `.txt`-filer.

## Oversættelser

Engelsk, tysk, russisk, ukrainsk, dansk i `EvtList.lng`.
De russiske, ukrainske og danske tekster er endnu ikke gennemgået af modersmålstalende;
rettelser er velkomne. Et nyt sprog er et nyt afsnit i `EvtList.lng`,
opkaldt efter Total Commanders sprogfil (`WCMD_POL.LNG` → `[pol]`).

## Bygning

MinGW-w64, se `build.bat`. Kildefiler: `evtlist.cpp` (WFX), `evtsource.cpp` (adgang til loggene),
`settings.cpp` (ini og dialog), `lang.cpp` (oversættelser).

## Licens

MIT. Forfatter: Native2904.
