# 👨‍💻 Práctica Servidores Web 👨‍💻

## 📋 Requisitos

### 1. Instalación del servidor web Apache
- Configurar dos dominios mediante el archivo `/etc/hosts`: 
  - `centro.intranet` (para servir contenido mediante WordPress).
  - `departamentos.centro.intranet` (para una aplicación en Python).

#### Instalación de Apache
![Comando para instalar apache](images/Screenshot_1.png)

---

### 2. Configuración de MySQL y PHP.
#### Cambiar la configuración del fichero /etc/hosts:
![Comando para configurar hosts](images/Screenshot_4.png)
![Comando para configurar hosts](images/Screenshot_5.png)

#### Instalación de MySQL:
![Comando para instalar mysql](images/Screenshot_2.png)

#### Instalación de PHP:
![Comando para instalar mysql](images/Screenshot_3.png)

---

### 3. Instalación y Configuración de WordPress
#### Instalación de WordPress:
![Instalación de WordPress](images/Screenshot_6.png)

#### Descomprimimos la carpeta:
![Descomprimir WordPress](images/Screenshot_7.png)

#### Eliminamos la carpeta de WordPress:
![Eliminar carpeta WordPress](images/Screenshot_8.png)

#### Configuración del VirtualHosts:
![VirtualHosts](images/Screenshot_10.png)
![VirtualHosts](images/Screenshot_11.png)

#### Habilitamos el sitio y reiniciamos apache para aplicar los cambios:
![Hablitar VirtualHosts](images/Screenshot_12.png)

#### Accedemos a `centro.intranet`
![Accedemos a centro.intranet](images/Screenshot_13.png)

#### Accedemos a MySQL creamos la base de datos
![Crear bd en mysql](images/Screenshot_14.png)

#### Creamos el usuario "admin"
![Usuario admin en Mysql](images/Screenshot_15.png)

#### Damos permisos al usuario:
![Dar permisos mysql](images/Screenshot_16.png)
![Dar permisos mysql](images/Screenshot_17.png)

#### Una vez creada la base de datos, podemos continuar con WordPress:
![Bd WordPress](images/Screenshot_18.png)

#### Copiamos el archivo `wp-config-sample.php` y le ponemos de nombre `wp-config.php` y rellenamos los siguientes datos:
![wp-config.php](images/Screenshot_20.png)

#### Ya podemos seguir con la instalación
![WordPress](images/Screenshot_21.png)

#### Tras el anterior paso, ya hemos instalado y configurado WordPress:
![WordPress](images/WordPress.png)
![WordPress](images/Screenshot_22.png)

---

### 4. Instalación y activación del módulo WGSI
#### Creamos el directorio en /var/www y habilitamos el módulo wsgi:
![WordPress](images/Screenshot_23.png)

#### Activamos el módulo:
![WordPress](images/Screenshot_24.png)

#### Configuramos el archivo `departamentos.centro.intranet`
![departamentos.centro.intranet](images/Screenshot_25.png)
![departamentos.centro.intranet](images/Screenshot_26.png)

#### Habilitamos el sitio
![a2ensite](images/Screenshot_28.png)

#### Creamos el archivo que será el index:
![pythonapp](images/Screenshot_29.png)

---

### 5. Despliegue de una Aplicación Python

#### Reiniciamos apache con `systemctl restart apache2` y accedemos al sitio web:
![departamentos.centro.intranet](images/Screenshot_30.png)

#### Uso de contraseñas
#### Crearemos un archivo para guardar los usuarios y contraseñas en un sitio que sea accesible:
![apachepasswd](images/Screenshot_31.png)

#### Creamos los usuarios y contraseñas los cuales se autenticarán:
![apachepasswd](images/Screenshot_32.png)

#### Configuramos el virtualhost de departamentos.centro.intranet:
![apachepasswd](images/Screenshot_33.png)
![apachepasswd](images/Screenshot_34.png)

#### Activamos el módulo `auth_basic` y reiniciamos apache:
![apachepasswd](images/Screenshot_35.png)

#### Accedemos a departamentos.centro.intranet y nos pedirá el usuario:
![apachepasswd](images/Screenshot_36.png)

---

### 6. Instalación y configuración de Awstat.
#### Instalamos Awstats:
![awstats](images/Screenshot_37.png)

#### Activamos el módulo cgi:
![awstats](images/Screenshot_38.png)

#### Reiniciamos apache:
![awstats](images/Screenshot_39.png)

#### Configuramos el archivo de Awstats:
![awstats](images/Screenshot_40.png)
![awstats](images/Screenshot_41.png)
![awstats](images/Screenshot_42.png)

#### Generamos las estadísticas iniciales:
![awstats](images/Screenshot_43.png)

#### Configuramos Apache para awstats:
![awstats](images/Screenshot_44.png)

#### Modificaremos la configuración de awstats en Apache:
![awstats](images/Screenshot_45.png)
![awstats](images/Screenshot_46.png)

#### Habilitamos la configuración y reiniciamos Apache:
![awstats](images/Screenshot_47.png)

#### Accedemos al sitio web podemos ver las estadísticas de visita de nuestro dominio:
![awstats](images/Screenshot_48.png)

---

### 7. Instalación del servidor web nginx:
#### Intalamos Nginx:
![nginx](images/Screenshot_84.png)

#### Modificamos su archivo de configuración:
![nginx](images/Screenshot_50.png)
![nginx](images/Screenshot_51.png)

#### Creamos un nuevo fichero de configuración:
![nginx](images/Screenshot_52.png)
![nginx](images/Screenshot_53.png)

#### Comprobamos la configuración y reiniciamos nginx:
![nginx](images/Screenshot_54.png)

#### Creamos el directorio donde estarán nuestros archivos:
![nginx](images/Screenshot_55.png)

#### Creamos un index:
![nginx](images/Screenshot_56.png)

#### fichero de configuración de antes cambiamos el root a este nuevo directorio:
![nginx](images/Screenshot_57.png)

#### Agregamos el orden de index y el server_name:
![nginx](images/Screenshot_58.png)

#### Agregamos el nombre del dominio al fichero hosts:
![nginx](images/Screenshot_59.png)
![nginx](images/Screenshot_60.png)

#### Accederemos a Nginx por el puerto 8080:
![nginx](images/Screenshot_74.png)

#### Instalamos phpmyadmin:
![nginx](images/Screenshot_76.png)

#### Creamos un enlace simbólico:
![nginx](images/Screenshot_77.png)

#### Cambiaremos los permisos del archivo:
![nginx](images/Screenshot_78.png)

#### Modificamos el archivo:
![nginx](images/Screenshot_79.png)

#### Instalamos php-fpm:
![nginx](images/Screenshot_80.png)

#### Accedemos a phpmyadmin:
![nginx](images/Screenshot_81.png)

#### Creamos un usuario para poder acceder:
![nginx](images/Screenshot_82.png)

#### Accedemos:
![nginx](images/Screenshot_83.png)




