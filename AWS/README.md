# Práctica: Instalación de WordPress en AWS con EFS y RDS

## Introducción
Esta práctica tiene como objetivo desplegar un sitio WordPress en AWS utilizando una instancia EC2 con almacenamiento compartido mediante EFS y una base de datos gestionada con RDS.

## 1. Creación de la infraestructura en AWS

### 1.1 Configuración de la VPC
1. Accede a la consola de AWS y dirígete al servicio de VPC.
2. Crea una nueva VPC con un rango de direcciones IP adecuado.
3. Define al menos una subred pública y otra privada.
4. Asocia una gateway de internet para permitir la conexión a la subred pública.
5. Configura la tabla de rutas para permitir la comunicación entre los recursos.

![Configuración de VPC](https://github.com/abelsr-2005/Servicios-en-Red-e-Internet/blob/main/AWS/.imgs/1.png)

### 1.2 Lanzamiento de una instancia EC2
1. En la consola de AWS, accede al servicio EC2 y lanza una nueva instancia.
2. Selecciona Ubuntu como sistema operativo.
3. Configura un grupo de seguridad permitiendo tráfico HTTP (puerto 80) y SSH (puerto 22).
4. Asocia una IP elástica si deseas una dirección pública fija.

![Lanzamiento de EC2](https://github.com/abelsr-2005/Servicios-en-Red-e-Internet/blob/main/AWS/.imgs/2.png)

### 1.3 Creación de una base de datos RDS
1. Accede al servicio RDS y crea una nueva base de datos MySQL o MariaDB.
2. Configura los parámetros como usuario, contraseña y nombre de base de datos.
3. Asegúrate de que el grupo de seguridad permite la conexión desde la instancia EC2.

![Configuración de RDS](https://github.com/abelsr-2005/Servicios-en-Red-e-Internet/blob/main/AWS/.imgs/3.png)

### 1.4 Configuración de EFS
1. Accede al servicio EFS y crea un nuevo sistema de archivos.
2. Configura los puntos de montaje en las subredes correspondientes.
3. Conecta la instancia EC2 con EFS para el almacenamiento de `wp-content`.

![Configuración de EFS](https://github.com/abelsr-2005/Servicios-en-Red-e-Internet/blob/main/AWS/.imgs/4.png)

## 2. Instalación y configuración de WordPress

### 2.1 Instalación de dependencias
Conéctate a la instancia EC2 y ejecuta los siguientes comandos:

```bash
sudo apt update && sudo apt upgrade -y
sudo apt install apache2 php php-mysql mysql-client -y
```

![Instalación de dependencias](https://github.com/abelsr-2005/Servicios-en-Red-e-Internet/blob/main/AWS/.imgs/5.png)

### 2.2 Descarga e instalación de WordPress
```bash
cd /var/www/html
sudo wget https://wordpress.org/latest.tar.gz
sudo tar -xzf latest.tar.gz
sudo chown -R www-data:www-data wordpress
```

![Descarga de WordPress](https://github.com/abelsr-2005/Servicios-en-Red-e-Internet/blob/main/AWS/.imgs/6.png)

### 2.3 Configuración de la base de datos en WordPress
Modifica el archivo `wp-config.php` y agrega las credenciales de la base de datos RDS.

![Configuración de wp-config.php](https://github.com/abelsr-2005/Servicios-en-Red-e-Internet/blob/main/AWS/.imgs/7.png)

### 2.4 Configuración de EFS en WordPress
Monta el sistema de archivos EFS y enlázalo al directorio `wp-content`:
```bash
sudo mkdir /mnt/efs
sudo mount -t efs fs-id:/ /mnt/efs
sudo ln -s /mnt/efs/wp-content /var/www/html/wordpress/wp-content
```

![Montaje de EFS](https://github.com/abelsr-2005/Servicios-en-Red-e-Internet/blob/main/AWS/.imgs/8.png)

## 3. Pruebas y despliegue
1. Accede a la dirección IP de la instancia en el navegador.
2. Sigue el asistente de instalación de WordPress.
3. Verifica que los archivos subidos se almacenen en EFS y que la base de datos se conecte correctamente a RDS.

![Asistente de instalación](https://github.com/abelsr-2005/Servicios-en-Red-e-Internet/blob/main/AWS/.imgs/9.png)

## Conclusión
Con esta configuración, WordPress se ejecuta en una arquitectura escalable con almacenamiento compartido y una base de datos gestionada, mejorando la disponibilidad y redundancia del sistema.

![Arquitectura final](https://github.com/abelsr-2005/Servicios-en-Red-e-Internet/blob/main/AWS/.imgs/10.png)
