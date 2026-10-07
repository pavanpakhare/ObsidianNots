# Docker

Since you're learning **Java/Spring Boot + databases + Redis/RabbitMQ**, I'll focus on Docker in a way that directly applies to backend development.

## 1. What is Docker?

Docker packages an application and everything it needs into a **container**.

Without Docker:

```text
Your machine
 ├── Java 21
 ├── PostgreSQL
 ├── Redis
 ├── RabbitMQ
 └── Your Spring Boot app
```

With Docker:

```text
Docker
 ├── Spring Boot container
 ├── PostgreSQL container
 ├── Redis container
 └── RabbitMQ container
```

A container is isolated from the host and other containers, but it shares the host's Linux kernel.

---

# 2. Docker Architecture

The important concepts are:

```text
Docker CLI
    │
    ▼
Docker Engine
    │
    ├── Images
    │
    ├── Containers
    │
    ├── Networks
    │
    └── Volumes
```

### Image

A **read-only template** used to create containers.

Examples:

```text
postgres:17
redis:8
rabbitmq:4
nginx:latest
```

### Container

A running instance of an image.

```bash
docker run redis
```

creates a Redis container from the Redis image.

---

# 3. Check Docker

On Fedora:

```bash
docker --version
```

Check the daemon:

```bash
sudo systemctl status docker
```

Start it:

```bash
sudo systemctl start docker
```

Enable at boot:

```bash
sudo systemctl enable docker
```

Test:

```bash
docker run hello-world
```

---

# 4. Docker Images

Search images:

```bash
docker search nginx
```

Download an image:

```bash
docker pull nginx
```

List images:

```bash
docker images
```

or:

```bash
docker image ls
```

Remove an image:

```bash
docker rmi nginx
```

---

# 5. Run Your First Container

```bash
docker run nginx
```

The terminal may appear to hang.

That's because the container is running in the foreground.

Use:

```bash
Ctrl+C
```

to stop it.

Run in background:

```bash
docker run -d nginx
```

`-d` means **detached mode**.

Check containers:

```bash
docker ps
```

Show stopped containers too:

```bash
docker ps -a
```

---

# 6. Container Names

Docker automatically generates names.

Instead:

```bash
docker run -d --name my-nginx nginx
```

Now:

```bash
docker ps
```

will show:

```text
my-nginx
```

Stop it:

```bash
docker stop my-nginx
```

Start it again:

```bash
docker start my-nginx
```

Remove it:

```bash
docker rm my-nginx
```

---

# 7. Port Mapping

This is extremely important.

Suppose Nginx inside the container listens on:

```text
80
```

Run:

```bash
docker run -d -p 8080:80 nginx
```

Meaning:

```text
Host              Container

localhost:8080 ─────► :80
```

Open:

```text
http://localhost:8080
```

General syntax:

```bash
-p HOST_PORT:CONTAINER_PORT
```

For Spring Boot:

```bash
docker run -p 8080:8080 my-spring-app
```

---

# 8. Container Logs

```bash
docker logs my-nginx
```

Follow logs:

```bash
docker logs -f my-nginx
```

This is particularly useful for Spring Boot:

```bash
docker logs -f spring-app
```

---

# 9. Execute Commands Inside Containers

```bash
docker exec -it my-nginx bash
```

If the image doesn't contain bash:

```bash
docker exec -it my-nginx sh
```

Now you're inside the container.

For example:

```bash
ls
```

Exit:

```bash
exit
```

---

# 10. Environment Variables

You can pass configuration into a container.

```bash
docker run \
  -e POSTGRES_USER=admin \
  -e POSTGRES_PASSWORD=secret \
  -e POSTGRES_DB=mydb \
  postgres
```

Inside the container:

```bash
echo $POSTGRES_USER
```

This is very common for databases and applications.

For Spring Boot:

```bash
docker run \
  -e SPRING_DATASOURCE_URL=jdbc:postgresql://postgres:5432/mydb \
  -e SPRING_DATASOURCE_USERNAME=admin \
  -e SPRING_DATASOURCE_PASSWORD=secret \
  my-spring-app
```

---

# 11. Volumes

Containers are generally **ephemeral**.

If you delete a PostgreSQL container, you don't want your database disappearing with it.

Use a volume:

```bash
docker volume create postgres-data
```

Then:

```bash
docker run \
  --name postgres \
  -e POSTGRES_PASSWORD=secret \
  -v postgres-data:/var/lib/postgresql/data \
  postgres
```

Architecture:

```text
PostgreSQL container
       │
       ▼
/var/lib/postgresql/data
       │
       ▼
Docker volume
       │
       ▼
Persistent data
```

List volumes:

```bash
docker volume ls
```

Inspect:

```bash
docker volume inspect postgres-data
```

---

# 12. Bind Mounts

Instead of a Docker-managed volume, you can mount a directory from your computer.

```bash
docker run \
  -v ~/postgres-data:/var/lib/postgresql/data \
  postgres
```

Difference:

```text
Volume:

Docker manages storage
postgres-data
      │
      ▼
container
```

Bind mount:

```text
Your directory
~/postgres-data
      │
      ▼
container
```

Use **volumes** for most database persistence.

Use **bind mounts** when you specifically want the container to access files from your host.

---

# 13. Dockerfile

A Dockerfile describes how to build your own image.

Example:

```dockerfile
FROM eclipse-temurin:21-jdk

WORKDIR /app

COPY app.jar app.jar

EXPOSE 8080

CMD ["java", "-jar", "app.jar"]
```

Build:

```bash
docker build -t my-spring-app .
```

Check:

```bash
docker images
```

Run:

```bash
docker run -p 8080:8080 my-spring-app
```

---

# 14. Dockerfile Instructions

Important instructions:

