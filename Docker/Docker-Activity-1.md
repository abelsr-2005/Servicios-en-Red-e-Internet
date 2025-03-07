# Actividad #1 - Instalación de Docker en ~~Ubuntu~~ Fedora

## Ejercicio

Instalar Docker en Ubuntu siguiendo las instrucciones de los siguientes artículos:

## Pasos:

Before you install Docker Engine for the first time on a new host machine, you need to set up the Docker repository. Afterward, you can install and update Docker from the repository.

Install the `dnf-plugins-core` package (which provides the commands to manage your DNF repositories) and set up the repository.

```bash
sudo dnf -y install dnf-plugins-core
sudo dnf-3 config-manager --add-repo https://download.docker.com/linux/fedora/docker-ce.repo
```

![Add Docker Packages](/Docker/.imgs/Act-1/Fig1.png)

### [Install Docker Engine](https://docs.docker.com/engine/install/fedora/#install-docker-engine)

1. Install the Docker packages.

    To install the latest version, run:

    ```bash
    sudo dnf install docker-ce docker-ce-cli containerd.io docker-buildx-plugin docker-compose-plugin
    ```

    ![Install Docker Packages](/Docker/.imgs/Act-1/Fig2.png)

    This command installs Docker, but it doesn't start Docker. It also creates a `docker` group, however, it doesn't add any users to the group by default.

2. Start Docker Engine.

    ```bash
    sudo systemctl enable --now docker
    ```

    This configures the Docker systemd service to start automatically when you boot your system. If you don't want Docker to start automatically, use `sudo systemctl start docker` instead.

3. Verify that the installation is successful by running the `hello-world` image:

    ```bash
    sudo docker run hello-world
    ```

    This command downloads a test image and runs it in a container. When the container runs, it prints a confirmation message and exits.

    ![Start and test docker installation](/Docker/.imgs/Act-1/Fig3.png)

You have now successfully installed and started Docker Engine.
