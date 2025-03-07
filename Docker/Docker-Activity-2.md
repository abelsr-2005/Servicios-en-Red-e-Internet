
lang: es

# Actividad #2 - Uso Básico de Docker

## Paso 1 - Ejecutar el primer contenedor
```bash
docker run hello-world
```
![Running Hello World Image](/Docker/.imgs/Act-1/Fig3.png)

## Paso 2 - Mostrar imágenes disponibles
```bash
docker images
```
![Docker Images](/Docker/.imgs/Act-2/Fig1.png)

## Paso 3 - Listar todos los contenedores
```bash
docker ps -a
```
![Docker ps -a](/Docker/.imgs/Act-2/Fig2.png)

## Paso 4 - Crear un Dockerfile y construir la imagen
```dockerfile
FROM node:lts-alpine
WORKDIR /app
COPY . .
RUN yarn install --production
CMD ["node", "src/index.js"]
EXPOSE 3000
```
![Dockerfile](/Docker/.imgs/Act-2/Fig3.png)

## Paso 5 - Construir la imagen
```bash
docker build -t getting-started .
```
![Docker build](/Docker/.imgs/Act-2/Fig4.png)

## Paso 6 - Ejecutar el contenedor
```bash
docker run -d -p 127.0.0.1:3000:3000 getting-started
```
![Docker run](/Docker/.imgs/Act-2/Fig5.png)
