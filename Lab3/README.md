# Deployment Anleitung

## Teil 1
Unter dem Ordern 'Teil 1' befindet sich das docker-coompose.yml. In diesem kann man die Werte für DB_USER, DB_PASSWORD und dem Namen der Datenbank anpassen wenn gewünscht. Zudem kann auch der port für die Wordpress installation geändert werden. Hier jetzt als beispiel 8000. Sobald man fertig ist kann das docker-compose gestartet werden. Dazu in der CLI folgendes im Teil1 Ordner ausführen:
```
docker-compose up -d
```

## Teil 2
Wie im vorherigen Beispiel können alle environment variablen nach Bedarf angepasst werden. Um das docker compose zuerst über 

```
docker-compose build
```
alle nötigen Container builden (im Teil 2 Ordner ausführen).
Danach kann über 
```
docker-compose up -d
```
das docker compose wieder gestartet werden.

Nach dem starten kann das Setup unter der wordpress URL ausgeführt werden und dort die Datenbankverbindung hergestellt werden.