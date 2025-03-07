lang: es


# Actividad #1 - Instalación de Docker en Fedora

## Guía oficial
Para instalar Docker en Fedora, te sugiero seguir la [guía oficial](https://docs.docker.com/engine/install/fedora/), asegurándote de tener siempre la última versión.

## Instrucciones
```bash
sudo dnf -y install dnf-plugins-core
sudo dnf config-manager --add-repo https://download.docker.com/linux/fedora/docker-ce.repo
sudo dnf install docker-ce docker-ce-cli containerd.io docker-buildx-plugin docker-compose-plugin
sudo systemctl enable --now docker
sudo docker run hello-world
```
![Add Docker Packages](/Docker/.imgs/Act-1/Fig1.png)
![Install Docker Packages](/Docker/.imgs/Act-1/Fig2.png)
![Start and test docker installation](/Docker/.imgs/Act-1/Fig3.png)
