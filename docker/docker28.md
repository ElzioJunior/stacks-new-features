# Docker 28.x NEW Features

Compared with Docker 27.x, Docker 28.x was mostly about security updates, runtime updates, rootless improvements, and continued build/runtime cleanup.

## Newer Runtime Stack

Docker 28.x updated pieces that backend developers rarely call directly but rely on every day:

- BuildKit
- Buildx
- `containerd`
- `runc`
- Go runtime

When something changes around filesystem permissions, process behavior, or image build cache, these components are often involved.

## Security and Networking Fixes

Docker 28.x included security and networking fixes.

For backend services, retest:

- Published ports.
- Service-to-service calls in Compose.
- Healthchecks.
- Containers using custom networks.
- Containers running as non-root users.

## Better Rootless Path

Rootless Docker continued to improve.

If your organization wants less privileged developer machines or CI workers, this line is a better place to test than older releases.

## What should I check after upgrading?

- Run Compose integration tests after upgrading.
- Test published ports and internal service names.
- Verify non-root containers still read/write expected paths.
- Record Docker component versions in CI logs.

## References

- Docker Engine 28 release notes: https://docs.docker.com/engine/release-notes/28/
