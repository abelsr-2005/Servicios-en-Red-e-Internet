# Actividad #2 - Uso Básico de Docker

## Ejercicios
### Comandos iniciales
```bash
docker run hello-world
docker images
docker ps -a
```
![Running Hello World Image](/Docker/.imgs/Act-1/Fig3.png)
![Docker Images](/Docker/.imgs/Act-2/Fig1.png)
![Docker ps -a](/Docker/.imgs/Act-2/Fig2.png)

### Creación de imagen personalizada
```dockerfile
FROM node:lts-alpine
WORKDIR /app
COPY . .
RUN yarn install --production
CMD ["node", "src/index.js"]
EXPOSE 3000
```
![Dockerfile](/Docker/.imgs/Act-2/Fig3.png)
```bash
docker build -t getting-started .
docker run -d -p 127.0.0.1:3000:3000 getting-started
```
![Docker run](/Docker/.imgs/Act-2/Fig5.png)
