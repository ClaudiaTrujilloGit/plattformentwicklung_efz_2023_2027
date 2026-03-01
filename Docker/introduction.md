Docker introduction
===================

- [Docker introduction](#docker-introduction)
  - [Concepts](#concepts)
  - [Common Dockerfile key instructions](#common-dockerfile-key-instructions)
  - [Example Dockerfile](#example-dockerfile)
  - [Example Docker Compose file](#example-docker-compose-file)
  - [Commands](#commands)
  - [Install Docker (Ubuntu)](#install-docker-ubuntu)
  - [Uninstall Docker (Ubuntu)](#uninstall-docker-ubuntu)

## Concepts
```
Dockerfile       : Plain text file that contains a sequence of step-by-step instructions for building a Docker image.
Docker Image     : Read-only template that contains all the instructions and files needed to create a Docker container.
'->                An image is the blueprint for a machine. It contains a set of instructions detailing exactly what the final product should contain.
Docker Container : Runnable instance of an image. 
'->                It is the isolated space where an app executes, along with its configuration, dependencies, and required software packages.
'->                An individual container is managed with the Docker CLI.
'->                Multiple ones are administered using Docker Compose or an orchestration tool like Kubernetes.
Docker Compose   : Tool that simplifies the definition and management of multi-container applications.
'->                Uses a single configuration file, typically named docker-compose.yml.
```

## Common Dockerfile key instructions
```
FROM              : Specifies the base image for a new build stage.
RUN               : Executes commands during the image build process.
COPY or ADD       : Copies files from the build context into the image.
CMD or ENTRYPOINT : Defines the command that runs when the container starts.
ENV               : Sets environment variables that will be available during the build and at runtime.
WORKDIR           : Sets the working directory for the subsequent RUN, CMD, ENTRYPOINT, COPY, and ADD instructions.
```
## Example Dockerfile
```
FROM python:3.9-slim
WORKDIR /app
COPY requirements.txt .
RUN pip install -r requirements.txt
COPY . .
CMD ["python", "app.py"]
```

## Example Docker Compose file
```
services:
  web:
    build: ./web  # Build the image from Dockerfile in the ./web directory
    ports:
      - "8000:8000"  # Map host port 8000 to container port 8000
    depends_on:
      - db     # Wait for the db service to be started
      - redis  # Wait for the redis service to be started

  db:
    image: postgres:15  # Use the official PostgreSQL 15 image
    environment:
      POSTGRES_USER: myuser       # Set database username
      POSTGRES_PASSWORD: mypassword  # Set database password
      POSTGRES_DB: mydb           # Set initial database name
    volumes:
      - db-data:/var/lib/postgresql/data  # Persist database data using a named volume

  redis:
    image: redis:alpine  # Use a lightweight Redis image for caching

volumes:
  db-data:  # Define a named volume to store database data
```

## Commands
```
docker ps                                       : Asks the Docker Daemon to list all currently running containers.
'-> docker ps -a                                : Lists all containers, including those that are stopped.
docker pull <name>:<tag>                        : Downloads an image from the registry.
'-> docker pull ubuntu:latest                   : Download the latest official Ubuntu image.
docker images                                   : Lists the images you have locally downloaded.
docker search nginx                             : Search for images on Docker Hub, eg. nginx.
docker rmi <image>                              : Deletes a local image.
docker build -t your-image-name:latest .        : Builds a container in the current directory using a specific image.
docker run <image>                              : Runs a container.
docker run -it ubuntu /bin/bash                 : Creates a docker container and runs a command inside it.
docker run -d --name webserver -p 8080:80 nginx : Runs a container, eg. nginx.
docker start webserver                          : Start a container, eg. webserver.
docker stop <container>                         : Gracefully stops a running container.
docker rm <container>                           : Deletes a container.
docker compose up -d                            : Builds and starts all the services defined in the docker-compose.yml file in the background.
'->                                               -d for detached flag.
docker logs <container_name>                    : Shows the application’s stdout and stderr.
docker login <my-registry.example.com>          : Log in to a registry.
docker image prune                              : Rwmove unused Docker images.
docker container prune                          : Delete stopped containers.
docker volume prune                             : Remove unused volumes.
docker network prune                            : Remove unused networks.
journalctl -u docker.service                    : See Docker logs.
docker inspect <image> or <container id>        : Shows container or images details.
docker top <container id>                       : Shows processes inside the container.
docker compose up                               : Starts a multi-container app.
```

## Install Docker (Ubuntu)
```
> Step 1: Set up Docker's apt repository:
-----------------------------------------

# Add Docker's official GPG key:
sudo apt update
sudo apt install ca-certificates curl
sudo install -m 0755 -d /etc/apt/keyrings
sudo curl -fsSL https://download.docker.com/linux/ubuntu/gpg -o /etc/apt/keyrings/docker.asc
sudo chmod a+r /etc/apt/keyrings/docker.asc

# Add the repository to Apt sources:
sudo tee /etc/apt/sources.list.d/docker.sources <<EOF
Types: deb
URIs: https://download.docker.com/linux/ubuntu
Suites: $(. /etc/os-release && echo "${UBUNTU_CODENAME:-$VERSION_CODENAME}")
Components: stable
Signed-By: /etc/apt/keyrings/docker.asc
EOF

sudo apt update

> Step 2: Install the Docker packages:
--------------------------------------

sudo apt install docker-ce docker-ce-cli containerd.io docker-buildx-plugin docker-compose-plugin
sudo systemctl status docker

> Step 3: Verify that the installation is successful by running the hello-world image:
--------------------------------------------------------------------------------------

sudo docker run hello-world
```

## Uninstall Docker (Ubuntu)
```
> Step 1: Uninstall the Docker Engine, CLI, containerd, and Docker Compose packages:
------------------------------------------------------------------------------------

sudo apt purge docker-ce docker-ce-cli containerd.io docker-buildx-plugin docker-compose-plugin docker-ce-rootless-extras

> Step 2: Delete all images, containers and volumes:
----------------------------------------------------

sudo rm -rf /var/lib/docker
sudo rm -rf /var/lib/containerd

> Step 3: Remove source list and keyrings:
------------------------------------------

sudo rm /etc/apt/sources.list.d/docker.sources
sudo rm /etc/apt/keyrings/docker.asc

> Step 4 (optional): You have to delete any edited configuration files manually.
--------------------------------------------------------------------------------

.
```