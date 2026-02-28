## Concepts
```
Docker Image     : Read-only template that contains all the instructions and files needed to create a Docker container.
'->                An image is the blueprint for a machine. It contains a set of instructions detailing exactly what the final product should contain.
Dockerfile       : Plain text file that contains a sequence of step-by-step instructions for building a Docker image.
Docker Container : Runnable instance of an image. 
'->                It is the isolated space where an app executes, along with its configuration, dependencies, and required software packages.
'->                An individual container is managed with the Docker CLI.
'->                Multiple ones are administered using Docker Compose or an orchestration tool like Kubernetes.
Docker Compose   : Tool that simplifies the definition and management of multi-container applications.
'->                Uses a single configuration file, typically named docker-compose.yml
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

## Commands
```
docker ps                                : Asks the Docker Daemon to list all currently running containers.
'-> docker ps -a                         : Lists all containers, including those that are stopped.
docker pull <name>:<tag>                 : Downloads an image from the registry.
'-> docker pull ubuntu:latest            : Download the latest official Ubuntu image.
docker images                            : Lists the images you have locally downloaded.
docker rmi <image>                       : Deletes a local image.
docker build -t your-image-name:latest . : Builds a container in the current directory using a specific image.
docker run -it ubuntu /bin/bash          : Creates a docker container and runs a command inside it.
docker stop <container>                  : Gracefully stops a running container.
docker rm <container>                    : Deletes a container.
docker compose up -d                     : Builds and starts all the services defined in the docker-compose.yml file in the background.
'->                                        -d for detached flag.
docker logs <container_name>             : Shows the application’s stdout and stderr.
docker login <my-registry.example.com>   : Log in to a registry.
```

## Docker installation
```
Step 1: Set up Docker's apt repository:
'->     # Add Docker's official GPG key:
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

Step 2: Install the Docker packages:
'->     sudo apt install docker-ce docker-ce-cli containerd.io docker-buildx-plugin docker-compose-plugin
        sudo systemctl status docker

Step 3: Verify that the installation is successful by running the hello-world image:
'->     sudo docker run hello-world
```

## Uninstall Docker
```
Step 1: Uninstall the Docker Engine, CLI, containerd, and Docker Compose packages:
'->     sudo apt purge docker-ce docker-ce-cli containerd.io docker-buildx-plugin docker-compose-plugin docker-ce-rootless-extras

Step 2: Delete all images, containers and volumes:
'->     sudo rm -rf /var/lib/docker
        sudo rm -rf /var/lib/containerd

Step 3: Remove source list and keyrings:
'->     sudo rm /etc/apt/sources.list.d/docker.sources
        sudo rm /etc/apt/keyrings/docker.asc

Step 4 (optional): You have to delete any edited configuration files manually.
```