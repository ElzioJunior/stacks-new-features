# Docker 26.x NEW Features

Compared with Docker 25.0, Docker 26.x continued the image-store, OCI, runtime, and networking cleanup work.

## More containerd Image Store Work

Docker kept improving the containerd image-store path.

The backend impact is mostly in CI and tooling:

- Image build output.
- Image save/load behavior.
- Image scanners.
- Registry push/pull behavior.

If your pipeline uses Docker images as artifacts, test the whole image path after upgrading.

```bash
docker build -t my-api:test .
docker image save my-api:test -o my-api.tar
docker image load -i my-api.tar
```

## Build and Runtime Component Updates

Docker 26.x carried newer BuildKit, Buildx, `containerd`, and `runc` versions.

Backend teams should treat this like a runtime upgrade:

```bash
docker version
docker buildx version
docker compose version
```

## OCI Archive Compatibility

OCI archive fixes matter when images are passed between Docker and other tools.

Examples:

- Vulnerability scanners.
- CI artifact storage.
- Promotion pipelines.
- Kubernetes deployment tooling.

## What should I check after upgrading?

- Test image artifact flows: build, save, load, scan, push, pull.
- Compare CI build cache behavior before and after the upgrade.
- Capture Docker, Buildx, and Compose versions in pipeline logs.
- Re-run integration tests that depend on local database/cache containers.

## References

- Docker Engine 26.0 release notes: https://docs.docker.com/engine/release-notes/26.0/
- Docker Engine 26.1 release notes: https://docs.docker.com/engine/release-notes/26.1/
