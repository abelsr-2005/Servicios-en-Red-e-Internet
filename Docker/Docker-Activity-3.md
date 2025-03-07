
lang: es

# Actividad #3 - Gestión de Imágenes y Contenedores

## Paso 1 - Descargar imágenes
```bash
docker pull ubuntu
docker pull hello-world
docker pull nginx
```
![Steps 1-4](/Docker/.imgs/Act-3/Fig1.png)

## Paso 2 - Ejecutar contenedores con nombres personalizados
```bash
docker run --name myhello1 hello-world
```
![Step 5](/Docker/.imgs/Act-3/Fig2.png)

```bash
docker run --name myhello2 hello-world
```
![Step 6](/Docker/.imgs/Act-3/Fig3.png)

```bash
docker run --name myhello3 hello-world
```
![Step 7](/Docker/.imgs/Act-3/Fig4.png)

## Paso 3 - Mostrar contenedores en ejecución
```bash
docker ps
```

## Paso 4 - Detener y borrar contenedores
```bash
docker stop myhello1
docker stop myhello2
docker rm myhello1
```
## Paso 5 - Mostrar todos los contenedores
```bash
docker ps -a
```
![Steps 8-12](/Docker/.imgs/Act-3/Fig5.png)

## Paso 6 - Borrar todos los contenedores
```bash
docker stop $(docker ps -aq)
docker rm $(docker ps -aq)
```
![Step 13](/Docker/.imgs/Act-3/Fig6.png)
