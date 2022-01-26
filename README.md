# Lowdb logger

Wir wollen einen Server programmieren, der alle Requests in einer Datei speichert.

## Endpoints
* `GET /` -> Speichert die Anfrage und gibt Ok zurück
* `GET /test` -> Speichert die Anfrage und gibt Ok zurück

## Installieren
Installiere **express** und **lowdb**:
```
npm install express
npm install lowdb
// oder so ;)
npm install express lowdb
```

### Lowdb initialisieren:
```
import { Low, JSONFile } from 'lowdb'

const db = new Low(new JSONFile('logs.json'))
await db.read()
db.data ||= { logs: [] }
```

## Logs schreiben
Schreibe für die Routen '/' und '/test' jeweils eine Funktion, die in die Datenbank (lowdb) einen neuen log eintrag hinzufügt.  
Daten:
```
{
    timestamp: Date.now(),
    message: "Die Route ... wurde aufgerufen"
}
```

## logs Prüfen
Öffne Danach per Hand die Datei logs.json und prüfe die Eintrgäge.
Es sollte ca. so ausehen:
```
{
    logs: [
        {
            timestamp: 10233654123,
            "message": "Die Route '/' wurde aufgerufen"
        }
    ]
}
```