# Instalación del servidor web Apache

#### Primero actualizamos la lista de paquetes disponibles en los repositorios configurados en el sistema:
`sudo apt update` y `sudo apt upgrade`

![](/images/.png)

#### Instalamos Apache:
`sudo apt-get install apache2`
![](/images/.png)

#### instalamos PHP, MySQL y MariaDB:
`sudo apt-get install apache2 php7.0 libapruti11-dbd-mysql -y`
![](/images/.png)

`sudo apt-get install mariadb-server mariadb-client -y`
![](/images/.png)

#### Activamos los servicios:
`sudo systemctl enable apache2`
`sudo systemctl enable mysql`
![](/images/.png)

#### Entramos en MySQL:
`sudo mysql -u root -p`
![](/images/.png)

#### Creamos una base de datos nueva:
`CREATE database defaultsite_db;`
![](/images/.png)

#### Damos permisos totales a la base de datos:
`GRANT SELECT, INSERT, UPDATE, DELETE ON defaultsite_db.* TO 'defaultsite_admin'@'localhost' IDENTIFIED BY 'usuario';`
![](/images/.png)
`GRANT SELECT, INSERT, UPDATE, DELETE ON defaultsite_db.* TO 'defaultsite_admin'@'localhost.localdomain' IDENTIFIED BY 'password';`
![](/images/.png)
`flush privileges;`
![](/images/.png)


