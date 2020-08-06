# Docker and Containers

Containers are a way to package software in a format that can run isolated on a shared operating system. Unlike Virtual Machines (VMs), containers do not bundle a full operating system - only the libraries and settings required to make the software work are needed. This makes for efficient, lightweight, self-contained systems and guarantees that software will always run the same, regardless of where it’s deployed.

Docker is a software platform for running containers.

## Get Docker

Docker can be installed on operating system platforms such as Linux, Mac and Windows. To download Docker and get installation instructions for your platform, head over to <https://www.docker.com/get-started>.

## Docker Hosts and Engines

A Docker host is an instance with an operating system such Linux, Mac or Windows that has the Docker engine installed. The Docker engine is typically referred to as just Docker.

The Docker engine is a client-server application made up of the Docker daemon, a REST API that specifies interfaces for interacting with the daemon, and a command line interface (CLI) client that talks to the daemon (through the REST API wrapper).

To check what version of Docker you have installed, run the command;

    docker version

To get system-wide information about your Docker host, run;

    docker info

## Docker Command Line (CLI) Reference

All Docker client commands start with docker. For a complete command line reference check out, <https://docs.docker.com/engine/reference/commandline/docker/>.

## Docker Images

Docker images are stored on your Docker Host and if they're not, Docker will attempt to pull these images from a container registry such as Docker Hub, the default container registry. You can also build your own images from a `Dockerfile`. For more information about building images, check out <https://docs.docker.com/engine/reference/builder/>.

| Command            | Description                                                   |
| :----------------- | :------------------------------------------------------------ |
| docker image ls    | Lists images on the Docker host.                              |
| docker image pull  | Pulls an image from a container registry to the Docker host.  |
| docker image push  | Pushes an image from the Docker host to a container registry. |
| docker image rm    | Removes an image from the Docker host.                        |
| docker image tag   | Tags an image.                                                |
| docker image build | Builds an image from a `Dockerfile`.                          |

### Examples

Downloads the `hello-world` image from the container registry to the Docker host.

    docker image pull hello-world

Downloads the `ubuntu` image tagged `20.04` from the container registry to the Docker host.

    docker image pull ubuntu:20.04

Deletes the `ubuntu` image tagged `20.04` from the Docker host.

    docker image rm ubuntu:20.04

Deletes all images on the Docker host.

    docker image rm $(docker image ls -q)

## Docker Containers

Docker containers are instantiated from Docker images.

To detach from a running container (must have been started with the `-it` flag), press `Ctrl` + `P` + `Q`. To reattach to the running container, use the command docker container attach.

| Command                | Description                                                         |
| :--------------------- | :------------------------------------------------------------------ |
| docker container run   | Starts a new container.                                             |
| docker container ls    | Lists running containers. Add the `-a` flag to show all containers. |
| docker container exec  | Runs a command in a running container.                              |
| docker container start | Starts a stopped container.                                         |
| docker container stop  | Stops a running container.                                          |
| docker container rm    | Removes a container.                                                |

### Examples

Launches a new container using the `hello-world` image.

    docker container run hello-world

Launches a new interactive container called `mycontainer` from the `ubuntu` image tagged `20.04` and passes it the command `/bin/bash`.

    docker container run -it --name mycontainer ubuntu:20.04 /bin/bash

Launches a new detached container called `web` and maps port `80` on the host to port `80` on the container using the image `httpd`.

    docker container run -d --name web -p 80:80 httpd

Stops all containers on the Docker host.

    docker container stop $(docker container ls -aq)

Deletes all containers on the Docker host.

    docker container rm $(docker container ls -aq)

## Docker Services

On a Docker swarm, containers can be orchestrated across a swarm when deployed as a service. They allow us to do things like scale an application and reconcile actual state with desired state for container deployments across a swarm. For more information about Docker services, checkout out <https://docs.docker.com/engine/swarm/how-swarm-mode-works/services/>.

| Command                 | Description                                   |
| :---------------------- | :-------------------------------------------- |
| docker service create   | Creates a new service.                        |
| docker service ls       | Lists services.                               |
| docker service ps       | Lists tasks in a service.                     |
| docker service rm       | Removes one or more services.                 |
| docker service update   | Updates a service.                            |
| docker service rollback | Reverts changes to a service's configuration. |
| docker service scale    | Scales one or more replicated services.       |

### Examples

Creates a service named `myservice` with `1` running task using the latest `alpine` image running the command `ping docker.com`.

    docker service create --replicas 1 --name myservice alpine ping docker.com

Lists the tasks running in the service `myservice`.

    docker service ps myservice

Scales the service `myservice` to `2` running tasks.

    docker service scale myservice=2

Deletes all services in a swarm.

    docker service rm $(docker service ls -q)

## Docker Stacks

Stacks essentially define applications that consists of multiple Docker services. Stacks are deployed from a Docker Compose YAML file. For more information Docker Compose YAML files, check out <https://docs.docker.com/compose/overview/>.

| Command               | Description                                     |
| :-------------------- | :---------------------------------------------- |
| docker stack deploy   | Deploys a new stack or updates an existing one. |
| docker stack ls       | Lists stacks.                                   |
| docker stack ps       | Lists tasks in a stack.                         |
| docker stack rm       | Removes one or more stacks.                     |
| docker stack services | Lists services in a stack.                      |

## Recommended Pluralsight Courses

1. Docker and Containers: The Big Picture by Nigel Poulton

   - <https://app.pluralsight.com/library/courses/docker-containers-big-picture/>

2. Docker and Kubernetes: The Big Picture by Nigel Poulton

   - <https://app.pluralsight.com/library/courses/docker-kubernetes-big-picture/>

3. Getting Started with Docker by Nigel Poulton

   - <https://app.pluralsight.com/library/courses/docker-getting-started/>

4. Docker Deep Dive by Nigel Poulton

   - <https://app.pluralsight.com/library/courses/docker-deep-dive-update/>

5. Docker Networking by Nigel Poulton

   - <https://app.pluralsight.com/library/courses/docker-networking/>

## References

- What is a Container?

  - <https://www.docker.com/resources/what-container>
