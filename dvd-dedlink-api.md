# Ergebnisse Austausch

Autor: Marc Schunk / Pascal Burkhardt / LADV-Team

## Motivation

Links zu Veranstaltungen auf errgebnisse.leichtathletik.de (DED) verwenden nicht die
Veranstaltungsnummer. Damit Veranstaltungen auf errgebnisse.leichtathletik.de
automatisch auf leichtathletik.de verlinkt werden können, werden dies Links zur Ergebnisse seite und die Live-Ergebnisse der Veranstaltungsdatenbank (DVD) bekanntgegeben werden.

## HTTP Schnittstelle

Endpunkt: `https://dateien.leichtathletik.de/dedlink`

Operationen:
- Link setzen oder löschen: HTTP POST `https://dateien.leichtathletik.de/dedlink/<VERANSTALTUNGSNUMMER>`  
- Link abrufen: HTTP GET `https://dateien.leichtathletik.de/dedlink/<VERANSTALTUNGSNUMMER>`


### Authentifizierung

Für alle Operationen ist ein API KEY zu verwenden: Header X-Auth-Token. Der API KEY identifiziert das Quallsystem. Es werden die API KEYs der Events API verwendet.

### Beispiele

Links zur DED eintragen. Live-Ergebnisse (`ded_live_result_url`) in der DED `https://ergebnisse.leichtathletik.de/Competitions/Details/4142` und Ergebnisse (`ded_result_url`) `https://ergebnisse.leichtathletik.de/Competitions/Resultoverview/3604`.
```
curl -si -H "X-Auth-Token:<API-KEY>" -H "Content-Type:application/json" -d '{"ded_live_result_url":"https://ergebnisse.leichtathletik.de/Competitions/Details/3604","ded_result_url":"https://ergebnisse.leichtathletik.de/Competitions/Resultoverview/3604"}' \
  -X POST "https://dateien.leichtathletik.de/dedlink/20D16000000000001"
HTTP 200
{"event_id":"20D16000000000001","ded_result_url":"https://ergebnisse.leichtathletik.de/Competitions/Resultoverview/3604","ded_live_result_url":"https://ergebnisse.leichtathletik.de/Competitions/Details/3604"}
```

Links zur DED löschen:
```
curl -si -H "X-Auth-Token:<API-KEY>" -H "Content-Type:application/json" -d '{"ded_live_result_url":null,"ded_result_url":null}' \
  -X POST "https://dateien.leichtathletik.de/dedlink/20D16000000000001"
HTTP 200
{"event_id":"20D16000000000001","ded_result_url":null,"ded_live_result_url":null}
```

Aktuelle DED-Links abfragen:
```
curl -si -H "X-Auth-Token:<API-KEY>" -H "Content-Type:application/json" \
  -X GET "https://dateien.leichtathletik.de/dedlink/20D16000000000001"
HTTP 200
{"event_id":"20D16000000000001","ded_result_url":"https://ergebnisse.leichtathletik.de/Competitions/Resultoverview/3604","ded_live_result_url":"https://ergebnisse.leichtathletik.de/Competitions/Details/3604"}
```
