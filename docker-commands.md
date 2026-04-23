# Docker Commands Reference

## 1. Installation & Version

- **Check Docker version:**

  ```
  docker --version
  ```

- **Check detailed Docker info:**

  ```
  docker info
  ```

- **Check Docker Compose version:**

  ```
  docker compose version
  ```

---

## 2. Images

- **Pull an image from Docker Hub:**

  ```
  docker pull <image-name>
  ```

- **Pull a specific version/tag:**

  ```
  docker pull <image-name>:<tag>
  ```

- **List all local images:**

  ```
  docker images
  ```

- **Remove an image:**

  ```
  docker rmi <image-name>
  ```

- **Remove all unused images:**

  ```
  docker image prune -a
  ```

- **Build an image from a Dockerfile:**

  ```
  docker build -t <image-name>:<tag> .
  ```

- **Build without using cache:**

  ```
  docker build --no-cache -t <image-name>:<tag> .
  ```

- **Tag an image:**

  ```
  docker tag <source-image>:<tag> <target-image>:<tag>
  ```

- **Inspect an image:**

  ```
  docker image inspect <image-name>
  ```

- **View image history (layers):**

  ```
  docker history <image-name>
  ```

---

## 3. Containers

- **Run a container:**

  ```
  docker run <image-name>
  ```

- **Run a container in detached (background) mode:**

  ```
  docker run -d <image-name>
  ```

- **Run a container with a custom name:**

  ```
  docker run --name <container-name> <image-name>
  ```

- **Run a container and map ports:**

  ```
  docker run -p <host-port>:<container-port> <image-name>
  ```

- **Run a container with an environment variable:**

  ```
  docker run -e MY_VAR=value <image-name>
  ```

- **Run a container interactively:**

  ```
  docker run -it <image-name> /bin/bash
  ```

- **Run a container and remove it after it exits:**

  ```
  docker run --rm <image-name>
  ```

- **List running containers:**

  ```
  docker ps
  ```

- **List all containers (including stopped):**

  ```
  docker ps -a
  ```

- **Stop a running container:**

  ```
  docker stop <container-name or id>
  ```

- **Start a stopped container:**

  ```
  docker start <container-name or id>
  ```

- **Restart a container:**

  ```
  docker restart <container-name or id>
  ```

- **Kill a container immediately:**

  ```
  docker kill <container-name or id>
  ```

- **Remove a stopped container:**

  ```
  docker rm <container-name or id>
  ```

- **Remove all stopped containers:**

  ```
  docker container prune
  ```

- **Inspect a container:**

  ```
  docker inspect <container-name or id>
  ```

- **View container logs:**

  ```
  docker logs <container-name or id>
  ```

- **Follow live container logs:**

  ```
  docker logs -f <container-name or id>
  ```

- **View resource usage stats:**

  ```
  docker stats
  ```

- **View running processes inside a container:**

  ```
  docker top <container-name or id>
  ```

---

## 4. Executing Commands in Containers

- **Execute a command in a running container:**

  ```
  docker exec <container-name> <command>
  ```

- **Open an interactive shell inside a running container:**

  ```
  docker exec -it <container-name> /bin/bash
  ```

- **Open a shell in Alpine-based containers:**

  ```
  docker exec -it <container-name> /bin/sh
  ```

---

## 5. Volumes

- **Create a volume:**

  ```
  docker volume create <volume-name>
  ```

- **List all volumes:**

  ```
  docker volume ls
  ```

- **Inspect a volume:**

  ```
  docker volume inspect <volume-name>
  ```

- **Remove a volume:**

  ```
  docker volume rm <volume-name>
  ```

- **Remove all unused volumes:**

  ```
  docker volume prune
  ```

- **Run a container with a named volume:**

  ```
  docker run -v <volume-name>:<container-path> <image-name>
  ```

- **Run a container with a bind mount:**

  ```
  docker run -v <host-path>:<container-path> <image-name>
  ```

---

## 6. Networks

- **List all networks:**

  ```
  docker network ls
  ```

- **Create a network:**

  ```
  docker network create <network-name>
  ```

- **Inspect a network:**

  ```
  docker network inspect <network-name>
  ```

- **Connect a container to a network:**

  ```
  docker network connect <network-name> <container-name>
  ```

- **Disconnect a container from a network:**

  ```
  docker network disconnect <network-name> <container-name>
  ```

- **Remove a network:**

  ```
  docker network rm <network-name>
  ```

- **Remove all unused networks:**

  ```
  docker network prune
  ```

- **Run a container on a specific network:**

  ```
  docker run --network <network-name> <image-name>
  ```

---

## 7. Docker Hub (Registry)

