# Docker 26.x to 28.x NEW Features

Compared with Docker 25.0, these releases are mostly runtime hardening: fewer new commands, more stability in builds, rootless Docker, networking, and image-store behavior.

## Runtime Chain

Docker upgrades include several pieces:

- Docker Engine
- Docker CLI
- BuildKit
- Buildx
- Compose plugin
- `containerd`
- `runc`

```bash
docker version
docker buildx version
docker compose version
```

When a backend build or container behaves differently after an upgrade, check these versions together.

## Rootless Docker

Rootless Docker became more practical.

Backend use cases:

- safer shared developer machines
- less privileged CI runners
- locked-down internal environments

Still test networking, bind mounts, and file ownership before making it the team default.

## Image Store and OCI Compatibility

```bash
docker build -t my-api:test .
docker image save my-api:test -o my-api.tar
docker image load -i my-api.tar
```

This matters for CI pipelines that scan, store, or promote image artifacts.

## What should I check after upgrading?

- Capture Docker, Buildx, and Compose versions in CI logs.
- Test Compose integration environments.
- Test rootless Docker before enforcing it.
- Test image artifact flows: build, save, load, scan, push, pull.

## References

- Docker Engine 26.0 release notes: https://docs.docker.com/engine/release-notes/26.0/
- Docker Engine 27 release notes: https://docs.docker.com/engine/release-notes/27/
- Docker Engine 28 release notes: https://docs.docker.com/engine/release-notes/28/
