# Docker LWDP(Linux/Web/Database/PHP)

## Download
Download all files to your project dir. Skip `.gitignore`, `readme.md`, `public` paths!

## Setup compose override
If you need to set up database volumes to your env.
```bash
cp docker-compose.override.yaml.example docker-compose.override.yaml
nano docker-compose.override.yaml
```

## Set APP_NAME to .env
```bash
nano .env

# Insert variable
APP_NAME=name
```

## Configure php
* Edit Dockerfile and change php version and modules. Use [php-extension-installer documentation](https://github.com/mlocati/docker-php-extension-installer)
* Edit `docker/php/php.ini` file

## Configure apache
* Edit `docker/apache/httpd.conf` file

## Setup host
* Set local ip in `docker-compose.yaml` file: `web->ports`. By default 127.0.0.2
* Edit `ServerName=my-site.loc` config in `docker/apache/httpd.conf` file
* Insert to host
```
127.0.0.2 my-site.loc
```

## Sync users(Linux only)
For open access to write logs
```bash
 sudo chown -R www-data:www-data storage/
```

## Build and run
```bash
docker-compose up

# Or without .env
APP_NAME=name docker-compose up
```

## Go into container
```bash
docker exec -it ${APP_NAME}-app bash # Use real value of APP_NAME(see .env)
```

## Helpers
```bash
# artisan
a

# git commit all
commit
```