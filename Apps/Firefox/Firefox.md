To resolve the `libEGL missing` issue when running Firefox in a Docker container, you need to install the `libegl1` package, which provides the required `libEGL` libraries. Let's modify the solution to include this missing library.

### Updated Steps in Markdown:

---

# Running Firefox in a Docker Container with Internet Access (Fix for `libpci` and `libEGL` missing)

### 1. **Create a Dockerfile**

In a directory of your choice, create a file named `Dockerfile` with the following content:

```Dockerfile
# Use Debian base image to avoid Snap and install Firefox ESR
FROM debian:bullseye-slim

# Install necessary packages including libEGL and libpci
RUN apt-get update && \
    apt-get install -y firefox-esr x11-apps libgl1-mesa-glx libxrender1 \
    libxtst6 libxi6 libgl1 libpci3 libegl1 && \
    apt-get clean

# Add user to avoid running as root
RUN useradd -ms /bin/bash dockeruser

# Switch to non-root user
USER dockeruser

# Run Firefox by default
CMD ["firefox"]
```

### 2. **Build the Docker Image**

Run the following command to build the image from the Dockerfile:

```bash
docker build -t firefox-container .
```

This command creates an image named `firefox-container`, now with the required `libEGL` and `libpci` libraries included.

### 3. **Run the Container**

Now, run the Firefox container with X11 forwarding:

```bash
docker run -it \
    --rm \
    --name firefox-instance \
    -e DISPLAY=$DISPLAY \
    -v /tmp/.X11-unix:/tmp/.X11-unix \
    firefox-container
```

### 4. **Allow X11 Connections**

Before running the container, allow X11 connections to your display on the host machine by running:

```bash
xhost +
```

### 5. **Clean Up (Optional)**

If you want to remove the previous images and containers to free up space, follow these steps:

- **List and remove containers:**

  ```bash
  docker ps -a
  docker rm <container_id>
  ```

- **List and remove images:**

  ```bash
  docker images
  docker rmi <image_id>
  ```

- **Clean up all unused resources:**

  ```bash
  docker system prune -a
  ```

---

This updated Dockerfile and setup should resolve both the `libpci` and `libEGL` missing errors. Let me know if it works or if you encounter any further issues!
