y<# DLV Stammdatenbank (DSD)
Schnittstellendokumentation und Schemas der DLV Stammdatenbank (DSD).

Alle Schnittstellen und deren Dokumentation bzgl. der DLV Stammdaten (Athleten/Athletinnen, Vereine, StG, LG, Kreise, Bezirke, Landesverbände)

## Stammdatenschnittstelle
- [XML-Schema Definition (Athleten/Athletinnen)](https://github.com/Deutscher-Leichtathletikverband/Interfaces/blob/master/Athletes.xsd)
- [XML-Schema Definition (Vereine)](https://github.com/Deutscher-Leichtathletikverband/Interfaces/blob/master/Clubs.xsd)
- [Dokumentation (Deutsch)](https://github.com/Deutscher-Leichtathletikverband/Interfaces/blob/master/Schnittstellenbeschreibung%20DLV%20Stammdaten.docx)
- [Dokumentation (English)](https://github.com/Deutscher-Leichtathletikverband/Interfaces/blob/master/Schnittstellenbeschreibung%20DLV%20Stammdaten.de.en.docx)

## Codelisten

Die Codelisten sind öffentlich. [Open API Dokumentation](https://dateien.leichtathletik.de/meta/openapidoc)

- Altersklassen: [Endpunkt (JSON)](https://dateien.leichtathletik.de/meta/agegroups) | [Dokumentation](https://dateien.leichtathletik.de/meta/openapidoc#/meta/get_meta_agegroups)
- Disziplinen: [Endpunkt (JSON)](https://dateien.leichtathletik.de/meta/disciplines) | [Dokumentation](https://dateien.leichtathletik.de/meta/openapidoc#/meta/get_meta_disciplines)
- Disziplinblöcke (NEU): [Endpunkt (JSON)](https://dateien.leichtathletik.de/meta/disciplineblocks) | [Dokumentation](https://dateien.leichtathletik.de/meta/openapidoc#/meta/get_meta_disciplineblocks)
- Disziplingruppen (NEU): [Endpunkt (JSON)](https://dateien.leichtathletik.de/meta/disciplinegroups) | [Dokumentation](https://dateien.leichtathletik.de/meta/openapidoc#/meta/get_meta_disciplinegroups)
- Disziplinmatrix: [Endpunkt (JSON)](https://dateien.leichtathletik.de/meta/agegroupsanddisciplines) | [Dokumentation](https://dateien.leichtathletik.de/meta/openapidoc#/meta/get_meta_agegroupsanddisciplines)
- Veranstaltungskategorien: [Endpunkt (JSON)](https://dateien.leichtathletik.de/meta/eventcategories) | [Dokumentation](https://dateien.leichtathletik.de/meta/openapidoc#/meta/get_meta_eventcategories)
- Veranstaltungstypen: [Endpunkt (JSON)](https://dateien.leichtathletik.de/meta/eventtypes) | [Dokumentation](https://dateien.leichtathletik.de/meta/openapidoc#/meta/get_meta_eventtypes)
- Veranstaltungsfilegruppen: [Endpunkt (JSON)](https://dateien.leichtathletik.de/meta/eventfilegroups) | [Dokumentation](https://dateien.leichtathletik.de/meta/openapidoc#/meta/get_meta_eventfilegroups)

Zusatzinformationen für leichtathletik.de

- Altersklassen Web Gruppen: [Endpunkt (JSON)](https://dateien.leichtathletik.de/meta/agegroupsweb) | [Dokumentation](https://dateien.leichtathletik.de/meta/openapidoc#/meta/get_meta_agegroupsweb)
- Disziplinen Web Gruppen: [Endpunkt (JSON)](https://dateien.leichtathletik.de/meta/disciplinesweb) | [Dokumentation](https://dateien.leichtathletik.de/meta/openapidoc#/meta/get_meta_disciplinesweb)
- Veranstaltungskategorien Web Gruppen: [Endpunkt (JSON)](https://dateien.leichtathletik.de/meta/eventcategoriesweb) | [Dokumentation](https://dateien.leichtathletik.de/meta/openapidoc#/meta/get_meta_eventcategoriesweb)

## Meldungen Datenformat

Das Meldungen-Datenformat dient zum Austausch von Meldungen zwischen Meldeprogrammen und Wettkampfprogrammen.

- [Dokumentation Datenformat Meldungen 1.2 (PDF)](docs/Registration-Format-1.2.pdf)
- [XML-Schema Datei (XSD)](xsd/registration-1.2.xsd)
- [Beispieldateien](samples/registration-1.2)
- [Änderungsübersicht](https://github.com/Deutscher-Leichtathletikverband/Interfaces/issues/4)

## Schnittstelle Personendaten lesen/ändern und Startrecht beantragen (DLV TrueAthletes App) 
- https://testapi.it4sport.de/api/documentation/athletes

# DLV Veranstaltungsdatenbank (DVD)
Schnittstellendokumentation und Schemas für den Austausch von Veranstaltungen.

## Veranstaltungsschnittstelle
Die Standardschnittstelle zum Lesen und Schreiben von Veranstaltungen von bzw. in die DLV Veranstaltungsdatenbank (DVD).

Aktuelle Veranstaltungsschnittstelle (Format 2023):
- XML-Schema Definition: [Format 2023](https://github.com/Deutscher-Leichtathletikverband/Interfaces/blob/main/xsd/Events-format2023.xsd) | [Format 2023 list](https://github.com/Deutscher-Leichtathletikverband/Interfaces/blob/main/xsd/Events-format2023list.xsd)
- [Beispieldateien](https://github.com/Deutscher-Leichtathletikverband/Interfaces/tree/main/samples/event-format-2023)
- [Übersicht Änderungen](https://github.com/Deutscher-Leichtathletikverband/Interfaces/pull/7)
- [Dokumentation (Englisch)](https://github.com/Deutscher-Leichtathletikverband/Interfaces/blob/main/DVD-Documentation-Update-2023.pdf)

Aktuelle Veranstaltungsschnittstelle (Format 2021):
- XML-Schema Definition: [Format 2021](https://github.com/Deutscher-Leichtathletikverband/Interfaces/blob/main/xsd/Events-format2021.xsd) | [Format 2021 compact](https://github.com/Deutscher-Leichtathletikverband/Interfaces/blob/main/xsd/Events-format2021compact.xsd)
- [Übersicht Änderungen gegenüber Version 3](https://github.com/Deutscher-Leichtathletikverband/Interfaces/blob/main/Format2021-updates.md)

## Vermessene Strecken
- Liste der vermessenen Strecken: [Endpunkt (JSON)](https://dateien.leichtathletik.de/tracks) | [Dokumentation](https://dateien.leichtathletik.de/meta/openapidoc#/tracks/get_tracks)
- Vermessene Strecke mittels id: https://dateien.leichtathletik.de/tracks/{id} | [Dokumentation](https://dateien.leichtathletik.de/meta/openapidoc#/tracks/get_tracks__id_) 

## Schnittstelle zum Austausch der Ergebnislinks
Schnittstelle zum Austausch der Ergebnislinks (Live-Ergebnisse und Endergebnisse) zwischen der DED und DVD:
- [Dokumentation (Deutsch)](https://github.com/Deutscher-Leichtathletikverband/Interfaces/blob/master/dvd-dedlink-api.md)

## Schnittstelle zum Austausch von Ergebnisdateien
Schnittstelle zum Übermitteln von Ergebnisdateien zwischen DED und DVD:
- [Dokumentation (Deutsch)](https://github.com/Deutscher-Leichtathletikverband/Interfaces/blob/master/dvd-results-api.md)

# DLV Ergebnisdatenbank (DED)
Alles rund um die Ergebnisdatenbank und die Bestenlisten.

## Bestenlisten
### Lesen der SB/PB für eine Athleten ID:
Route: https://bestenliste.leichtathletik.de/api/external/athleteprofile/{AthletenGuid}
- i.e. https://bestenliste.leichtathletik.de/api/external/athleteprofile/71ece101-b7bb-4169-adf1-8b449b0eca6d
 
### Lesen der Bestenliste für eine Altersklasse und Disziplin (100 Zeilen):
Route: https://bestenliste.leichtathletik.de/api/external/performances/{KlassenCode}/{EventCode}/{Jahr}/{Umgebung}/{Page}
- i.e. https://bestenliste.leichtathletik.de/api/external/performances/M/LJ/2021/Indoor/1
 
### Suche in einer Bestenliste nach einer Athleten ID:
Route: https://bestenliste.leichtathletik.de/api/external/performances/{KlassenCode}/{EventCode}/{Jahr}/{Umgebung}/{Page}?guids={AthletenGuids}
- i.e. https://bestenliste.leichtathletik.de/api/external/performances/M/LJ/2021/Indoor/1?guids=c5953cd6-fbfc-11e9-bde2-6c626d40fea8&guids=bd68d2bc-0911-40de-820c-6471414dbe23

## Ergebnisse
### Lesen der Ergebnisse für eine Athleten ID und ein bestimmtes Jahr:
GET https://ergebnisse.leichtathletik.de/api/Results/v1/germany/byathlete/2020/BD06D0C9-2C13-411B-BFFC-3A8FDFA4A71B

### Lesen der Ergebnisse für eine Athleten Startrechtsnummer und ein bestimmtes Jahr:
GET https://ergebnisse.leichtathletik.de/api/Results/v1/germany/byathletelegacy/2018/103460

### Lesen der Ergebnisse für eine Athleten Startrechtsnummer, einem bestimmten Jahr und einem Landesverband:
GET https://ergebnisse.leichtathletik.de/api/Results/v1/germany/byathletelegacy/2018/103460/HE

## Sonstiges
- Swagger: https://ergebnisse.leichtathletik.de/swagger
- Aktuelles OAS3 JSON: https://ergebnisse.leichtathletik.de/swagger/v1/swagger.json
- Weitere Informationen: https://bitbucket.org/seltec/athon/

## Englische Version
### If you are looking for an english version:
https://github.com/Deutscher-Leichtathletikverband/Interfaces/blob/main/README.en.md
