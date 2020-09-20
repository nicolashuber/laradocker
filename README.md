# Laradocker

A Docker environment for developing Laravel applications.

## Setup

```
./bin/install
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
docker-compose run --rm yarn dev
```

## Deploy

```
ssh-keygen -f deploy/.ssh/id_ed25519 -t ed25519 -N ''
cat deploy/.ssh/id_ed25519.pub
```

```
docker-compose run --rm deployer deploy production
```

```
git push && docker-compose run --rm deployer deploy production && ssh -t root@otis 'service php7.3-fpm reload' 
```

## Artisan worker

```
docker-compose run --rm php artisan queue:work --tries=3
``
