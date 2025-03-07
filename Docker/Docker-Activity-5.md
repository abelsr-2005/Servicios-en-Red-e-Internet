
lang: es

# Actividad #5 - Docker Compose

## Ejemplo 1 - Aplicación Temperaturas

### Paso 1 - Crear docker-compose.yml
```yaml
version: '3.1'
services:
  frontend:
    container_name: temperaturas-frontend
    image: iesgn/temperaturas_frontend
    restart: always
    ports:
    - 8081:3000
    environment:
      TEMP_SERVER: temperaturas-backend:5000
    depends_on:
    - backend
  backend:
    container_name: temperaturas-backend
    image: iesgn/temperaturas_backend
    restart: always
```
![docker-compose.yml](/Docker/.imgs/Act-5/Fig1.png)

### Paso 2 - Levantar los servicios
```bash
docker compose up -d
```
![Example 1](/Docker/.imgs/Act-5/Fig2.png)

### Paso 3 - Detener los servicios
```bash
docker compose down
```

## Ejemplo 2 - Wordpress + MariaDB

### Paso 1 - Crear docker-compose.yml
```yaml
version: '3.1'
services:
  wordpress:
    image: wordpress
    restart: always
    environment:
      WORDPRESS_DB_HOST: db
      WORDPRESS_DB_USER: user_wp
      WORDPRESS_DB_PASSWORD: asdasd
      WORDPRESS_DB_NAME: bd_wp
    ports:
    - 8080:80
    volumes:
    - wordpress_data:/var/www/html
  db:
    image: mariadb
    restart: always
    environment:
      MYSQL_DATABASE: bd_wp
      MYSQL_USER: user_wp
      MYSQL_PASSWORD: asdasd
      MYSQL_ROOT_PASSWORD: asdasd
    volumes:
    - mariadb_data:/var/lib/mysql
volumes:
  wordpress_data:
  mariadb_data:
```
![docker-compose.yml](/Docker/.imgs/Act-5/Fig3.png)

### Paso 2 - Levantar los servicios
```bash
docker compose up -d
```
![Example 2](/Docker/.imgs/Act-5/Fig4.png)

### Paso 3 - Detener los servicios
```bash
docker compose down
```
