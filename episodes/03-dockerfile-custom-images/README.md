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

