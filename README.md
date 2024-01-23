# sample-mvc
Model de projet PHP utilisant le pattern MVC, ce modèle est à but pédagogique pour les étudiants CDA (Concepteur Développeur d'Application)

## Pré-requis
- LAMP
- Le module rewrite de apache activé
- les extensions php : pdo et pdo_mysql

## Installer LAMP et tout ce qui faut sous Docker
### Installer Docker Desktop
https://www.docker.com/products/docker-desktop/

### Créer l'environnement LAMP en ligne de commande :
Copiez collez les commandes suivantes dans un invité de commande après avoir installer Docker Desktop
```bash
docker network create lamp-net

docker run -d --name lamp-php --network=lamp-net -p 80:80 php:8.2-apache

docker exec lamp-php docker-php-ext-install pdo
docker exec lamp-php docker-php-ext-install pdo_mysql
docker exec lamp-php docker-php-ext-install mysqli
docker exec lamp-php a2enmod rewrite

docker run -d --name lamp-mysql --network=lamp-net -e MYSQL_ROOT_PASSWORD=root mysql

docker run -d --name lamp-pma --network=lamp-net -e PMA_HOST=lamp-mysql -p 8080:80 phpmyadmin

docker start lamp-php
docker start lamp-mysql
docker start lamp-pma

```

## Mettre en place le projet
- Ouvrez le container lamp-php sous VSCode avec l'extension Dev Container.
- Clonez le repo sur votre ordinateur.
```bash
git clone https://github.com/CHAOUCHI/sample-mvc.git
```
- Copier coller le dossier samp-mvc dans le dossier /var/www/html du container lamp-php depuis VSCode.

