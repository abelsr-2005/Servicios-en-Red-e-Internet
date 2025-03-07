
lang: es

# Actividad #1 - Instalación de Docker en Fedora

## Paso 1 - Configurar el repositorio
```bash
sudo dnf -y install dnf-plugins-core
sudo dnf config-manager --add-repo https://download.docker.com/linux/fedora/docker-ce.repo
```
![Add Docker Packages](/Docker/.imgs/Act-1/Fig1.png)

## Paso 2 - Instalar Docker
```bash
sudo dnf install docker-ce docker-ce-cli containerd.io docker-buildx-plugin docker-compose-plugin
```
![Install Docker Packages](/Docker/.imgs/Act-1/Fig2.png)

## Paso 3 - Activar y probar Docker
```bash
sudo systemctl enable --now docker
sudo docker run hello-world
```
![Start and test docker installation](/Docker/.imgs/Act-1/Fig3.png)
