# Ergebnisse Austausch

Autor: Marc Schunk / Pascal Burkhardt / LADV-Team

## Motivation

Die Geschäftsführer Tagung der Landesverbände und der DLV haben im Frühjahr 2019 beschlossen, dass alle Veranstaltungsergebnisse in Deutschland zwischen Seltec und LADV ausgetauscht werden sollen. Dieses Dokument beschreibt einen Vorschlag für die Schnittstelle dazu.

## Grundsätzliches

Grundlage für den Ergebnisse Austausch ist die Veranstaltungsdatenbank des DLV. Ergebnisse sind Datei-Anlagen
an eine Veranstaltung. Eine Veranstaltung wird durch ihre eindeutige Veranstaltungsnummer identifiziert. Ergebnisse
werden durch eine vom System vergebene GUID identifiziert und sind unveränderlich (immutable). Es werden Orginaldateien abgelegt.

Für die Schnittstelle für den Ergebnisse Austausch wird ein eigener Endpunkt verwendet, da sie die Berechtigungen unterscheiden.
Für die Veranstaltungsanmeldung hat jeder Landesverband ein System gewählt. Ergebnisse für diese Veranstaltungen werden von
unterschiedlichen Systemen bereitgestellt. Über getrennte Endpunkte können Zugriffsberechtigungen anders vergeben/verwaltet werden.

Es kann festgelegt werden welche der Dateien für leichtathletik.de bereitgestellt werden. Beispiesweise können PDFs und
HTMLs automatisch weitergegeben werden. Es ist nicht vorgesehen Ergebnisdaten XMLs oder JSONs an leichtathletik.de weiter zu gegeben.

Über die events API ist es nicht möglich Dateien hochzuladen.

## HTTP Schnittstelle

Endpunkt: `https://dateien.leichtathletik.de/results`

Für jede Ergebnisdatei werden folgende Informationen gespeichert:
- Bytes
- Art: PDF / XML / HTML / JSON
- MD5 (wird vom Server berechnet)
- GUID (wird vom Server vergeben)
- Name der Datei
- Quellsystem: DLV / LADV / SELTEC (ggf. weitere, wird über API KEY ermittelt)

### Authentifizierung

Für alle Operationen ist ein API KEY zu verwenden: Header X-Auth-Token. Der API KEY identifiziert das Quallsystem. Es werden die API KEYs der Events API verwendet.

### Datei Operationen

- Datei hochladen: HTTP POST `https://dateien.leichtathletik.de/results/<VERANSTALTUNGSNUMMER>`  
- Datei abrufen HTTP GET `https://dateien.leichtathletik.de/results/<VERANSTALTUNGSNUMMER>/<GUID>`
  Antwort enthält die Bytes
- Datei löschen: HTTP DELETE `https://dateien.leichtathletik.de/results/<VERANSTALTUNGSNUMMER>/<GUID>`

### List Operationen

- Liste Dateien zu einer Veranstaltung: HTTP GET `https://dateien.leichtathletik.de/results/<VERANSTALTUNGSNUMMER>`
- Liste Veranstaltungen + Dateien: HTTP GET `https://dateien.leichtathletik.de/results?...`

Die List Operationen bieten Filter Parameter ähnlich zum events-Endpunkt. Zusätlich gibt es Filter nach "Quellsystem" und "Art" der Datei.

### Beispiele

