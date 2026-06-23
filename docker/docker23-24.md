# Docker 23.0 and 24.0 NEW Features

Compared with Docker 20.10, this period made BuildKit and plugin-based tooling the normal backend workflow.

## BuildKit as the Normal Builder

```bash
docker build -t my-api .
```

Backend builds now rely more on BuildKit behavior: cache, secrets, multi-platform support, and build output.

## Build Secrets

Do not copy private tokens or package-manager credentials into images.

```bash
docker build \
  --secret id=maven_settings,src=$HOME/.m2/settings.xml \
  -t my-api .
```

```dockerfile
RUN --mount=type=secret,id=maven_settings,target=/root/.m2/settings.xml \
    ./mvnw -DskipTests package
```

The secret exists during the build step but is not stored as an image layer.

## Buildx and Compose Plugins

```bash
docker buildx version
docker compose version
```

If an upgrade breaks builds or local environments, check Engine, CLI, Buildx, and Compose versions together.

## What should I check after upgrading?

- Install Docker Engine, CLI, Buildx, and Compose together.
- Move build credentials to BuildKit secrets.
- Prefer `docker compose` over old `docker-compose`.
- Retest CI cache behavior.

## References

- Docker Engine 23.0 release notes: https://docs.docker.com/engine/release-notes/23.0/
- Docker Engine 24.0 release notes: https://docs.docker.com/engine/release-notes/24.0/
- Docker Build secrets: https://docs.docker.com/build/building/secrets/
