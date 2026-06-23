# Docker 25.0 NEW Features

Compared with Docker 24.0, Docker 25.0 is mainly important for backend networking and image portability.

## Multiple Networks

```bash
docker run \
  --network frontend \
  --network backend \
  my-api
```

Backend use case: an API receives traffic from one network and talks to databases or internal services on another.

## IPv6 Improvements

```bash
docker network create \
  --ipv6 \
  --subnet fd00:dead:beef::/64 \
  app-net
```

This matters only when your backend platform or tests need IPv6.

## OCI-compatible Image Output

```bash
docker image save my-api:latest -o my-api.tar
```

This matters when CI stores images as artifacts or passes them to scanners/deployment tools.

## What should I check after upgrading?

- Review containers attached to more than one network.
- Test IPv6 only if your platform needs it.
- Test image `save` and `load` flows in CI.

## References

- Docker Engine 25.0 release notes: https://docs.docker.com/engine/release-notes/25.0/