|Instruction|Purpose|
|---|---|
|`FROM`|Base image|
|`WORKDIR`|Working directory|
|`COPY`|Copy files|
|`ADD`|Copy/add files|
|`RUN`|Execute build command|
|`ENV`|Environment variable|
|`EXPOSE`|Document container port|
|`CMD`|Default command|
|`ENTRYPOINT`|Main executable|
|`ARG`|Build-time variable|

Example:

```dockerfile
FROM eclipse-temurin:21-jdk

WORKDIR /app

COPY target/app.jar app.jar

EXPOSE 8080

ENTRYPOINT ["java", "-jar", "app.jar"]
```

---

# 15. Docker Image Layers

Dockerfiles create layers.

```dockerfile
FROM ubuntu
RUN apt update
RUN apt install -y curl
COPY app /app
```

Conceptually:

```text
Layer 4 → application
Layer 3 → curl
Layer 2 → apt update
Layer 1 → ubuntu
```

Docker can reuse unchanged layers, making builds faster.

This is why Dockerfile ordering matters.

---

# 16. Docker Network

Suppose you have:

```text
Spring Boot
     │
     ▼
PostgreSQL
```

Create a network:

```bash
docker network create backend
```

Run PostgreSQL:

```bash
docker run -d \
  --name postgres \
  --network backend \
  -e POSTGRES_PASSWORD=secret \
  postgres
```

Run Spring Boot:

```bash
docker run -d \
  --name spring \
  --network backend \
  -p 8080:8080 \
  my-spring-app
```

Now Spring Boot can connect to:

```text
postgres:5432
```

**not:**

```text
localhost:5432
```

This is a very important Docker concept.

Inside a container:

```text
localhost = that same container
```

---

# 17. Docker Compose

When you have multiple containers, manually running them becomes annoying.

For example:

```text
Spring Boot
     │
     ├── PostgreSQL
     ├── Redis
     └── RabbitMQ
```

Docker Compose lets you define everything in one YAML file.

`compose.yaml`:

```yaml
services:

  postgres:
    image: postgres:17
    environment:
      POSTGRES_DB: shop
      POSTGRES_USER: admin
      POSTGRES_PASSWORD: secret
    volumes:
      - postgres-data:/var/lib/postgresql/data

  redis:
    image: redis:8

  rabbitmq:
    image: rabbitmq:4-management

  app:
    build: .
    ports:
      - "8080:8080"
    depends_on:
      - postgres
      - redis
      - rabbitmq

volumes:
  postgres-data:
```

Start:

```bash
docker compose up
```

Background:

```bash
docker compose up -d
```

Stop:

```bash
docker compose down
```

View containers:

```bash
docker compose ps
```

Logs:

```bash
docker compose logs
```

Specific service:

```bash
docker compose logs app
```

Rebuild:

```bash
docker compose up --build
```

---

# 18. Compose Networking

Compose automatically creates a network.

Therefore:

```text
app
 │
 ├── postgres:5432
 ├── redis:6379
 └── rabbitmq:5672
```

Your Spring configuration can use:

```properties
spring.datasource.url=jdbc:postgresql://postgres:5432/shop

spring.data.redis.host=redis

spring.rabbitmq.host=rabbitmq
```

Notice:

```text
postgres
redis
rabbitmq
```

are the **service names**.

---

# 19. Docker Architecture for Your Spring Boot Projects

A typical project could look like:

```text
                    Internet
                       │
                       ▼
                    Nginx
                       │
                       ▼
                 Spring Boot
                  /    |    \
                 /     |     \
                ▼      ▼      ▼
          PostgreSQL Redis RabbitMQ
```

Compose:

```yaml
services:

  app:
    build: .
    ports:
      - "8080:8080"
    depends_on:
      - postgres
      - redis
      - rabbitmq

  postgres:
    image: postgres:17
    environment:
      POSTGRES_DB: ecommerce
      POSTGRES_USER: admin
      POSTGRES_PASSWORD: secret
    volumes:
      - postgres-data:/var/lib/postgresql/data

  redis:
    image: redis:8

  rabbitmq:
    image: rabbitmq:4-management
    ports:
      - "15672:15672"

volumes:
  postgres-data:
```

Then:

```bash
docker compose up -d --build
```

You have your entire backend environment running.

---

# 20. Essential Docker Commands

### Images

```bash
docker images
docker pull IMAGE
docker build -t NAME .
docker rmi IMAGE
```

### Containers

```bash
docker ps
docker ps -a

docker run IMAGE
docker start CONTAINER
docker stop CONTAINER
docker restart CONTAINER
docker rm CONTAINER
```

### Debugging

```bash
docker logs CONTAINER
docker exec -it CONTAINER sh
docker inspect CONTAINER
```

### Networks

```bash
docker network ls
docker network create NAME
docker network inspect NAME
```

### Volumes

```bash
docker volume ls
docker volume create NAME
docker volume inspect NAME
docker volume rm NAME
```

### Cleanup

```bash
docker container prune
docker image prune
docker volume prune
docker network prune
```

Be careful with:

```bash
docker system prune
```

It can remove unused Docker resources.

---

# 21. Most Important Concepts to Learn

For backend development, learn these in this order:

```text
1. Image
     ↓
2. Container
     ↓
3. Dockerfile
     ↓
4. Port mapping
     ↓
5. Environment variables
     ↓
6. Volumes
     ↓
7. Networks
     ↓
8. Docker Compose
     ↓
9. Multi-container applications
     ↓
10. Docker optimization
     ↓
11. Docker security
     ↓
12. CI/CD + Docker
```

After that:

```text
Docker
  ↓
Docker Compose
  ↓
GitHub Actions
  ↓
Docker Registry
  ↓
VPS
  ↓
Nginx
  ↓
Kubernetes
```

