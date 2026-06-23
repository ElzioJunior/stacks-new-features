# Docker 19.03 NEW Features

Compared with Docker 18.09, Docker 19.03 made Docker more useful as a daily backend development tool.

## Docker Contexts

Docker contexts let the CLI remember different Docker endpoints.

```bash
docker context ls
docker context use local
docker ps
```

For backend engineers, this avoids manually switching `DOCKER_HOST` when moving between local Docker, a remote test host, and CI-like environments.

## BuildKit and Buildx Become More Visible

BuildKit became easier to adopt, and Buildx started becoming the normal way to do advanced builds.

```bash
docker buildx create --name my-builder --use
docker buildx build -t my-api .
```

This matters for backend services because it leads directly to multi-platform images, better cache control, and CI build improvements in later releases.

## Rootless Docker Work

Rootless Docker work became more visible around this line.

The backend view:

- Safer local development on shared machines.
- Useful for CI runners where full root Docker is not acceptable.
- Not always a drop-in replacement, especially for networking and filesystem edge cases.

## GPU Flag

Docker added a simpler `--gpus` flag.

```bash
docker run --gpus all nvidia/cuda:12.4.1-base-ubuntu22.04 nvidia-smi
```

Most backend APIs do not need this, but it matters for services that run ML inference, video processing, or CUDA workloads.

## What should I check after upgrading?

- Use contexts instead of manually exporting `DOCKER_HOST`.
- Start testing Buildx if CI needs multi-platform images.
- Consider rootless Docker for safer developer or CI machines.
- Use `--gpus` only for specialized backend workloads.

## References

- Docker Engine 19.03 release notes: https://docs.docker.com/engine/release-notes/19.03/
