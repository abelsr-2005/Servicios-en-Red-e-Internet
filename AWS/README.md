# Práctica: Instalación de WordPress en AWS con EFS y RDS

## Introducción
Esta práctica tiene como objetivo desplegar un sitio WordPress en AWS utilizando una instancia EC2 con almacenamiento compartido mediante EFS y una base de datos gestionada con RDS.

## 1. Creación de la infraestructura en AWS

### 1.1 Configuración de la VPC
1. Accede a la consola de AWS y dirígete al servicio de VPC. <br>
   ![VPC](.imgs/3.png)<br>
2. Crea una nueva VPC con un rango de direcciones IP adecuado.<br>
      ![VPC](.imgs/6.png)<br>
4. Define al menos una subred pública y otra privada.<br>
      ![VPC](.imgs/7.png)<br>
5. Asocia una gateway de internet para permitir la conexión a la subred pública.<br>
      ![VPC](.imgs/8.png)<br>
6. Crea la VPC<br>
      ![VPC](.imgs/9.png)<br>

### 1.2 Lanzamiento de una instancia EC2
1. En la consola de AWS, accede al servicio EC2 y lanza una nueva instancia.
      ![VPC](.imgs/10.png)<br>
2. Selecciona Ubuntu como sistema operativo.
      ![VPC](.imgs/11.png)<br>
3. Configura un grupo de seguridad permitiendo tráfico HTTP (puerto 80) y SSH (puerto 22).
      ![VPC](.imgs/15.png)<br>
4. Asocia la VPC.
      ![VPC](.imgs/14.png)<br>
5. Lanzaremos la instancia.
      ![VPC](.imgs/16.png)<br>

### 1.3 Creación de una base de datos RDS
1. Accede al servicio RDS y crea una nueva base de datos MySQL o MariaDB.
      ![VPC](.imgs/27.png)<br>
      ![VPC](.imgs/29.png)<br>
3. Configura los parámetros como usuario, contraseña y nombre de base de datos.
      ![VPC](.imgs/31.png)<br>
4. Asegúrate de que el grupo de seguridad permite la conexión desde la instancia EC2.
      ![VPC](.imgs/33.png)<br>
5. Configura la clase de instancia de base de datos y el almacenamiento.
      ![VPC](.imgs/32.png)<br>
6. Una vez hayamos configurado todo, la crearemos.
      ![VPC](.imgs/35.png)<br>

### 1.4 Configuración de la conexión de EC2 con RDS
1. Seleccionamos la base de datos y pulsaremos sobre "Acciones -> Configurar la conexión de EC2"
      ![VPC](.imgs/36.png)
2. Seleccionaremos la instancia de EC2:
      ![VPC](.imgs/37.png)
3. Confirmaremos los cambios:
      ![VPC](.imgs/38.png)

### 1.5 Configuración de EFS
1. Accede al servicio EFS y crea un nuevo sistema de archivos.
      ![VPC](.imgs/39.png)
2. Configura los puntos de montaje en las subredes correspondientes.
      ![VPC](.imgs/41.png)
      ![VPC](.imgs/42.png)
   
4. Conecta la instancia EC2 con EFS para el almacenamiento de `wp-content`.

## 2. Instalación y configuración de WordPress

### 2.1 Instalación de dependencias
Conéctate a la instancia EC2 y ejecuta los siguientes comandos:

```bash
sudo apt update && sudo apt upgrade -y
sudo apt install apache2 php php-mysql mysql-client -y
```
  ![VPC](.imgs/22.png)
  ![VPC](.imgs/23.png)

### 2.2 Descarga e instalación de WordPress
1. Descargamos el archivo.
      ![VPC](.imgs/43.png)
2. Descomprimimos el archivo.
      ![VPC](.imgs/44.png)

### 2.3 Configuración de la base de datos en WordPress
1. Nos conectamos al gestor de base de datos MYSQL:
      ![VPC](.imgs/46.png)
2. Creamos la base de datos para WordPress:
      ![VPC](.imgs/47.png)
3. Nos intentamos conectar a la WordPress desde el navegador:
      ![VPC](.imgs/48.png)
4. Copiamos el contenido de wp-config-sample.php a wp-config.php:
      ![VPC](.imgs/49.png)
5. Modificamos el archivo de wp-config.php:
      ![VPC](.imgs/50.png)
6. Instalamos las dependencias de nfs:
      ![VPC](.imgs/53.png)
7. Instalamos wordpress:
      ![VPC](.imgs/54.png)
8. Y por último ya accederiamos a WordPress
      ![VPC](.imgs/56.png)

## Conclusión
Con esta configuración, WordPress se ejecuta en una arquitectura escalable con almacenamiento compartido y una base de datos gestionada, mejorando la disponibilidad y redundancia del sistema.
