# Docker 20.10 NEW Features

Compared with Docker 19.03, Docker 20.10 was a long-lived migration point. Many backend teams stayed on it for a long time.

## Safer Daemon Warnings

Docker added stronger warnings around unauthenticated TCP access to the daemon.

```json
{
  "hosts": ["unix:///var/run/docker.sock"]
}
```

The backend rule is simple: anyone who controls the Docker daemon can usually control the host. Do not expose it casually from dev machines, CI workers, or internal tools.

## Better Events After Prune

Docker improved event visibility after pruning resources.

```bash
docker system prune
docker events --filter event=prune
```

This helps backend teams understand when images, containers, networks, volumes, or builder cache disappear from shared development machines or CI runners.

## API v1.41

Docker Engine API moved to v1.41.

If your backend automation talks to Docker directly, check the API version used by libraries and scripts.

```bash
docker version
```

## Legacy Cleanup

20.10 removed or deprecated older behavior:

- `aufs` storage driver was deprecated.
- Old Dockerfile `ENV name value` syntax was deprecated.
- Some old API and CLI behavior was removed.
- Pulling from registries without pull-by-digest support started showing warnings.

## What should I check after upgrading?

- Check internal tools that call the Docker API directly.
- Replace old Dockerfile `ENV key value` with `ENV key=value`.
- Avoid old storage drivers in CI runners.
- Treat Docker daemon access as host-level access.

## References

- Docker Engine 20.10 release notes: https://docs.docker.com/engine/release-notes/20.10/
