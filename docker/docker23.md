# Docker 23.0 NEW Features

Compared with Docker 20.10, Docker 23.0 is a big jump. It changed versioning and made modern build tooling more central.

## Versioning Changed

Docker moved away from calendar-style versions like `20.10` and started using SemVer-style versions like `23.0`.

For backend teams, this makes upgrades feel more like other runtime upgrades: read the major version notes before moving CI or shared dev machines.

## Buildx Is a Separate Plugin Package

Buildx is distributed as a separate package.

```bash
sudo apt-get install docker-ce docker-ce-cli containerd.io docker-buildx-plugin docker-compose-plugin
```

If `docker buildx` disappears after an upgrade, the Engine may be installed but the plugin package may be missing.

## BuildKit Becomes the Normal Build Path

Docker 23.0 made BuildKit the default builder for common `docker build` usage.

```bash
docker build -t my-api .
```

That means backend teams should understand BuildKit behavior, especially cache and secrets.

```bash
docker build \
  --secret id=maven_settings,src=$HOME/.m2/settings.xml \
  -t my-api .
```

```dockerfile
RUN --mount=type=secret,id=maven_settings,target=/root/.m2/settings.xml \
    ./mvnw -DskipTests package
```

## Compose Plugin Matters More

The modern command is:

```bash
docker compose up --build
```

The old standalone `docker-compose` binary may still exist in some projects, but newer Docker installs expect the Compose plugin.

## What should I check after upgrading?

- Install Engine, CLI, Buildx plugin, and Compose plugin together.
- Test CI builds after the BuildKit default change.
- Move build credentials to BuildKit secrets.
- Prefer `docker compose` over old `docker-compose`.

## References

- Docker Engine 23.0 release notes: https://docs.docker.com/engine/release-notes/23.0/
- Docker Build secrets: https://docs.docker.com/build/building/secrets/
