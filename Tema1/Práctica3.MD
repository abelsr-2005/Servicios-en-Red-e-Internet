# Instalación del servidor web Apache

#### Primero actualizamos la lista de paquetes disponibles en los repositorios configurados en el sistema:
`sudo apt update` y `sudo apt upgrade`

![](img-aws/Screenshot_1.png) <br>
![](img-aws/Screenshot_2.png)

#### Instalamos Apache:
`sudo apt-get install apache2`<br>
![](img-aws/Screenshot_3.png)

#### instalamos PHP, MySQL y MariaDB:
`sudo apt-get install apache2 php7.0 libapruti11-dbd-mysql -y`<br>
![](img-aws/Screenshot_4.png)

`sudo apt-get install mariadb-server mariadb-client -y`<br>
![](img-aws/Screenshot_5.png)

#### Activamos los servicios:
`sudo systemctl enable apache2`
`sudo systemctl enable mysql`<br>
![](img-aws/Screenshot_6.png)

#### Entramos en MySQL y creamos una base de datos nueva:
`sudo mysql -u root -p` <br>
![](img-aws/Screenshot_7.png)

#### Damos permisos totales a la base de datos:
`GRANT SELECT, INSERT, UPDATE, DELETE ON defaultsite_db.* TO 'defaultsite_admin'@'localhost' IDENTIFIED BY 'usuario';` <br>
`GRANT SELECT, INSERT, UPDATE, DELETE ON defaultsite_db.* TO 'defaultsite_admin'@'localhost.localdomain' IDENTIFIED BY 'password';` <br>
![](img-aws/Screenshot_8.PNG)
`flush privileges;` <br>
![](img-aws/Screenshot_9.PNG)

#### Entramos en la base de datos:
`use defaultsite_db;` <br>
![](img-aws/Screenshot_10.png)
#### Y creamos una tabla para los usuarios autenticados:
`CREATE table mysql_auth ( username varchar(191) not null, passwd varchar(191), groups varchar(191), primary key (username) );`
![](img-aws/Screenshot_11.PNG) <br>
Transformamos una contraseña a hash para hacerlo más seguro:
`htpasswd -bns siteuser siteuser` <br>
![](img-aws/Screenshot_12.PNG)
#### Insertamos los datos en la tabla que hemos creado en la base de datos.
`INSERT INTO `mysql_auth` (`username`, `passwd`, `groups`) VALUES('siteuser', '{SHA}tk7HEH6Wo7SKT6+3FHCgiGnJ6dA=', 'sitegroup');` <br>
![](img-aws/Screenshot_13.PNG)
#### Habilitamos los módulos.
`sudo a2enmod dbd` <br>
`sudo a2enmod authn_dbd` <br>
`sudo a2enmod socache_shmcb` <br>
`sudo a2enmod authn_socache`

#### Creamos el directorio que estará protegido.

`sudo mkdir /var/www/html/protecteddir` <br>
`sudo chown -R www-data:www-data /var/www/html/protecteddir`

#### Modificamos la configuración de Apache de nuestro dominio:
`sudo nano /etc/apache2/sites-available/000-default.conf`

#### Introducimos lo siguiente:

#### Y reiniciamos Apache.
`sudo systemctl restart apache2`


#### Ahora cuando entremos al directorio por acceso web, nos pedirá el usuario y contraseña.