- **Log in to Docker Hub:**

  ```
  docker login
  ```

- **Log out from Docker Hub:**

  ```
  docker logout
  ```

- **Push an image to Docker Hub:**

  ```
  docker push <username>/<image-name>:<tag>
  ```

- **Pull an image from Docker Hub:**

  ```
  docker pull <username>/<image-name>:<tag>
  ```

- **Search for an image on Docker Hub:**

  ```
  docker search <image-name>
  ```

---

## 8. Dockerfile Instructions

- **Sample Dockerfile structure:**

  ```dockerfile
  FROM ubuntu:22.04
  LABEL maintainer="yourname@email.com"
  ENV APP_DIR=/app
  WORKDIR /app
  COPY . .
  RUN apt-get update && apt-get install -y python3
  EXPOSE 8080
  CMD ["python3", "app.py"]
  ```

- **Common Dockerfile instructions:**

  | Instruction | Purpose |
  |-------------|---------|
  | `FROM`      | Base image to build upon |
  | `RUN`       | Execute a command during build |
  | `COPY`      | Copy files from host to image |
  | `ADD`       | Like COPY but supports URLs and tar extraction |
  | `ENV`       | Set environment variables |
  | `WORKDIR`   | Set the working directory |
  | `EXPOSE`    | Document which port the container listens on |
  | `CMD`       | Default command when container starts |
  | `ENTRYPOINT`| Like CMD but not overridden by docker run args |
  | `ARG`       | Build-time variable |
  | `VOLUME`    | Create a mount point |
  | `LABEL`     | Add metadata to the image |

---

## 9. Docker Compose

- **Start services defined in docker-compose.yml:**

  ```
  docker compose up
  ```

- **Start services in detached mode:**

  ```
  docker compose up -d
  ```

- **Build images before starting:**

  ```
  docker compose up --build
  ```

- **Stop and remove containers:**

  ```
  docker compose down
  ```

- **Stop and remove containers including volumes:**

  ```
  docker compose down -v
  ```

- **View logs for all services:**

  ```
  docker compose logs
  ```

- **Follow live logs:**

  ```
  docker compose logs -f
  ```

- **List running services:**

  ```
  docker compose ps
  ```

- **Run a one-off command in a service:**

  ```
  docker compose exec <service-name> /bin/bash
  ```

- **Scale a service to multiple instances:**

  ```
  docker compose up --scale <service-name>=3
  ```

- **Sample docker-compose.yml structure:**

  ```yaml
  version: "3.8"
  services:
    web:
      image: nginx
      ports:
        - "8080:80"
      volumes:
        - ./html:/usr/share/nginx/html
      networks:
        - mynet

    db:
      image: postgres:15
      environment:
        POSTGRES_PASSWORD: secret
      volumes:
        - pgdata:/var/lib/postgresql/data
      networks:
        - mynet

  volumes:
    pgdata:

  networks:
    mynet:
  ```

---

## 10. Copying Files

- **Copy a file from host to container:**

  ```
  docker cp <host-path> <container-name>:<container-path>
  ```

- **Copy a file from container to host:**

  ```
  docker cp <container-name>:<container-path> <host-path>
  ```

---

## 11. Saving & Loading Images

- **Save an image to a tar file:**

  ```
  docker save -o <filename>.tar <image-name>
  ```

- **Load an image from a tar file:**

  ```
  docker load -i <filename>.tar
  ```

- **Export a container's filesystem:**

  ```
  docker export <container-name> -o <filename>.tar
  ```

- **Import a container filesystem as an image:**

  ```
  docker import <filename>.tar <image-name>:<tag>
  ```

---

## 12. System Cleanup

- **Remove all stopped containers, unused networks, dangling images and build cache:**

  ```
  docker system prune
  ```

- **Remove everything including unused images:**

  ```
  docker system prune -a
  ```

- **Check disk usage by Docker:**

  ```
  docker system df
  ```

---

## 13. Docker Swarm (Orchestration)

- **Initialize a swarm:**

  ```
  docker swarm init
  ```

- **Join a swarm as a worker:**

  ```
  docker swarm join --token <token> <manager-ip>:2377
  ```

- **List nodes in the swarm:**

  ```
  docker node ls
  ```

- **Deploy a stack from a compose file:**

  ```
  docker stack deploy -c docker-compose.yml <stack-name>
  ```

- **List stacks:**

  ```
  docker stack ls
  ```

- **List services in a stack:**

  ```
  docker stack services <stack-name>
  ```

- **Remove a stack:**

  ```
  docker stack rm <stack-name>
  ```

- **Leave the swarm:**

  ```
  docker swarm leave --force
  ```
