# Docker

## How to start with Docker

### Dockerfile with comments

```dockerfile
FROM node:15 # What image we need
WORKDIR /app # Create a workidir, (similar to baseUrl)
COPY package.json . # Copy package.json to our WORKDIR
RUN npm install # Execute npm install (build)
COPY . ./ # Copy all files to our WORKDIR
EXPOSE 3000 # Is just for information purpouse
CMD ["node", "index.js"] # Execute node index.js (after build)
```

### Ignore copy of some files

For ignore copy some files into the docker container, we need to create a .dockerignore file and put all the files we don't want to copy.

### Docker commands

#### Build commands

Build the image

```bash
docker build <Dockerfile-dir>
docker build .
```

Build the image with custom name

```bash
docker build -t <custom-image-name> <Dockerfile-dir>

# Examples:

docker build -t my-app-image .
```

#### List commands

List docker images

```bash
docker image ls
```

List running docker containers

```bash
docker ps
```

#### Run commands

Run docker image with custom name

- --name <custom-app-name> -> Name of the app
- --d -> Detach mode (Run container in background and print container ID)
- -p <outside_port>:<container_port> -> Allow to forward the traffic from the outside port to the container port

```bash
docker run -p <OUTSIDE_PORT>:<CONTAINER_PORT> -d --name <custom-app-name> <image-name>

# Examples:

docker run --name my-app my-app-image

docker run -d --name my-app my-app-image

docker run -p 4000:3000 -d --name my-app my-app-image
```

Run command inside docker container

- -it -> Interactive mode

```bash
docker exec -it <name-app> <command>

# Examples

docker exec -it my-app bash

```

#### Delete commands

Delete docker image

```bash
docker image rm <IMAGE ID>

# Examples:

docker image rm 1831ad8a8d8
```

Delete docker container

- -f -> Force delete even if the container is running

```bash
docker rm <container-name> -f

# Examples:

docker rm my-app -f
```

## Working with multiple containers

## Moving to Prod
