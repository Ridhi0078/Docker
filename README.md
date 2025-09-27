# Docker Learning Repository

This repository contains practical examples and exercises for learning **Docker**, including images, containers, port mappings, environment variables, Dockerizing a Node.js application, and using Docker Compose.

---

## 1. Problem Statement
The goal of this repository is to provide hands-on experience with Docker concepts and commands, demonstrating containerization, image management, environment variables, and multi-container orchestration using Docker Compose.

---

## 2. Installation of Docker CLI and Desktop

**Docker CLI** and **Docker Desktop** allow you to run and manage containers on your machine.

### Installation Steps:

- **Windows / Mac:**
  1. Download Docker Desktop: [https://www.docker.com/products/docker-desktop](https://www.docker.com/products/docker-desktop)
  2. Install and start Docker Desktop.
  3. Enable WSL 2 (Windows) if prompted.

### Verify Installation:
```bash
docker --version
docker info
```

---

## 3. Understanding Images vs Containers
- Image: Docker image is a lightweight, standalone, executable package that includes everything needed to run one application: code, runtime, system tools, system libraries and settings. Its essentially a blueprint or a template. Images are built from a dockerfile, which contains instructions for assembling the image layer by layer.
- Containers: A Docker container is a standardized, isolated, and executable software package that bundles an application and all its dependencies, including libraries, system tools, code, and runtime, into a single, self-contained unit. This unit is designed to run consistently and reliably across different computing environments, from a developer's local machine to a production server or cloud platform.

```bash
docker images           # List all images
docker ps               # List running containers
docker ps -a            # List all containers
docker rm <container>   # Remove container
docker rmi <image>      # Remove image
```

---

## 4. Running Ubuntu image in container
```bash
# Pull the image
docker pull ubuntu:latest

# Run Ubuntu container interactively
docker run -it ubuntu:latest /bin/bash

# Exit the container
exit
```

---

## 5. Multiple Containers
Docker allows running multiple containers simultaneously:
```bash
docker run -d --name webserver nginx:latest
docker run -d --name redis-server redis:latest
docker ps
```

---

## 6. PORT Mappings:
Port mapping in Docker, also known as port publishing or port forwarding, enables communication between services running inside a Docker container and the host machine or external networks. By default, Docker containers run in isolation, and their network services are not directly accessible from outside the container's network. Port mapping bridges this gap, making containerized applications reachable.

```bash
docker run -p <HOST_PORT>:<CONTAINER_PORT> <IMAGE_NAME>

eg: docker run -d -p 8080:80 nginx
```

--- 

## 7. Environment Variables:
Pass environment variables to containers:

```bash
docker run -d -e NODE_ENV=production -e PORT=3000 --name my-node-app my-node-image
```
- Inside the container, you can access these using process.env (Node.js) or env (Linux).

---

