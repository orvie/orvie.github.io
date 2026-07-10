---
layout: page
title: Dockerfile Best Practices
---

# Dockerfile Best Practices

## Use Multi-Stage Builds

Keep the final image small by separating build and runtime stages.

```dockerfile
# Build stage
FROM node:20 AS build
WORKDIR /app
COPY package*.json ./
RUN npm ci
COPY . .
RUN npm run build

# Runtime stage
FROM node:20-slim
WORKDIR /app
COPY --from=build /app/dist ./dist
COPY --from=build /app/package*.json ./
RUN npm ci --omit=dev
CMD ["node", "dist/index.js"]
```

## Order Layers for Cache Efficiency

Put things that change least often first, so Docker can reuse cached layers.

```dockerfile
COPY package*.json ./
RUN npm ci
COPY . .
```

Copying `package*.json` and installing dependencies before copying the rest of the source means dependency installs are cached until the manifest actually changes.

## Use a `.dockerignore`

```
node_modules
.git
.env
dist
*.log
```

Prevents unnecessary files from busting the cache or bloating the build context.

## Run as a Non-Root User

```dockerfile
RUN addgroup --system app && adduser --system --ingroup app app
USER app
```

## Pin Base Image Versions

Use specific tags (`node:20-slim`) instead of `latest` so builds are reproducible.

## Keep Images Small

- Prefer `-slim` or `-alpine` base images where compatible
- Combine `RUN` commands to reduce layers: `RUN apt-get update && apt-get install -y curl && rm -rf /var/lib/apt/lists/*`
- Remove build-only dependencies in the final stage

## Troubleshooting

- **Cache never hits**: Check that `COPY` steps aren't invalidated by unrelated file changes earlier in the Dockerfile
- **Image too large**: Use `docker history <image>` to see which layer added the most size
- **Permission denied at runtime**: Ensure files copied `--from=build` are readable by the non-root `USER`
