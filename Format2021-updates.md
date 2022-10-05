# Format 2021 updates

Die Events API Schnittstelle bleibt im wesentlichen unverändert. Die Möglichkeit updates per Webhook zu erhhalten kommt
dazu. Das XML-Format erhält inkrementelle updates, inklusive breaking changes.

## Änderungen XML Format (format2021)

### Vereine/Kreise/Bezirke mit Stammdaten ID

Im `format2021` werden nun die Stammdaten IDs verwendet. Zudem liefert die API der DVD immer den Namen von
Verein/Kreis/Bezirk mit, sodass Systeme die nur Daten anzeigen, die Namen nicht über die Stammdatenaustausch
Schnittstelle abrufen müssen.

Beispiel bisher (`format2020`):
```xml
<StateID>BY</StateID>
<CountyID>1000</CountyID>
<DistrictID>1100</DistrictID>
<ClubID>20001246</ClubID>
```

Beispiel neu (`format2021`):
```xml
<County code="BY0001000" name="Oberbayern"/>
<District code="BY0001100" name="Oberbayern-Südwest"/>
<Club code="BY0001246" name="TSV Schleißheim"/>
```

### URL definition vereinheitlicht

Alle URLs verwenden nun einheitlich `xs:string` als Datentyp. Siehe Issue #30. Zusätzlich führt die Schnittstelle
weiterhin eine Validierung auf gültige URLs durch.

### Generische Properties ergänzt

Veranstaltungen können nun zusätzliche Properties haben. Derzeit werden diese Properties nicht gespeichert.

Beispiel:
```xml
<Event>
  ...
  <Properties>
    <Property name="leichtathletik-de" value="true"/>
    <Property name="ping" value="pong"/>
  </Properties>
  <EventCancelled>false</EventCancelled>
</Event>
```

### längere Textbausteine

Die Textbausteine (`EventFile.Remark`) können nun bis zu 2000 Zeichen lang sein. Siehe Issue #11

### persönliche Daten unterdrücken

Es ist nun möglich die öffentliche Anzeige von personen bezogenen Daten zu unterdrücken. Damit die Einstellung
akzeptiert wird, muss eine Veranstaltungswebseite angegeben werden. Siehe Issue #16.

Beispiel:
```xml
<Organizer HidePersonalData="true">
    <Salutation>Herr</Salutation>
    <FirstName>Max</FirstName>
    <LastName>Mustermann</LastName>
```

`HidePersonalData` ist optional. Ist kein Wert vorhanden wird dies als `HidePersonalData=false` behandelt. 

### Altersklassen und Disziplincodes umgestellt

Es werden nun die gleichen Altersklassen und Disziplincodes wie im Ergebnisdaten-XML und Meldungen-XML verwendet (DLV Altersklassencodes und DLV Disziplincodes).

Beispiel:
```xml
<AgeGroup ID="M12" Name="männliche Jugend M12">
    <Disciplines>
        <Discipline ID="TKUG" Normed="true" DisciplineName="Kugelstoß"/>
```

### Qualifikationsleistungen

Es ist nun möglich Qualifikationsleistungen bei Wettbewerben anzugeben. Siehe Issue #16. Beispiel:
```xml
<AgeGroup ID="M" Name="Männer">
    <Disciplines>
        <Discipline ID="TKUG" Normed="true" DisciplineName="Kugelstoß" QualificationPerformance="15,50"/>
```

Die Formatierung der Leistungen ist identisch zum Meldungen XML-Format.

### Compact Datenformat

Zusätzlich zum abruf im `format2021` gibt es noch ein "kompaktes"-Format das nur die wesentlichen Informationen zu einer
Veranstaltung enthält. Für Abrufe die nur eine Veranstaltungsliste benötigen und nicht alle Details verarbeiten ist
dieser abruf ideal. Abruf ist über `Format=format2021compact` bereits möglich. Das XSD ist unter
[Events-format2021compact.xsd](xsd/Events-format2021compact.xsd) abrufbar.