```command
# eine PDF-Ergebnisdatei an die DVD übermitteln
curl -si -H "X-Auth-Token:<APY-KEY>" -F "type=PDF" -F "name=Ergebnisliste" -F "data=@Document.pdf" \
  -X POST "https://dateien.leichtathletik.de/results/20L00000000205102"
HTTP 200
{"event_id":"20L00000000205102","type":"PDF","md5":"c857bf3dc0d15d1ec0e33654a93a46","guid":"765d645a-e009-4686-9443-35564bae3413","name":"Ergebnisliste","system":"SELTEC"}

# eine Ergebnisdatei aus der DVD abrufen
curl -si -H "X-Auth-Token:<APY-KEY>" -X GET \
  "https://dateien.leichtathletik.de/results/20L00000000205102/765d645a-e009-4686-9443-35564bae3413"
HTTP 200
<binary data>

# eine Ergebnisdatei in der DVD löschen
curl -si -H "X-Auth-Token:<APY-KEY>" -X DELETE \
  "https://dateien.leichtathletik.de/results/20L00000000205102/765d645a-e009-4686-9443-35564bae3413"
HTTP 204

# Liste aller Ergebnisdateien zur Veranstaltung 20L00000000205102 abrufen
curl -si -H "X-Auth-Token:<APY-KEY>" -X GET \
  "https://dateien.leichtathletik.de/results/20L00000000205102"
HTTP 200
[{
  "event_id": "20L00000001005101",
  "type": "HTML",
  "md5": "4aa5e86ab2e10a35d92ec62255e424a",
  "guid": "765d645a-e009-4686-9443-35564bae3413",
  "name": "Ergebnisse",
  "system": "SELTEC"
},]

# Liste von Ergebnisdateteien die von SELTEC bereitgestellt wurden für Veranstaltungen zwischen 1.1.2020 und 31.12.2020
# die seit dem 12.12.2020 verändert wurden.
curl -si -H "X-Auth-Token:<APY-KEY>" -X GET \
"https://dateien.leichtathletik.de/results?EventStartDate=2020-01-01&EventEndDate=2020-12-31&StateID=DM&System=SELTEC&ChangedSince=2020-12-12"
HTTP 200
```

## Nutzungshinweise

Es obligt dem System das Ergebnisse bereitstellt dafür zu sorgen, dass im Falle von Korrekturen die "veralteten" Dateien gelöscht werden und die korrigierten Dateien übermittelt werden.
Für das löschen einer Datei siehe Datei-Operationen `HTTP DELETE` und das Beispiel dazu.
Für das hochladen einer Datei siehe Datei-Operationen `HTTP POST` und das Beispiel dazu.

Desweiteren darf die gleich Datei nicht mehrfach hinterlegt werden. Das System, das Ergebnisse bereitstellt hat dafür zu sorgen, dass die gleiche Datei nicht mehrfach hinterlegt wird.

## Webhooks

Systeme die interesse an "near real time" haben, können einen Webhook-Endpoint hinterlegen lassen. Der Webhook wird dann bei neuen und gelöschten Ergebnissen informiert (für Anfrange für Webhook Endpoints bitte [GitHub](https://github.com/Deutscher-Leichtathletikverband/Veranstaltungen/issues) verwenden). Der Webhook-Endpoint erhält bei allen CREATE/DELETE Operationen einen POST request. Der body ist im wesentlichen identisch zu anderen Antworten der `results`-API. Zusätzlich informationen werden über Header transportiert.

Beispiel Webhook request-body:
```json
{
  "event_id": "20L00000001005101",
  "type": "HTML",
  "md5": "4aa5e86ab2e10a35d92ec62255e424a",
  "guid": "765d645a-e009-4686-9443-35564bae3413",
  "name": "Ergebnisse",
  "system": "SELTEC"
}
```

Zusätzlich sind zwei Header enthalten:

- `X-DVD-Operation`: enthält `CREATE` oder `DELETE`, abhängig davon ob die Ergebnis Datei angelegt oder gelöscht wurde.
- `X-DVD-Origin-Token`: enthält einen String der die Herkunft von der DVD bestätigt. Beispiel: `f70a5e86ab2e10a35d92ec62255e42aba`. Für einen Endpunkt ist der String immer identisch.

### Beispiel curls für Webhook aufrufe

Eine Cosa Ergebnisliste wird von LADV bereitgestellt:

```command
curl -si -H "X-DVD-Origin-Token:some-token" -H "Content-Type:application/json; charset=utf-8" -H "X-DVD-Operation:CREATE" \
  -d '{"event_id":"20K20000000002108","type":"XML","md5":"e4655be3f11a129e8dc26a9452d91d7","guid":"b9a10d12-e16c-4779-97f6-6439f716af63","name":"Ergebnisliste","system":"LADV"}' \
  -X POST "https://example.com/webhooks/results"
```

Eine Cosa Ergebnisliste wird von LADV gelöscht:
```command
curl -si -H "X-DVD-Origin-Token:some-token" -H "Content-Type:application/json; charset=utf-8" -H "X-DVD-Operation:DELETE" \
  -d '{"event_id":"20K20000000002108","type":"XML","md5":"e4655be3f11a129e8dc26a9452d91d7","guid":"b9a10d12-e16c-4779-97f6-6439f716af63","name":"Ergebnisliste","system":"LADV"}' \
  -X POST "https://example.com/webhooks/results"
```
