# WordPress with Docker/Webpack/SASS
A template for WordPress theme development

## Prerequisites
You will need the following preinstalled on your local machine.
- Docker
- Docker Compose
- Node.js
- npm

## Getting Started
```sh
cd mytheme
npm install
cd ..
docker-compose up
# Now connect to localhost:8082
```

## Development
Develop inside mytheme folder. To compile sass|scss and js files, run `npm run build`. For distribution, run `npm run dist`. And for hot reload, run `npm run watch`.

## Installing Plugins
Due to the way plugin folder is mounted in docker, you have to add `define('FS_METHOD', 'direct');` to wp-config.php.


```sh
# Get container id
docker ps
docker exec -it <wordpress_container_id> bash

# Now inside wordpress container
apt-get update
apt-get install vim
vim wp-config.php
```


## Copying existing project with duplicator
1. Install Duplicator plugin in old project
2. Click create new
3. Download both installer and archive
4. Copy installer.php and archive using the following command

```sh
# Remove all existing files
docker exec -it <container> bash
rm -rf /var/www/
exit

docker cp <container>:/installer.php /var/www/html/
docker cp <container>:/archive /var/www/html/
```
5. Go to localhost:8082/installer.php
6. `db` as host, wordpress as user and password