### API / Datenformat Meta-Daten updates

Codelisten, Namen und weitere Informationen für Altersklassen, Disziplinen, Veranstaltungs-Kategorien,
Veranstaltungs-Arten und Veranstaltungs-Dateigruppen stehen nun über eine überarbeitete und vereinfachte API zur
Verfügung. Die Verarbeitung dieser Meta-Daten sollte so ausgelegt sein, dass zusätzliche Werte keine Probleme
verursachen.

Highlights:
- für die Umstellung der Codelisten für Altersklassen und Disziplinen werden die neuen Codes sowie die alten IDs
  bereitgestellt. Angeschlossene Systeme können diese Mappings verwenden um altedaten zu konvertieren, falls notwendig.
- für Verein/Kreise/Bezirke werden nun die Stammdaten-IDs verwendet und eine Konvertierung der IDs für die
  Veranstaltungs-Schnittstelle entfällt zukünftig.

#### Altersklassen

Liste aller DLV Altersklassen Kennungen zur Verwendung in den Schnittstellen.

Abruf via `curl -is "https://dateien.leichtathletik.de/meta/agegroups"`

Beispiel
```json
[{
    "code": "M",
    "name": "Männer",
    "official": true,
    "legacy_id": 1,
    "name_en": "Men"
  },
  ...
]
```

#### Disziplinen

Liste aller DLV Disziplin Kennungen zur Verwendung in den Schnittstellen.

Abruf via `curl -is "https://dateien.leichtathletik.de/meta/disciplines"`

Beispiel
```json
[{
    "code": "L100",
    "legacy_ids": [
      13
    ],
    "name": "100 m Lauf",
    "official": true,
    "name_en": "100 m Sprint"
  },  ...
]
```

#### Veranstaltungs-Kategorien

Liste aller Veranstaltungs-Kategorien zur Verwendung in den Schnittstellen.

Abruf via `curl -is "https://dateien.leichtathletik.de/meta/eventcategories"`

Beispiel
```json
[{
    "name": "5.1 Deutsche Meisterschaften",
    "id": 35,
    "type": "STADIA",
    "web_category_name": "National"
  },  ...
]
```

#### Veranstaltungs-Arten

Liste aller Veranstaltungs-Arten zur Verwendung in den Schnittstellen.

Abruf via `curl -is "https://dateien.leichtathletik.de/meta/eventtypes"`

Beispiel
```json
[{
    "name": "Freiluft Stadion",
    "id": 3,
    "type": "STADIA",
    "name_en": "Outdoor stadium"
  },  ...
]
```

#### Veranstaltungs-Dateigruppen

Liste aller Veranstaltungs-Dateigruppen zur Verwendung in den Schnittstellen.

Abruf via `curl -is "https://dateien.leichtathletik.de/meta/eventfilegroups"`

Beispiel
```json
[{
    "name": "Zeitplan",
    "id": 3,
    "name_en": "Time schedule"
  },  ...
]
```

### Webhooks

