# Configuración de WordPress con AWS y EFS

Esta guía detalla los pasos para implementar WordPress en AWS utilizando Amazon Elastic File System (EFS) para almacenamiento compartido. 

## Prerrequisitos

- Una cuenta de AWS activa.
- Conocimientos básicos sobre EC2, VPC y EFS.
- Acceso a la consola de AWS y privilegios suficientes.

## Paso 1: Configurar la VPC y subredes

1. **Crear una VPC**
   - En la consola de VPC, crea una nueva VPC con un rango de direcciones CIDR (ej. `10.0.0.0/16`).
   - Captura: ![VPC](https://github.com/abelsr-2005/Servicios-en-Red-e-Internet/raw/main/AWS/.imgs/1.png)

2. **Crear subredes**
   - Agrega subredes en diferentes Zonas de Disponibilidad.
   - Captura: ![Subredes](https://github.com/abelsr-2005/Servicios-en-Red-e-Internet/raw/main/AWS/.imgs/2.png)

## Paso 2: Crear el sistema de archivos EFS

1. **Crear EFS**
   - Navega a la consola de EFS y crea un nuevo sistema de archivos.
   - Captura: ![EFS](https://github.com/abelsr-2005/Servicios-en-Red-e-Internet/raw/main/AWS/.imgs/3.png)

2. **Configurar puntos de montaje**
   - Agrega puntos de montaje en las subredes creadas.
   - Captura: ![Puntos de montaje](https://github.com/abelsr-2005/Servicios-en-Red-e-Internet/raw/main/AWS/.imgs/4.png)

3. **Configurar reglas de seguridad**
   - Asegúrate de que los grupos de seguridad permitan el tráfico NFS (puerto 2049).
   - Captura: ![Reglas EFS](https://github.com/abelsr-2005/Servicios-en-Red-e-Internet/raw/main/AWS/.imgs/5.png)

## Paso 3: Lanzar instancias EC2 y montar EFS

1. **Lanzar instancias EC2**
   - Inicia instancias EC2 en las subredes públicas.
   - Captura: ![Instancias EC2](https://github.com/abelsr-2005/Servicios-en-Red-e-Internet/raw/main/AWS/.imgs/6.png)

2. **Instalar NFS Utilities**
   ```bash
   sudo yum install -y nfs-utils
   ```

3. **Montar el sistema de archivos EFS**
   ```bash
   sudo mkdir -p /var/www/html
   sudo mount -t nfs4 -o nfsvers=4.1 fs-<ID_EFS>.efs.<region>.amazonaws.com:/ /var/www/html
   ```

4. **Configuración para montaje automático**
   ```bash
   echo "fs-<ID_EFS>.efs.<region>.amazonaws.com:/ /var/www/html nfs4 defaults,_netdev 0 0" | sudo tee -a /etc/fstab
   ```

## Paso 4: Instalar y configurar LAMP

1. **Instalar Apache, PHP y MariaDB**
   ```bash
   sudo yum install -y httpd mariadb-server
   sudo amazon-linux-extras enable php7.4
   sudo yum install -y php php-mysqlnd
   sudo systemctl start httpd
   sudo systemctl enable httpd
   sudo systemctl start mariadb
   sudo systemctl enable mariadb
   ```

2. **Configurar la base de datos para WordPress**
   ```sql
   CREATE DATABASE wordpress_db;
   CREATE USER 'wordpress_user'@'localhost' IDENTIFIED BY 'tu_contraseña';
   GRANT ALL PRIVILEGES ON wordpress_db.* TO 'wordpress_user'@'localhost';
   FLUSH PRIVILEGES;
   ```

## Paso 5: Descargar y configurar WordPress

1. **Descargar e instalar WordPress**
   ```bash
   wget https://wordpress.org/latest.tar.gz
   tar -xzf latest.tar.gz
   sudo mv wordpress/* /var/www/html/
   ```

2. **Configurar permisos**
   ```bash
   sudo chown -R apache:apache /var/www/html
   sudo chmod -R 755 /var/www/html
   ```

3. **Editar el archivo `wp-config.php`**
   ```bash
   sudo cp /var/www/html/wp-config-sample.php /var/www/html/wp-config.php
   sudo nano /var/www/html/wp-config.php
   ```
   Cambia los siguientes valores:
   ```php
   define('DB_NAME', 'wordpress_db');
   define('DB_USER', 'wordpress_user');
   define('DB_PASSWORD', 'tu_contraseña');
   define('DB_HOST', 'localhost');
   ```

4. **Reiniciar Apache**
   ```bash
   sudo systemctl restart httpd
   ```

## Paso 6: Completar la instalación de WordPress

1. Accede a `http://<tu_dominio_o_IP>/` en tu navegador.
2. Sigue las instrucciones en pantalla para completar la instalación de WordPress.
3. Captura: ![Instalación WordPress](https://github.com/abelsr-2005/Servicios-en-Red-e-Internet/raw/main/AWS/.imgs/52.png)

## Conclusión

Hemos configurado WordPress en AWS utilizando Amazon EFS para almacenamiento compartido, lo que permite una solución escalable y altamente disponible.
