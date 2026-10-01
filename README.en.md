# Guacamole docker compose

## Setup

Execute both commands or generate files manually

```bash
# change user if you like
# -n for no new line (guacamole container fail)
echo -n 'guacamole' > secrets/POSTGRESQL_USER

# sha1sum because postgres connection string shall not contain special charcters like /+@=
# cut for whitespace and tr for no new line (guacamole container fail)
head -c 64 /dev/urandom | sha1sum | cut -w -f1 | tr -d $'\n'> secrets/POSTGRESQL_PASSWORD
```
Default user and password: `guacadmin` `guacadmin`

## Start/Stop

To start execute `docker compose up -d` in this directory
To stop execute `docker compose down` in this directory

## Update

- stop containers `docker compose down`
- change versions in `docker-compose.yml`
- pull new images `docker compose pull` 
- start container `docker compose up -d`

## Configuration

see [Guacamole documentation]

[Guacamole documentation]: https://guacamole.apache.org/doc/gug/configuring-guacamole.html