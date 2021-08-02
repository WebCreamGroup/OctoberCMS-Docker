# Docker / WinterCMS
Docker for WinterCMS *(Based on Bitnami images)*

This repository is created to use **WinterCMS** on **docker**,
and also to use it as **submodule** for **themes or plugins development**.

### How to setup
```
$ cp .env.example .env
$ cp docker-compose.yml.example docker-compose.yml
$ docker-compose up -d
$ docker-compose exec wintercms php artisan winter:install
```

***

### How to use for theme development
**Add submodule to the your repository**
```
$ git submodule add --depth 1 https://github.com/WebCreamGroup/wintercms.docker.git
$ cd ./wintercms.docker
$ cp .env.example .env
$ cp docker-compose.yml.example docker-compose.yml
```

**Some changes in docker-compose.yml**
```
### WinterCMS service
  wintercms:
    ...
    volumes:
      ...
      - ../:/app/themes/mytheme

### Apache service
  apache:
    ...
    volumes:
      ...
      - ../:/app/themes/mytheme
```

That's it! The same thing with plugins.

*P.S. You can manage many themes and plugins*

***

#### What images are included
1. `bitnami/php-fpm:7.4-debian-10`
2. `bitnami/apache:2.4-debian-10`
3. `djfarrelly/maildev`

#### How to access
- **WinterCMS**: `http://localhost` or for **ssl** `https://localhost`
- **Maildev**: `http://localhost:1080`

#### How to access docker by shell
- **As host user**: `docker-compose exec wintercms bash`
- **As root user**: `docker-compose exec -u root wintercms bash`
