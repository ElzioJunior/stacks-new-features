# Docker 29.x NEW Features

Compared with Docker 28.x, Docker 29.x is important because it changes defaults and removes old behavior.

## containerd Image Store by Default

For fresh installs, the containerd image store became the default.

<img src="images/docker-image-store.svg" />

```text
old: docker pull -> Docker graphdriver image store
new: docker pull -> containerd image store
```

Backend impact: test CI image workflows carefully, especially image save/load, scanners, and promotion pipelines.

## Docker Content Trust Removed

Docker Content Trust was removed from the Docker CLI.

If you used this:

```bash
DOCKER_CONTENT_TRUST=1 docker pull my-company/my-api:1.0.0
```

Plan a migration to current signing and supply-chain tooling before upgrading shared environments.

## cgroup v1 Deprecated

```bash
docker info | grep -i cgroup
```

This matters for backend services with strict CPU or memory limits.

## What should I check after upgrading?

- Test image build, push, pull, save, load, and scan workflows.
- Audit any use of `DOCKER_CONTENT_TRUST`.
- Check cgroup mode on Linux hosts.
- Run load tests for services with CPU or memory limits.

## References

- Docker Engine 29 release notes: https://docs.docker.com/engine/release-notes/29/