Systeme die interesse an "near real time" updates haben, können einen Webhook-Endpoint hinterlegen lassen. Der
Webhook wird dann bei neuen (CREATE), aktualisierten (UPDATE) und gelöschten (DELETE) Veranstaltungen informiert (für
Anfrange für Webhook Endpoints bitte
[GitHub](https://github.com/Deutscher-Leichtathletikverband/Veranstaltungen/issues) verwenden). Der
Webhook-Endpoint erhält bei CREATE/UPDATE/DELETE Operationen einen POST request. Der body ist identisch zu
dem abruf einer einzelen Veranstaltungs-XML im `format2021` der `events`-API. Zusätzlich informationen werden
über Header transportiert.

Beispiel Webhook response-body:
```xml
<Events version="format2021">
    <Event ID="21D19000000000001" Type="STADIA" EventType="4" EventCategory="35" Name="DM Halle" Created="2020-10-07 11:45:09" Updated="2021-02-21 17:01:41">
        <DateStart>2021-02-20</DateStart>
        <DateEnd>2021-02-21</DateEnd>
        <ClosingDate>2021-02-07 00:00:00</ClosingDate>
        <CountryCode>GER</CountryCode>
        <StateID>WE</StateID>
        <FirstTime>false</FirstTime>
        <ApplyTaxes>false</ApplyTaxes>
        <Organizer>
            <FirstName>Deutscher</FirstName>
            <LastName>Leichtathletik-Verband</LastName>
            <Street>Alsfelder Straße 27</Street>
...
```

Zusätzlich sind zwei Header enthalten:

- `X-DVD-Operation`: enthält `CREATE`, `UPDATE` oder `DELETE`.
- `X-DVD-Origin-Token`: enthält einen String der die Herkunft von der DVD bestätigt. Beispiel: `f70a5e86ab2e10a35d92ec62255e42aba`. Für einen Endpunkt ist der String immer identisch.

### Beispiel curls für Webhook aufrufe

Eine Cosa Ergebnisliste wird von LADV bereitgestellt:

```command
curl -si -H "X-DVD-Origin-Token:some-token" -H "Content-Type:application/xml; charset=utf-8" -H "X-DVD-Operation:UPDATE" \
  -d '<Events version="format2021"><Event ID="21D19000000000001" ...' \
  -X POST "https://example.com/webhooks/events"
```

Die Webhooks werden ab 120 Sekunden nach der letzten Änderung versendet. Werden innerhalb der 120 Sekunden mehrere
Änderungen an einer Veranstaltung durchgeführt, so wird nur die letzte Änderung via Webhook verschickt.

Es ist nicht ausgeschlossen, das einzelne Webhooks verloren gehen können. Nutzern der Webhooks wird daher
empfohlen über einen Abruf der Veranstaltungsliste `format2021compact` einmal wöchentlich, oder einmal monatlich
zu prüfen ob Veranstaltungen out-of-sync sind und ggf. die Inkonsistenzen zu bereinigen.

Auf den Webhook wird innerhalb von 10 Sekunden ein HTTP 2XX erwaret. Keine Antwort, oder eine Antwort mit anderem
HTTP Code wird als Fehler angesehen. Webhook Endpunkte die viele Fehler liefern werden deaktiviert.

### Zusätzliche XSD updates

Weitere XSD updates

- diverse Deklarationen von default Werten entfernt
- `StateID` verwendet nun die gleiche definition wie das Stammdatenaustausch XML (via Enum)
- `AgeGroup`s enthalten nun den Namen beim abruf aus der DVD

## Deprecation alte Datenformate

Bis Ende des Jahres 2021 soll die Events API nur noch die Aktuellen Formate unterstütztn. Die alten Datenformate
`format2020`, `legacy` and `legacycompact` werden entfernt. Zudem wird der abruf der `basicdata` entfernt zugunsten
des neuen `meta`-Daten abrufes.

Um allen beteiligten die Umstellung so einfach wie möglich zu machen, wird für ein halbes Jahr die Events Schnittstelle
alte und neue Datenformate parallel unterstützen. Jedes angebundene System hat ein halbes Jahr Zeit um auf die aktuellen
Formate umzustellen.

Neue Schnittstelle verfügbar:
- abruf in `format2021` und `format2021compact` ab 15.3. via API (GET `.../events?LV=BY&Format=format2021`)
- abruf `meta`-Daten ab 15.3. via API (GET `.../meta/agegroups` etc.)
- push in `format2021` ab XX.4. via API
- Update Dokumentation für `format2021` ab XX.4. (dieses Dokument ist bereits eine zusammenstellung aller Änderungen)

Angebundene Systeme haben 6 Monate Zeit zur Umstellung auf `format2021`

Ab 1.10. ist bei Abrufen "format2021" default
Ab 1.12.2021 ist `format2020` und `legacy` nicht mehr verfügbar.


