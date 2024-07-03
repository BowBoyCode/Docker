# DockerMisc
Certainly! Here is a list of commonly used Docker commands along with a brief explanation for each:

### Docker Installation
1. **Install Docker**
    ```bash
    sudo apt-get update
    sudo apt-get install docker-ce docker-ce-cli containerd.io
    ```

### Docker Basics
2. **Check Docker version**
    ```bash
    docker --version
    ```

3. **Run a container**
    ```bash
    docker run <image>
    ```
    Example:
    ```bash
    docker run hello-world
    ```

4. **List all containers**
    ```bash
    docker ps
    ```
    - To include stopped containers:
    ```bash
    docker ps -a
    ```

5. **Stop a container**
    ```bash
    docker stop <container_id>
    ```

6. **Start a container**
    ```bash
    docker start <container_id>
    ```

7. **Restart a container**
    ```bash
    docker restart <container_id>
    ```

8. **Remove a container**
    ```bash
    docker rm <container_id>
    ```

9. **Remove all stopped containers**
    ```bash
    docker container prune
    ```

### Docker Images
10. **List Docker images**
    ```bash
    docker images
    ```

11. **Pull an image from Docker Hub**
    ```bash
    docker pull <image>
    ```

12. **Remove an image**
    ```bash
    docker rmi <image_id>
    ```

13. **Build an image from a Dockerfile**
    ```bash
    docker build -t <image_name> .
    ```

### Docker Volumes
14. **Create a volume**
    ```bash
    docker volume create <volume_name>
    ```

15. **List volumes**
    ```bash
    docker volume ls
    ```

16. **Remove a volume**
    ```bash
    docker volume rm <volume_name>
    ```

### Docker Networks
17. **Create a network**
    ```bash
    docker network create <network_name>
    ```

18. **List networks**
    ```bash
    docker network ls
    ```

19. **Remove a network**
    ```bash
    docker network rm <network_name>
    ```

### Docker Compose
20. **Run Docker Compose**
    ```bash
    docker-compose up
    ```

21. **Run Docker Compose in the background**
    ```bash
    docker-compose up -d
    ```

22. **Stop Docker Compose**
    ```bash
    docker-compose down
    ```

### Docker Logs
23. **View container logs**
    ```bash
    docker logs <container_id>
    ```

### Docker Exec
24. **Run a command in a running container**
    ```bash
    docker exec -it <container_id> <command>
    ```
    Example:
    ```bash
    docker exec -it <container_id> /bin/bash
    ```

    ### Docker Tagging
24. **Tag a container**
    ```bash
    docker exec -it <container_id> <command>
    ```
    Example:
    ```bash
    docker exec -it <container_id> /bin/bash
    ```

    When running a Docker container, you can tag and name your container for easier management and identification. Here’s how you can do that:

### Tagging an Image

Tagging an image is useful for versioning your Docker images. When you build an image, you can assign a tag to it.

```bash
docker build -t <repository>:<tag> .
```

Example:
```bash
docker build -t myapp:1.0 .
```

You can also tag an existing image with a new tag:

```bash
docker tag <image_id> <repository>:<tag>
```

Example:
```bash
docker tag 123456789abc myapp:latest
```

### Naming a Container

When running a Docker container, you can assign it a name for easier reference:

```bash
docker run --name <container_name> <image>
```

Example:
```bash
docker run --name mycontainer myapp:1.0
```

### Full Command Example

Here is an example that combines tagging an image and running a named container:

1. **Build an Image with a Tag**

```bash
docker build -t myapp:v1.0 .
```

2. **Run a Container with a Name**

```bash
docker run --name myapp_container myapp:v1.0
```

### Explanation

1. **docker build -t myapp:v1.0 .**
   - `-t myapp:v1.0`: Tags the image as `myapp` with the tag `v1.0`.
   - `.`: Specifies the current directory as the build context, where the Dockerfile is located.

2. **docker run --name myapp_container myapp:v1.0**
   - `--name myapp_container`: Names the container `myapp_container`.
   - `myapp:v1.0`: Specifies the image `myapp` with the tag `v1.0` to run.

### Additional Options

You can also add other options to the `docker run` command for more functionality:

- **Running in detached mode**:
  ```bash
  docker run -d --name myapp_container myapp:v1.0
  ```

- **Mapping ports**:
  ```bash
  docker run -d -p 8080:80 --name myapp_container myapp:v1.0
  ```

- **Mounting volumes**:
  ```bash
  docker run -d -v /host/path:/container/path --name myapp_container myapp:v1.0
  ```
