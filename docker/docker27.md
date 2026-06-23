# Docker 27.x NEW Features

Compared with Docker 26.x, Docker 27.x continued polishing BuildKit, rootless Docker, and the containerd image-store path.

## Better Build Reliability

Docker 27.x included BuildKit and builder garbage collection fixes.

For backend teams, this affects shared CI machines:

```bash
docker builder prune
docker system df
docker system prune
```

The goal is fewer surprises when CI runners clean cache or run out of disk.

## Rootless Docker Improvements

Rootless Docker continued to improve.

Backend use cases:

- Safer local development on shared machines.
- Less privileged CI runners.
- Better alignment with locked-down environments.

Still test networking, bind mounts, and file ownership carefully before switching a whole team.

## containerd Image Store Maturity

The containerd image store continued to mature.

For backend developers, the main thing is compatibility with normal workflows:

```bash
docker pull postgres:16
docker run --rm postgres:16 postgres --version
docker build -t my-api:test .
```

## What should I check after upgrading?

- Watch CI disk usage and builder cache behavior.
- Test rootless Docker before making it the default.
- Verify bind-mounted source code permissions.
- Test local Compose environments after the upgrade.

## References

- Docker Engine 27 release notes: https://docs.docker.com/engine/release-notes/27/
