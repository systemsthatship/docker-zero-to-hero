---

# ⚙️ Episode 02 — Docker Architecture & Installation

**Folder:** `02-docker-architecture-and-installation/`

Explore Docker's internal architecture and get your environment ready for hands-on development.

### Hands-on labs

| Lab | Folder | Description |
|---|---|---|
| 01 | `01-install-docker/` | Install Docker |
| 02 | `02-first-container/` | Run your first Docker container |
| 03 | `03-container-shell/` | Access the shell inside a running container |
| 04 | `04-docker-desktop/` | Work with Docker Desktop on Windows |

### Installation script

The episode also includes:

```text
docker-install.sh
```

On a compatible Linux distribution, make the script executable and run it:

```bash
chmod +x docker-install.sh
./docker-install.sh
```

Review the script before executing it and verify that your Linux distribution is supported.

### Useful Docker commands

```bash
# Check Docker version
docker --version

# Display Docker system information
docker info

# Download an image
docker pull nginx

# Run a container
docker run -d --name my-nginx -p 8080:80 nginx

# List running containers
docker ps

# List all containers
docker ps -a

# Access a running container
docker exec -it my-nginx sh

# Stop a container
docker stop my-nginx

# Remove a container
docker rm my-nginx
```
