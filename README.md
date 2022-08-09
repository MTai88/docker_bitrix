## Bitrix infrastructure
This repository contains infrastructure code for Bitrix-based site. It's include cronjob, mailhog, adminer, memcached

## Install

### Configure the environment file

Copy file `.env_template` into `.env`

```
cp -f .env_template .env
```

You can change config options in ```.env``` file:

```
PHP_VERSION=php74          # php version
WEB_SERVER_TYPE=nginx      # server type nginx/apache
DB_SERVER_TYPE=mysql       # mysql/percona
MYSQL_DATABASE=bitrix      # database name
MYSQL_USER=bitrix          # database user
MYSQL_PASSWORD=123         # database user password
MYSQL_ROOT_PASSWORD=123    # database root user password
INTERFACE=0.0.0.0          # interface where ports will be proxied
SITE_PATH=/var/www/bitrix  # path to your site files directory
```

## Starting and stopping containers
### Start
```
docker-compose up -d
```

### Stop
```
docker-compose down
```

## Notes
- Default path with your local files ```/var/www/bitrix/```
- You should write database container name as "db" in database server address, "localhost" won't be working. Example database & memcached site [config](configs/.settings.php).
- To upload the database backup use the command: ```cat /var/www/bitrix/backup.sql | docker exec -i mysql /usr/bin/mysql -u root -p123 bitrix```
- Mailhog web interface: `http://localhost:8025`
- Adminer web interface: `http://localhost:8080`

---
Based on the [BitrixDock](https://github.com/bitrixdock/bitrixdock)