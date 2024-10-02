Setting up Bitwarden in Docker on Kali Linux involves several steps. Here's a detailed guide to help you through the process:

### Step 1: Update and Install Prerequisites

Ensure your system is updated and that Docker and Docker Compose are installed.

```bash
sudo apt update && sudo apt upgrade -y
sudo apt install docker.io docker-compose -y
```

### Step 2: Create a Directory for Bitwarden

Create a directory where you will store the Bitwarden files.

```bash
mkdir -p ~/bitwarden
cd ~/bitwarden
```

### Step 3: Create a `docker-compose.yml` File

Create a `docker-compose.yml` file inside the `bitwarden` directory with the following content:

```yaml
version: '3'

services:
  bitwarden:
    image: bitwardenrs/server:latest
    container_name: bitwarden
    restart: unless-stopped
    volumes:
      - ./bw-data:/data
    ports:
      - 80:80
      - 443:443
    environment:
      WEBSOCKET_ENABLED: "true" # Enable WebSocket notifications
      SIGNUPS_ALLOWED: "false"  # Disable self-signups
```

### Step 4: Create Volumes and Directories

Create necessary directories and set permissions:

```bash
mkdir -p ~/bitwarden/bw-data
sudo chown -R 1000:1000 ~/bitwarden/bw-data
```

### Step 5: Configure HTTPS (Optional)

If you want to use HTTPS, you will need to configure SSL certificates. You can use Let's Encrypt to obtain free SSL certificates. For simplicity, let's assume you have your SSL certificates ready. 

Modify the `docker-compose.yml` file to map the SSL certificates:

```yaml
version: '3'

services:
  bitwarden:
    image: bitwardenrs/server:latest
    container_name: bitwarden
    restart: unless-stopped
    volumes:
      - ./bw-data:/data
      - /path/to/your/ssl/cert.pem:/ssl/cert.pem
      - /path/to/your/ssl/key.pem:/ssl/key.pem
    ports:
      - 80:80
      - 443:443
    environment:
      WEBSOCKET_ENABLED: "true"
      SIGNUPS_ALLOWED: "false"
      SSL_CERT: "/ssl/cert.pem"
      SSL_KEY: "/ssl/key.pem"
```

Replace `/path/to/your/ssl/cert.pem` and `/path/to/your/ssl/key.pem` with the actual paths to your SSL certificate and key files.

### Step 6: Start Bitwarden

Navigate to your Bitwarden directory and start the container using Docker Compose:

```bash
cd ~/bitwarden
sudo docker-compose up -d
```

### Step 7: Access Bitwarden

Open your web browser and navigate to `http://<your-kali-linux-ip>` or `https://<your-kali-linux-ip>` if you configured SSL. You should see the Bitwarden login page.

### Step 8: Secure Your Installation

1. **Firewall Configuration**: Ensure your firewall settings allow traffic on the ports you're using for Bitwarden (80 and 443).

2. **Admin Panel**: Bitwarden has an admin panel that can be enabled through environment variables. You might want to restrict access to this.

Here's how to enable and access the admin panel:

Add the following environment variable to your `docker-compose.yml` file:

```yaml
    environment:
      ...
      ADMIN_TOKEN: <your_admin_token>
```

Replace `<your_admin_token>` with a secure token. Access the admin panel at `https://<your-kali-linux-ip>/admin` and use the token to log in.

### Additional Notes

- **Backups**: Regularly backup your `bw-data` directory to prevent data loss.
- **Updates**: Keep your Bitwarden image up-to-date by periodically pulling the latest version and restarting the container.

This setup should get you running Bitwarden in Docker on Kali Linux. Let me know if you need further assistance!
