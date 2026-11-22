# 🐳 Docker Zero to Hero — System That Ships

Learn Docker from the ground up through practical, hands-on examples.

Welcome to the **Docker Zero to Hero** series by **System That Ships**! This repository contains the source code, Dockerfiles, scripts, and practical exercises demonstrated throughout the YouTube series.

The goal is simple: understand Docker concepts and learn how to use them by building and running real containers.

---

## 📚 Episode Roadmap

| Episode | Topic | What You'll Learn |
|---|---|---|
| 01 | Docker Introduction | Understand Docker, containers, and why containerization matters |
| 02 | Docker Architecture & Installation | Explore Docker architecture, install Docker, and run your first container |
| 03 | Dockerfile & Custom Images | Create Dockerfiles, build custom images, run containers, and push images to Docker Hub |

More episodes and practical labs will be added as the series progresses.

---

## 📁 Repository Structure

```text
episodes/
│
├── 01-docker-introduction/
│
├── 02-docker-architecture-and-installation/
│   ├── 01-install-docker/
│   ├── 02-first-container/
│   ├── 03-container-shell/
│   └── 04-docker-desktop/
│
└── 03-dockerfile-custom-images/
    ├── 01-Create-Index-html/
    │   └── index.html
    │
    ├── 02-First-Dockerfile/
    │   ├── Dockerfile
    │   └── index.html
    │
    ├── 03-My-First-Image-build/
    │   ├── Dockerfile
    │   └── index.html
    │
    ├── 04-Run-My-First-Custom-Container/
    │
    ├── 05-My-First-Image-v2/
    │   ├── Dockerfile
    │   └── index.html
    │
    └── 06-Docker-Hub-Image-Push/
```

---

# 🚀 Getting Started

## Prerequisites

Before starting the hands-on labs, make sure you have:

- Docker Engine or Docker Desktop installed
- Git installed
- A terminal (Linux, macOS, Windows Terminal, or PowerShell)
- A Docker Hub account for image-publishing exercises

Verify your Docker installation:

```bash
docker --version
docker info
```

Clone this repository:

```bash
git clone https://github.com/systemsthatship/docker-zero-to-hero.git
```

Navigate into the repository:

```bash
cd docker-zero-to-hero
```

---

# 📦 Episode 01 — Docker Introduction

**Folder:** `01-docker-introduction/`

Get familiar with Docker and containerization concepts.

Topics include:

- What is Docker?
- What is containerization?
- Containers vs. Virtual Machines
- Why do we need Docker?
- Real-world use cases of Docker

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

---

# 🏗️ Episode 03 — Dockerfile & Building Custom Images

**Folder:** `03-dockerfile-custom-images/`

Learn how to create your own Docker images instead of relying only on prebuilt images.

**Episode goal:** Create. Build. Run. Share.

### Hands-on lab sequence

| Lab | Folder | What You'll Do |
|---|---|---|
| 01 | `01-Create-Index-html/` | Create a simple HTML application |
| 02 | `02-First-Dockerfile/` | Write your first Dockerfile |
| 03 | `03-My-First-Image-build/` | Build your first custom Docker image |
| 04 | `04-Run-My-First-Custom-Container/` | Run a container using your custom image |
| 05 | `05-My-First-Image-v2/` | Update the application and build version 2 |
| 06 | `06-Docker-Hub-Image-Push/` | Tag and push your image to Docker Hub |

## Step 1 — Create the application

Create an `index.html` file containing your application content.

## Step 2 — Create your first Dockerfile

Example Dockerfile:

```dockerfile
FROM nginx:alpine

COPY index.html /usr/share/nginx/html/index.html

EXPOSE 80
```

### Understanding the instructions

| Instruction | Purpose |
|---|---|
| `FROM` | Specifies the base image |
| `COPY` | Copies application files into the image |
| `EXPOSE` | Documents the port used by the application |

## Step 3 — Build your custom image

Navigate to the build lab:

```bash
cd episodes/03-dockerfile-custom-images/03-My-First-Image-build
```

Build the image:

```bash
docker build -t my-first-app:v1 .
```

Verify the image:

```bash
docker images
```

## Step 4 — Run your custom container

```bash
docker run -d \
  --name my-web-app \
  -p 8080:80 \
  my-first-app:v1
```

Open your browser:

```text
http://localhost:8080
```

Verify the running container:

```bash
docker ps
```

View container logs:

```bash
docker logs my-web-app
```

## Step 5 — Build version 2

Modify your `index.html` file and build a new image:

```bash
docker build -t my-first-app:v2 .
```

Remove the previous container:

```bash
docker rm -f my-web-app
```

Run version 2:

```bash
docker run -d \
  --name my-web-app-v2 \
  -p 8080:80 \
  my-first-app:v2
```

You have now created and run two versions of your custom Docker image.

## Step 6 — Push your image to Docker Hub

Log in:

```bash
docker login
```

Tag your image:

```bash
docker tag my-first-app:v2 YOUR_DOCKERHUB_USERNAME/my-first-app:v2
```

Push it:

```bash
docker push YOUR_DOCKERHUB_USERNAME/my-first-app:v2
```

Pull it back:

```bash
docker pull YOUR_DOCKERHUB_USERNAME/my-first-app:v2
```

Replace `YOUR_DOCKERHUB_USERNAME` with your actual Docker Hub username.

---

# 🧠 What You'll Learn

By completing these episodes, you'll gain practical experience with:

- Docker fundamentals and architecture
- Installing and configuring Docker
- Running and managing containers
- Accessing container shells
- Writing Dockerfiles
- Building custom Docker images
- Managing image versions and tags
- Running containerized applications
- Publishing images to Docker Hub

---

# 🎯 Who Is This Repository For?

This repository is designed for:

- Beginners learning Docker
- Developers exploring containerization
- DevOps and Cloud Engineers
- System Administrators
- Students preparing for DevOps interviews
- Engineers building practical containerization skills

No advanced Docker experience is required to get started.

---

# ▶️ Follow the YouTube Series

Subscribe to **System That Ships** for practical tutorials on:

- Docker & Kubernetes
- DevOps & Cloud Infrastructure
- AI Infrastructure & Platform Engineering
- Automation and Modern Engineering Practices

Every episode focuses on practical learning, real commands, and hands-on implementation.

---

# ⭐ Support This Project

If you find this repository useful:

- ⭐ Star this repository
- 🍴 Fork it and experiment with the examples
- 🐛 Open an issue if you encounter a problem
- 📢 Share it with other developers learning Docker
- 📺 Subscribe to System That Ships

Let's learn, build, and ship together!

---

**Built with ❤️ by System That Ships**

*Understand the technology. Build the solution. Ship it with confidence.*
