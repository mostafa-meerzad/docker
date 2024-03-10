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

## Create Own Image (Dockerfile)

## Main Docker commands

## Image versioning

## Docker Workflow Big Picture
