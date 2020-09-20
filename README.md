# Laradocker

A Docker environment for developing Laravel applications.

## Setup

```
sudo ./bin/install -b
```

## Server
```
docker-compose up server
```

## Artisan
```
docker-compose run --rm php artisan
```

## Assets

#### Install
```
docker-compose run --rm yarn
```

#### Development build
```
docker-compose run --rm yarn watch
```
