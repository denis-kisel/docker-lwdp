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

## Build and run
```bash
docker-compose up

# Or without .env
APP_NAME=name docker-compose up
```

## Laravel helper
Insert script to composer.json. Replace APP_NAME to real value from .env
```json
...
"scripts": {
  "a": [
        "docker-compose exec APP_NAME php artisan "
  ],
  "c": [
      "docker-compose exec APP_NAME composer "
  ]
}
...
```

Then
```bash
# php artisan
composer a

# Composer under container
composer c
```