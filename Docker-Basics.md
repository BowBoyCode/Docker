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
