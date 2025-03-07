
lang: es

# Actividad #4 - Almacenamiento y Redes

## Ejemplo 1 - Aplicación Temperaturas

### Paso 1 - Crear la red
```bash
docker network create red_temperaturas
```
![Example 1](/Docker/.imgs/Act-4/Fig1.png)

### Paso 2 - Ejecutar el backend
```bash
docker run -d --name temperaturas-backend --network red_temperaturas iesgn/temperaturas_backend
```

### Paso 3 - Ejecutar el frontend
```bash
docker run -d -p 80:3000 --name temperaturas-frontend --network red_temperaturas iesgn/temperaturas_frontend
```

## Ejemplo 2 - Wordpress + MariaDB

### Paso 1 - Crear la red
```bash
docker network create red_wp
```

### Paso 2 - Crear y ejecutar MariaDB
```bash
docker run -d --name servidor_mysql     --network red_wp     -v /opt/mysql_wp:/var/lib/mysql     -e MYSQL_DATABASE=bd_wp     -e MYSQL_USER=user_wp     -e MYSQL_PASSWORD=asdasd     -e MYSQL_ROOT_PASSWORD=asdasd     mariadb
```

### Paso 3 - Crear y ejecutar WordPress
```bash
docker run -d --name servidor_wp     --network red_wp     -v /opt/wordpress:/var/www/html/wp-content     -e WORDPRESS_DB_HOST=servidor_mysql     -e WORDPRESS_DB_USER=user_wp     -e WORDPRESS_DB_PASSWORD=asdasd     -e WORDPRESS_DB_NAME=bd_wp     -p 80:80     wordpress
```
