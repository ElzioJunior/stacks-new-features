# Docker 25.0 NEW Features

Compared with Docker 24.0, Docker 25.0 brought backend-relevant networking and image portability improvements.

## Multiple Networks at Container Create Time

Docker improved support for passing multiple `--network` flags when creating or running a container.

```bash
docker run \
  --network frontend \
  --network backend \
  my-api
```

For backend systems, this is useful when an API receives public traffic from one network and talks to internal services on another.

## IPv6 Improvements

Docker improved IPv6 behavior, including automatically enabling IPv6 on a network when an IPv6 subnet is specified.

```bash
docker network create \
  --ipv6 \
  --subnet fd00:dead:beef::/64 \
  app-net
```

The backend value is more predictable networking when services must be tested with IPv6 locally or in CI.

## Recursive Read-only Mounts

Docker 25.0 added support for recursive read-only mounts.

This is useful when a backend container needs config or test fixtures mounted read-only and you want nested mounts to stay read-only too.

## More OCI-compatible Image Save Output

`docker image save` became more OCI compatible.

```bash
docker image save my-api:latest -o my-api.tar
```

This matters when images move between Docker, scanners, artifact stores, or deployment tooling.

## What should I check after upgrading?

- Review containers that attach to more than one network.
- Test IPv6 if your backend platform supports it.
- Use read-only mounts for config and fixture data.
- Test `save` and `load` flows if CI stores image tar files.

## References

- Docker Engine 25.0 release notes: https://docs.docker.com/engine/release-notes/25.0/
