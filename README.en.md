# German Athletics Master Data (DSD)
API Documentation and Schemas regarding the German Athletics Master Data System (DSD).

All interfaces and definitions regarding Master Data (Athletes, Clubs, StG, LG, Regions, Counties, States)

## Master Data API
- [XML-Schema Definition (Athletes)](https://github.com/Deutscher-Leichtathletikverband/Interfaces/blob/master/Athletes.xsd)
- [XML-Schema Definition (Clubs)](https://github.com/Deutscher-Leichtathletikverband/Interfaces/blob/master/Clubs.xsd)
- [Documentation (German)](https://github.com/Deutscher-Leichtathletikverband/Interfaces/blob/master/Schnittstellenbeschreibung%20DLV%20Stammdaten.docx)
- [Documentation (English)](https://github.com/Deutscher-Leichtathletikverband/Interfaces/blob/master/Schnittstellenbeschreibung%20DLV%20Stammdaten.de.en.docx)

## Code lists

[Open API documentation](https://dateien.leichtathletik.de/meta/openapidoc)

- Agegroups: [Endpoint (JSON)](https://dateien.leichtathletik.de/meta/agegroups) | [documentation](https://dateien.leichtathletik.de/meta/openapidoc#/meta/get_meta_agegroups)
- Disciplines: [Endpoint (JSON)](https://dateien.leichtathletik.de/meta/disciplines) | [documentation](https://dateien.leichtathletik.de/meta/openapidoc#/meta/get_meta_disciplines)
- Disciplineblocks (NEW): [Endpoint (JSON)](https://dateien.leichtathletik.de/meta/disciplineblocks) | [documentation](https://dateien.leichtathletik.de/meta/openapidoc#/meta/get_meta_disciplineblocks)
- Disciplinegroups (NEW): [Endpoint (JSON)](https://dateien.leichtathletik.de/meta/disciplinegroups) | [documentation](https://dateien.leichtathletik.de/meta/openapidoc#/meta/get_meta_disciplinegroups)
- Disciplinmatrix: [Endpoint (JSON)](https://dateien.leichtathletik.de/meta/agegroupsanddisciplines) | [documentation](https://dateien.leichtathletik.de/meta/openapidoc#/meta/get_meta_agegroupsanddisciplines)
- Eventcategories: [Endpoint (JSON)](https://dateien.leichtathletik.de/meta/eventcategories) | [documentation](https://dateien.leichtathletik.de/meta/openapidoc#/meta/get_meta_eventcategories)
- Eventtypes: [Endpoint (JSON)](https://dateien.leichtathletik.de/meta/eventtypes) | [documentation](https://dateien.leichtathletik.de/meta/openapidoc#/meta/get_meta_eventtypes)
- Eventfilegroups: [Endpoint (JSON)](https://dateien.leichtathletik.de/meta/eventfilegroups) | [documentation](https://dateien.leichtathletik.de/meta/openapidoc#/meta/get_meta_eventfilegroups)

Additional information for leichtathletik.de

- Agegroup web groups: [Endpoint (JSON)](https://dateien.leichtathletik.de/meta/agegroupsweb) | [documentation](https://dateien.leichtathletik.de/meta/openapidoc#/meta/get_meta_agegroupsweb)
- Discipline web groups: [Endpoint (JSON)](https://dateien.leichtathletik.de/meta/disciplinesweb) | [documentation](https://dateien.leichtathletik.de/meta/openapidoc#/meta/get_meta_disciplinesweb)
- Eventcategories web groups: [Endpoint (JSON)](https://dateien.leichtathletik.de/meta/eventcategoriesweb) | [documentation](https://dateien.leichtathletik.de/meta/openapidoc#/meta/get_meta_eventcategoriesweb)

## API to change personal data and apply for a license (DLV TrueAthletes App) 
- https://testapi.it4sport.de/api/documentation/athletes

# German Athletics Events Database (DVD)
API Documentation and Schemas in order to exchange events.

## Events API
The main API to read and submit events from and to the German Athletics Events Database (DVD).

Current Events API (format 2021):
- XML-Schema Definition: [Format 2021](https://github.com/Deutscher-Leichtathletikverband/Interfaces/blob/main/Events-format2021.xsd) | [Format 2021 compact](https://github.com/Deutscher-Leichtathletikverband/Interfaces/blob/main/Events-format2021compact.xsd)
- [Overview changes](https://github.com/Deutscher-Leichtathletikverband/Interfaces/blob/main/Format2021-updates.md)
- Dokumentation (Deutsch) [update folgt]
- Dokumentation (English) [update folgt]

Version 3 of the Events API (deprecated):
- [XML-Schema Definition](https://github.com/Deutscher-Leichtathletikverband/Interfaces/blob/master/Events%20v3.xsd)
- [Documentation (German)](https://github.com/Deutscher-Leichtathletikverband/Interfaces/blob/master/Schnittstellenbeschreibung%20DLV%20Veranstaltungen%20Version%203.docx)
- [Documentation (English)](https://github.com/Deutscher-Leichtathletikverband/Interfaces/blob/master/Schnittstellenbeschreibung%20DLV%20Veranstaltungen%20Version%203.de.en.docx)

Legacy Version of the Events API (deprecated):
- [XML-Schema Definition](https://github.com/Deutscher-Leichtathletikverband/Interfaces/blob/master/Events.xsd)
- [Documentation (German)](https://github.com/Deutscher-Leichtathletikverband/Interfaces/blob/master/Schnittstellenbeschreibung%20DLV%20Veranstaltungen.docx)

## Ded Link API
API to exchange result links between DED and DVD:
- [Documentation (German)](https://github.com/Deutscher-Leichtathletikverband/Interfaces/blob/master/dvd-dedlink-api.md)

## Results API
API to post and exchange result files between DED and DVD:
- [Documentation (German)](https://github.com/Deutscher-Leichtathletikverband/Interfaces/blob/master/dvd-results-api.md)

# German Athletics Results Database (DED)
Everything regarding Results and Best Lists.

## Best Lists
### Get SB/PB for an Athlete ID:
Route: https://bestenliste.leichtathletik.de/api/external/athleteprofile/{AthletenGuid}
- i.e. https://bestenliste.leichtathletik.de/api/external/athleteprofile/71ece101-b7bb-4169-adf1-8b449b0eca6d
 
### Get Best List for an Agegroup and Discipline (100 rows):
Route: https://bestenliste.leichtathletik.de/api/external/performances/{KlassenCode}/{EventCode}/{Jahr}/{Umgebung}/{Page}
- i.e. https://bestenliste.leichtathletik.de/api/external/performances/M/LJ/2021/Indoor/1
 
### Search in Best Lists with an Athlete ID:
Route: https://bestenliste.leichtathletik.de/api/external/performances/{KlassenCode}/{EventCode}/{Jahr}/{Umgebung}/{Page}?guids={AthletenGuids}
- i.e. https://bestenliste.leichtathletik.de/api/external/performances/M/LJ/2021/Indoor/1?guids=c5953cd6-fbfc-11e9-bde2-6c626d40fea8&guids=bd68d2bc-0911-40de-820c-6471414dbe23

## Results
### Get Results with Athlete ID and Year:
GET https://ergebnisse.leichtathletik.de/api/Results/v1/germany/byathlete/2020/BD06D0C9-2C13-411B-BFFC-3A8FDFA4A71B

### Get Results with Athlete License and Year:
GET https://ergebnisse.leichtathletik.de/api/Results/v1/germany/byathletelegacy/2018/103460

### Get Results with Athlete License, Year and State ID:
GET https://ergebnisse.leichtathletik.de/api/Results/v1/germany/byathletelegacy/2018/103460/HE

## Others
- Swagger: https://ergebnisse.leichtathletik.de/swagger
- Current OAS3 JSON: https://ergebnisse.leichtathletik.de/swagger/v1/swagger.json
- Further Information: https://bitbucket.org/seltec/athon/
