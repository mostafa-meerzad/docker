# Docker Course

## What and Why of Docker

### What is Docker

Docker is a virtualization software that makes developing and deploying applications much easier.

It does that by packaging the application with all its dependencies, configuration, system tools and runtime into something called **Container**. which is portable artifact, easily shared and distributed.

`A Container is a standard unite that has everything an application needs to run`

### What problems Docker solves

#### DEVELOPMENT PROCESS **before containers**

each developer needs to **install and configure** all services **directly on their OS** on their local machine:

1. Installation process differs for each OS.
2. Many configuration steps where something can go wrong.

   for example:
   If your app uses 10 services, each developer needs to install these 10 services.

#### DEVELOPMENT process **with containers**

**Standardizes process** of running any services on any local dev environment

Each service is packaged:

- Own **isolated environment**
- Postgres packaged with all dependencies and configs

1. Start service as a **Docker Container** using **1 docker command**
2. command same for all OS
3. command same for all services
4. Easy to run different versions of the same app without any conflicts

#### Deployment process **before containers**

**Development team** would create a **package/artifact** along with an **installation instruction** on how to install and configure app on the server, then that instructions would be given to **Operations team**
which then would read them and install/configure the app on the server.
**_this process is very error pron and can be very frustrating_**

#### Deployment process **with containers**

Docker artifacts include everything the app needs, thus no configurations needed on the server except **Docker runtime** which results in less room for errors

## Docker vs Virtual Machines

### Why Docker is widely used

It offers compatibility.

### What advantages **Docker** has over **Virtual Machines**

- Docker only contains the **Application layer** and runs applications on that layer using the host machine's **kernel**
- **VMs** contain both the **Application layer** and **OS Kernel** which needs to simulate the whole Operating-system and run their own **kernel**

### What is the difference

- docker container sizes are much smaller compared to **VM images**
- Docker containers take seconds to run **VMs** take minuets to start

## Install Docker locally

It is best to refer to Docker's official documentations for installation guides.

### What do we get by installing docker-desktop

- docker engine:
  - a server with a long-running daemon process **dockerd**
  - manages containers and images
- docker cli client
  - command-line interface ("docker") to interact with **Docker Server**
  - execute docker commands to start/stop.. containers
- docker buildx
- extensions
- docker compose
- docker content trust
- kubernetes
- credential helper

## Images vs Containers

### Docker Image

A Docker image is an executable application artifact which includes application **source code, dependencies, complete environment configurations, any services needed, environment variables, create directories/files etc.**

### Docker Container

Is a running instance of a **docker image**
when we start the app it starts in a pre-configured environment which give us a **Container**

- you can run multiple containers from an image

## Public and Private Registries

Well to run images which will give use containers first we need to get those images from somewhere Right!. that is where docker **registry** comes in
**Docker registry** is a distribution system for docker images.

official images for applications like Nodejs, Mongodb, etc. are available and maintained by software authors in collaboration with docker community.

**Docker Hub** is the biggest docker-registry provided by docker and you can find official images of softwares you need.

- Technology changes and new versions of apps/services release and those show up as **tags** in **docker hub** with the app/service

### Pull an Image

1. find the image you want to install and run locally:
   - **Note:** picking a specific version is recommended
2. run `docker pull {package_name}:{package_tag}` it pull an image from a registry
   - `docker pull nginx:1.23`
   - **Docker hub** is the default registry when you pull an **image**
   - if you don't specify the image-version/tag docker will pull the **latest version**
3. run `docker images` to list all local images with some info

## Run Containers

1. run `docker run {name}:{tag}` which will create a **container** from the given image and runs it
2. The `docker ps` command is a powerful tool in Docker that lists Docker containers.
   - this lists **container id**, **image**, **command**, **time created**, **status**, **ports**, **name**: the name is randomly generated if you don't specify
3. `docker run -d {image}:{tag}` this command can be used to run a container in the background `-d = --detach` and prints the container-id
4. you may still want to see the logs, for debugging purposes `docker logs {container_id}` view logs from service running inside the container. which are present at the time of execution.
5. you can run docker images that are not locally installed docker **pulls** images from **docker hub** automatically

### Port Binding

binds container's port to the host's port to make the service available to the outside world;

applications inside container runs in an **isolated docker network** which allows us to run the same running on the same port multiple times, to access the services we need to **expose** the container port to the **host** (the machine the container runs on)

every service has a standard port and as a best practice we use the exact same port to expose it to;

you can do that when you run a container by providing **-p** or **--publish** publishes a container port to host.

`docker run -p {local_port}:{image's_port} {image_name}:{image_tag}`

only one service can run on a port at a time;

### Start/Stop containers

`docker run {image_name}` creates a new container every time you run this command it does not reuse the previously created containers if you run `docker ps -a` **-a** or **--all** lists all containers stopped or running

`docker stop {container_id}` to stop that running container gracefully

`docker kill {container_id}` to stop that running container forcefully

you can use **container_id** or **container_name** instead of its **id**

`docker run --name {custom_name} {other flags /optional } {image_name}`

### Private Docker Registries


## Create Own Image (Dockerfile)

## Main Docker commands

## Image versioning

## Docker Workflow Big Picture
