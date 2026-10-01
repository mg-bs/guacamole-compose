# Guacamole docker compose

## Setup

Die beiden Befehle ausführen, beim ersten Starten

```bash
# change user if you like
# -n for no new line (guacamole container fail)
echo -n 'guacamole' > secrets/POSTGRESQL_USER

# sha1sum because postgres connection string shall not contain special charcters like /+@=
# cut for whitespace and tr for no new line (guacamole container fail)
head -c 64 /dev/urandom | sha1sum | cut -w -f1 | tr -d $'\n'> secrets/POSTGRESQL_PASSWORD
```

Dienst ist dann unter http://localhost:8080 erreichbar
Standarduser und -passwort sind: `guacadmin` `guacadmin`

## Start/Stop

Zum Starten in diesem Verzeichnis `docker compose up -d` ausführen `-d` startet die Container im Hintergrund  
Zum Stoppen in diesem Verzeichnis `docker compose down` ausführen  

## Update

- Container mit `docker compose down` beenden
- Versionsnummern der Images in `docker-compose.yml` anpassen  
- `docker compose pull` ausführen  
- `docker compose up -d`

## Konfiguration

siehe [Guacamole Dokumentation]

[Guacamole Dokumentation]: https://guacamole.apache.org/doc/gug/configuring-guacamole.html