# Docker for Backend Developers

Docker Engine does not use Java-style LTS labels in the official release notes. So, for this stack, the pages below use the stable Engine release branches from 2018 onward.

Each page explains the difference compared with the previous listed Docker version group and focuses only on what matters to backend engineers.

<img src="images/docker-backend-workflow.svg" />

## Versions

- [Docker Core Concepts](docker-core.md)
- [Docker 29.x](docker29.md)
- [Docker 26.x to 28.x](docker26-28.md)
- [Docker 25.0](docker25.md)
- [Docker 23.0 and 24.0](docker23-24.md)
- [Docker 18.09 to 20.10](docker18-20.md)

## Backend Mental Model

```text
source code -> Dockerfile -> image -> container
                         \-> Compose -> app + database + cache + queue
```

The image is the packaged application. The container is a running process created from that image. Compose is the local environment that lets your API run beside dependencies like PostgreSQL, Redis, Kafka, RabbitMQ, or LocalStack.

## References

- Docker Engine release notes: https://docs.docker.com/engine/release-notes/
- Docker Build secrets: https://docs.docker.com/build/building/secrets/
- Docker Compose secrets: https://docs.docker.com/compose/how-tos/use-secrets/
- Docker Compose Watch: https://docs.docker.com/compose/how-tos/file-watch/
