# German Athletics Master Data (DSD)
API Documentation and Schemas regarding the German Athletics Master Data System (DSD).

All interfaces and definitions regarding Master Data (Athletes, Clubs, StG, LG, Regions, Counties, States)

## Master Data API
- [XML-Schema Definition (Athletes)](https://github.com/Deutscher-Leichtathletikverband/Interfaces/blob/master/Athletes.xsd)
- [XML-Schema Definition (Clubs)](https://github.com/Deutscher-Leichtathletikverband/Interfaces/blob/master/Clubs.xsd)
- [Documentation (German)](https://github.com/Deutscher-Leichtathletikverband/Interfaces/blob/master/Schnittstellenbeschreibung%20DLV%20Stammdaten.docx)
- [Documentation (English)](https://github.com/Deutscher-Leichtathletikverband/Interfaces/blob/master/Schnittstellenbeschreibung%20DLV%20Stammdaten.de.en.docx)

## Code lists
- [Agegroups](https://dateien.leichtathletik.de/meta/agegroups)
- [Disciplines](https://dateien.leichtathletik.de/meta/disciplines)
- [Eventcategories](https://dateien.leichtathletik.de/meta/eventcategories)
- [Eventtypes](https://dateien.leichtathletik.de/meta/eventtypes)
- [Eventfilegroups](https://dateien.leichtathletik.de/meta/eventfilegroups)

## Athletes, Licences API (DLV TrueAthletes App) 
- https://testapi.it4sport.de/api/documentation/athletes

# German Athletics Events (DVD)
API Documentation and Schemas in order to exchange events.

## Events API
The main API to read and submit Events from and to the German Athletis Events Database (DVD).

Version 3 of the Events API:
- [XML-Schema Definition](https://github.com/Deutscher-Leichtathletikverband/Interfaces/blob/master/Events%20v3.xsd)
- [Documentation (German)](https://github.com/Deutscher-Leichtathletikverband/Interfaces/blob/master/Schnittstellenbeschreibung%20DLV%20Veranstaltungen%20Version%203.docx)
- [Documentation (English)](https://github.com/Deutscher-Leichtathletikverband/Interfaces/blob/master/Schnittstellenbeschreibung%20DLV%20Veranstaltungen%20Version%203.de.en.docx)

Legacy Version of the Events API (deprecated):
- [XML-Schema Definition](https://github.com/Deutscher-Leichtathletikverband/Interfaces/blob/master/Events.xsd)
- [Documentation (German)](https://github.com/Deutscher-Leichtathletikverband/Interfaces/blob/master/Schnittstellenbeschreibung%20DLV%20Veranstaltungen.docx)

## Ded Link API
API to exchange results between DED and DVD:
- [Documentation (German)](https://github.com/Deutscher-Leichtathletikverband/Interfaces/blob/master/dvd-dedlink-api.md)

## Results API
API to post and exchange results (between DVD and DED):
- [Documentation (German)](https://github.com/Deutscher-Leichtathletikverband/Interfaces/blob/master/dvd-results-api.md)

# German Athletics Results Database (DED)
Everything regarding Results and Best Lists.

## Best lists
### Get SB/PB for an Athlete ID:
Route: https://bestenliste.leichtathletik.de/api/external/athleteprofile/{AthletenGuid}
- i.e. https://bestenliste.leichtathletik.de/api/external/athleteprofile/71ece101-b7bb-4169-adf1-8b449b0eca6d
 
### Get Best list for an Agegroup and Discipline (100 rows):
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
