# DLV Stammdatenbank (DSD)
Schnittstellendokumentation und Schemas der DLV Stammdatenbank (DSD).

Alle Schnittstellen und deren Dokumentation bzgl. der DLV Stammdaten (Athleten/Athletinnen, Vereine, StG, LG, Kreise, Bezirke, Landesverbände)

## Stammdatenschnittstelle
- [XML-Schema Definition (Athleten/Athletinnen)](https://github.com/Deutscher-Leichtathletikverband/Interfaces/blob/master/Athletes.xsd)
- [XML-Schema Definition (Vereine)](https://github.com/Deutscher-Leichtathletikverband/Interfaces/blob/master/Clubs.xsd)
- [Dokumentation (Deutsch)](https://github.com/Deutscher-Leichtathletikverband/Interfaces/blob/master/Schnittstellenbeschreibung%20DLV%20Stammdaten.docx)
- [Dokumentation (English)](https://github.com/Deutscher-Leichtathletikverband/Interfaces/blob/master/Schnittstellenbeschreibung%20DLV%20Stammdaten.de.en.docx)

## Codelisten
- [Altersklassen](https://dateien.leichtathletik.de/meta/agegroups)
- [Disziplinen](https://dateien.leichtathletik.de/meta/disciplines)
- [Veranstaltungskategorien](https://dateien.leichtathletik.de/meta/eventcategories)
- [Veranstaltungstypen](https://dateien.leichtathletik.de/meta/eventtypes)
- [Veranstaltungsfilegruppen](https://dateien.leichtathletik.de/meta/eventfilegroups)

## Schnittstelle Personendaten lesen/ändern und Startrecht beantragen (DLV TrueAthletes App) 
- https://testapi.it4sport.de/api/documentation/athletes

# DLV Veranstaltungsdatenbank (DVD)
Schnittstellendokumentation und Schemas für den Austausch von Veranstaltungen.

## Veranstaltungsschnittstelle
Die Standardschnittstelle zum Lesen und Schreiben von Veranstaltungen von bzw. in die DLV Veranstaltungsdatenbank (DVD).

Version 3 der Veranstaltungsschnittstelle:
- [XML-Schema Definition](https://github.com/Deutscher-Leichtathletikverband/Interfaces/blob/master/Events%20v3.xsd)
- [Dokumentation (Deutsch)](https://github.com/Deutscher-Leichtathletikverband/Interfaces/blob/master/Schnittstellenbeschreibung%20DLV%20Veranstaltungen%20Version%203.docx)
- [Dokumentation (English)](https://github.com/Deutscher-Leichtathletikverband/Interfaces/blob/master/Schnittstellenbeschreibung%20DLV%20Veranstaltungen%20Version%203.de.en.docx)

Die ursprüngliche Version der Veranstaltungsschnittstelle (veraltet):
- [XML-Schema Definition](https://github.com/Deutscher-Leichtathletikverband/Interfaces/blob/master/Events.xsd)
- [Dokumentation (Deutsch)](https://github.com/Deutscher-Leichtathletikverband/Interfaces/blob/master/Schnittstellenbeschreibung%20DLV%20Veranstaltungen.docx)

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
