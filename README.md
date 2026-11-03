# Hello World Docker

A minimal Node.js application that runs inside a Docker container and prints:

```text
Hello World from Docker!
```

## Prerequisites

- [Docker Desktop](https://www.docker.com/products/docker-desktop/) installed and running
- Git, if you want to clone the repository

## Run with Docker

Build the image from the `Dockerfile`:

```bash
docker build -t hello-world-docker .
```

Run the container:

```bash
docker run --rm hello-world-docker
```

You should see:

```text
Hello World from Docker!
```

The `--rm` option removes the container automatically when it exits.

## Run with Docker Compose

The existing `compose.yaml` starts the published `swostika19/hello-world-js:1.0` image:

```bash
docker compose up
```

Stop and remove the Compose container with:

```bash
docker compose down
```

To run the local Dockerfile through Compose instead, update the service to use:

```yaml
services:
  hello-world:
    build: .
    container_name: hello-world-container
```

Then run:

```bash
docker compose up --build
```

## Project structure

```text
.
├── app.js         # Node.js application
├── Dockerfile     # Instructions for building the image
└── compose.yaml   # Docker Compose configuration
```

## How it works

1. The image uses the lightweight `node:22-alpine` base image.
2. Docker sets `/app` as the working directory.
3. `app.js` is copied into the image.
4. The container starts `node app.js`.
