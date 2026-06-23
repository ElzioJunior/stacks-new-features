# Docker 24.0 NEW Features

Compared with Docker 23.0, Docker 24.0 was less about new backend commands and more about keeping the runtime chain current.

## Runtime Chain Updates

When you upgrade Docker, you usually upgrade more than `dockerd`.

Important moving parts:

- Docker Engine
- Docker CLI
- `containerd`
- `runc`
- BuildKit
- Buildx
- Compose plugin
- Go runtime

For backend teams, this matters because a build failure might come from Buildx or BuildKit, while a runtime failure might come from `containerd` or `runc`.

## Compose and Buildx Version Awareness

Check versions together:

```bash
docker version
docker buildx version
docker compose version
```

This is especially useful when a developer machine works but CI does not.

## Safer Upgrade Habit

Docker 24.0 is a good point to adopt an upgrade checklist for backend services.

```bash
docker compose build
docker compose up -d
docker compose logs -f api
docker buildx build -t my-api:test .
```

Run the same checks in local development and CI before moving production build agents.

## What should I check after upgrading?

- Track Docker, Buildx, and Compose plugin versions in bug reports.
- Rebuild representative backend images after the upgrade.
- Run integration dependencies with Compose after the upgrade.
- Verify CI cache behavior, especially if builds became slower.

## References

- Docker Engine 24.0 release notes: https://docs.docker.com/engine/release-notes/24.0/
