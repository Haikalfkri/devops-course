# DevOps Course

## Docker Commands

A collection of essential Docker commands for managing containers, images, and Docker Compose.

## 1. Docker Container Commands

### List Containers

```bash
# List all running containers
docker ps

# List all containers, including stopped containers
docker ps -a
```

### Stop Containers

```bash
# Stop a single container
docker stop container_id

# Stop multiple containers
docker stop container1 container2 container3
```

### Remove Containers

```bash
# Remove a container
docker rm container_id

# Remove all stopped containers
docker container prune
```

> **Note:** `docker container prune` removes all stopped containers, not running containers.

## 2. Docker Image Commands

### Remove Images

```bash
# Remove a single image
docker rmi nginx

# Remove multiple images
docker rmi nginx hello-world image3 image4
```

> **Note:** An image may not be removable if it is being used by an existing container.

## 3. Docker Build & Run Commands

### Build a Docker Image

```bash
docker build -t mern-backend .
```

- `-t mern-backend`: Assigns a name to the image.
- `.`: Uses the current directory as the build context.

### Run a Container

```bash
docker run -p 5000:5000 --name backend mern-backend
```

- `-p 5000:5000`: Maps host port `5000` to container port `5000`.
- `--name backend`: Assigns the container name `backend`.
- `mern-backend`: Specifies the Docker image to run.

### Run a Container with Environment Variables

```bash
docker run -p 5000:5000 --name backend --env-file .env mern-backend
```

- `--env-file .env`: Loads environment variables from the `.env` file.
- Make sure the `.env` file exists in the current working directory.

> **Security:** Do not commit `.env` files containing secrets or credentials to your Git repository.

## 4. Docker Compose Commands

### Start Services

```bash
# Build images and start services
docker-compose up --build

# Build images and start services in the background
docker-compose up --build -d
```

- `up`: Creates and starts the services defined in the Compose file.
- `--build`: Builds or rebuilds images before starting services.
- `-d`: Runs services in detached mode.

### Stop Services

```bash
# Stop and remove containers and networks created by Compose
docker-compose down
```

### View Logs

```bash
# View logs from all services
docker-compose logs

# View logs from a specific service
docker-compose logs service_name
```

> **Note:** Use the service name defined in `docker-compose.yml` for the `service_name` argument.

## 5. Quick Reference

| Command | Description |
|---|---|
| `docker ps` | List running containers |
| `docker ps -a` | List all containers |
| `docker stop container_id` | Stop a container |
| `docker rm container_id` | Remove a container |
| `docker container prune` | Remove all stopped containers |
| `docker rmi image_name` | Remove an image |
| `docker build -t image_name .` | Build a Docker image |
| `docker run image_name` | Run a container |
| `docker-compose up --build` | Build and start services |
| `docker-compose up --build -d` | Build and start services in the background |
| `docker-compose down` | Stop and remove Compose resources |
| `docker-compose logs` | View service logs |

## 6. Docker Compose V2

In newer Docker installations, Docker Compose V2 uses the `docker compose` command without a hyphen.

```bash
# Build images and start services
docker compose up --build

# Build images and start services in the background
docker compose up --build -d

# Stop and remove services
docker compose down

# View logs from all services
docker compose logs

# View logs from a specific service
docker compose logs service_name
```

Both `docker-compose` and `docker compose` may be available depending on your Docker installation.

## 7. Basic Docker Workflow

A typical workflow for running a Dockerized application:

1. **Build** the Docker image.
   ```bash
   docker build -t mern-backend .
   ```
2. **Run** the container.
   ```bash
   docker run -p 5000:5000 --name backend mern-backend
   ```
3. **Check** running containers.
   ```bash
   docker ps
   ```
4. **View** container logs.
   ```bash
   docker logs backend
   ```
5. **Stop** the container.
   ```bash
   docker stop backend
   ```
6. **Remove** the container when it is no longer needed.
   ```bash
   docker rm backend
   ```