
# Actividad #3 - Gestión de Imágenes y Contenedores

## Ejercicio
```bash
docker pull ubuntu
docker pull hello-world
docker pull nginx
docker images
docker run --name myhello1 hello-world
docker run --name myhello2 hello-world
docker run --name myhello3 hello-world
docker ps
docker stop myhello1 myhello2
docker rm myhello1
docker ps -a
docker stop $(docker ps -aq)
docker rm $(docker ps -aq)
```
![Steps 1-4](/Docker/.imgs/Act-3/Fig1.png)
![Step 7](/Docker/.imgs/Act-3/Fig4.png)
![Steps 8-12](/Docker/.imgs/Act-3/Fig5.png)
![Step 13](/Docker/.imgs/Act-3/Fig6.png)
