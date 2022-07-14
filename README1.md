## Requirement
- OS: *nix (Macos, Ubuntu…). Some commands in this document maybe not working in Windows. If you are Windows user, you should do some action by manual (git clone, copy env local…)
- Docker: version 1.13.0+
- Bitbucket Repository Access: You should contact your manager to add your email to all repository.
- Personal SSH Key: Make sure that your personal ssh key added to bitbucket: https://bitbucket.org/account/settings/ssh-keys/

## Clone repository and Build
This document will use ~/code/stock as ROOT directory. You totally use custom path yourself but in this case, you must change env variable APP_PATH before building docker image.

NOTE: ROOT directory contain ALL repo of project: api, docker...

Go to ROOT directory and run command clone this repository and create .env file.

```shell
cd ~/code/portal
git clone git@github.com:cmcthphu/de2_docker.git docker
cp docker/.env{.example,}
```

Clone api repo

```shell
cd ~/code/portal
git clone -b develop git@github.com:cmcthphu/de2_api.git api
cp api/.env{.example,}
```

Go to `docker` project.

```shell
cd ~/code/portal/docker
```

If you use custom path as ROOT directory, config APP_PATH in `.env`. Make sure Docker has access permission to your path.

```shell
APP_PORT=3080
APP_PATH=~/code/portal
POSTGRES_PORT=35432
COMPOSE_PROJECT_NAME=portal
```

Create `data` folder for postgres service

```shell
mkdir postgres/data
```

Build and run docker compose

```shell
docker compose up -d --build
```

Go to container

```shell
docker compose exec api sh
```

Composer install api

```shell
cd api
composer install
```

## Connect and Import Database
- Connect pgsql from SQL Tool

```shell
Host: localhost
Port: 35432
User: postgres
Password: secret
Database: market
```

## Conclusion
That’s all. You already to complete setup stock project in local. Let’s make amazing code.