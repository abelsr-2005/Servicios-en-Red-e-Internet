
lang: es

# Actividad #6 - Creación de Imágenes Docker

## Ejemplo 1 - Página Estática

### Paso 1 - Crear Dockerfile
```dockerfile
FROM nginx:latest
COPY index.html /usr/share/nginx/html
```
![Example 1](/Docker/.imgs/Act-6/Fig1.png)

### Paso 2 - Construir la imagen
```bash
docker build -t static_web_image .
```
### Paso 3 - Ejecutar el contenedor
```bash
docker run -d -p 8080:80 static_web_image
```

## Ejemplo 2 - Aplicación PHP

### Paso 1 - Crear Dockerfile
```dockerfile
FROM php:7.4-apache
COPY index.php /var/www/html/
```
![Example 2](/Docker/.imgs/Act-6/Fig2.png)

### Paso 2 - Construir la imagen
```bash
docker build -t php_app_image .
```
### Paso 3 - Ejecutar el contenedor
```bash
docker run -d -p 8080:80 php_app_image
```
![Example 2](/Docker/.imgs/Act-6/Fig3.png)

## Ejemplo 3 - Aplicación Python Flask

### Paso 1 - Crear Dockerfile
```dockerfile
FROM python:3.8-slim-buster
WORKDIR /app
COPY requirements.txt .
RUN pip install -r requirements.txt
COPY app.py .
EXPOSE 5000
CMD ["python", "app.py"]
```
![Example 3](/Docker/.imgs/Act-6/Fig4.png)

### Paso 2 - Construir la imagen
```bash
docker build -t python_app_image .
```
### Paso 3 - Ejecutar el contenedor
```bash
docker run -d -p 8080:5000 python_app_image
```
![Example 3](/Docker/.imgs/Act-6/Fig5.png)
