---
layout: page
title: Docker Basics
---

# Docker Basics

## Key Concepts

- **Image**: Read-only template used to create containers
- **Container**: A running (or stopped) instance of an image
- **Dockerfile**: Instructions to build an image
- **Volume**: Persistent storage that survives container restarts

## Common Commands

```bash
# Build an image from a Dockerfile
docker build -t my-app .

# Run a container
docker run -p 3000:3000 my-app

# List running containers
docker ps

# Stop a container
docker stop <container-id>

# View logs
docker logs -f <container-id>
```

## docker-compose

```yaml
version: "3.8"
services:
  app:
    build: .
    ports:
      - "3000:3000"
    environment:
      - NODE_ENV=production
```

```bash
docker-compose up -d
docker-compose down
```

## Troubleshooting

- **Port already in use**: Check for another process with `docker ps` or `lsof -i :3000`
- **Image not updating**: Rebuild with `docker build --no-cache`
- **Container exits immediately**: Check logs with `docker logs <container-id>`
