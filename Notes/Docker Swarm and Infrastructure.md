# Docker Swarm and Infrastructure

Containers run on Docker hosts, computers that have the Docker engine installed.

## Docker Hosts and Engines

A Docker host is an instance with an operating system such Linux, Mac or Windows that has the Docker engine installed. The Docker engine is typically referred to as just Docker.

The Docker engine is a client-server application made up of the Docker daemon, a REST API that specifies interfaces for interacting with the daemon, and a command line interface (CLI) client that talks to the daemon (through the REST API wrapper).

To check what version of Docker you have installed, run the command;

    docker version

To get system-wide information about your Docker host, run;

    docker info

## Docker Swarm

Docker hosts can be configured into one of two states.

1. Single-Engine Mode (Default)
2. Swarm Mode

In Swarm Mode, individual Docker hosts become a node in cluster called a swarm.

| Command                         | Description                                                                                                                                     |
| :------------------------------ | :---------------------------------------------------------------------------------------------------------------------------------------------- |
| docker swarm init               | Initializes a swarm. The host this command is run on will become a manager node.                                                                |
| docker swarm join               | Joins a Docker host to a swarm. The host this command runs on will join the swarm as a manager or worker node depending on the token passed in. |
| docker swarm leave              | Leaves a swarm. Manager nodes must be demoted first.                                                                                            |
| docker swarm join-token manager | Displays the join token for manager nodes.                                                                                                      |
| docker swarm join-token worker  | Displays the join token for worker nodes.                                                                                                       |
| docker node ls                  | Lists nodes in swarm.                                                                                                                           |
| docker node promote             | Promotes one or more nodes to manager in a swarm.                                                                                               |
| docker node demote              | Demotes one or more nodes from manager in a swarm.                                                                                              |

## Docker Networking

For containers to talk to anything, they need to be connected to a network. By default, an installation of Docker comes with a number of networks created for you. You can create and manage networks using the docker network command.

Networks in Docker have a driver and scope. Drivers essentially dictate the type of a network and the scope describes whether the network is available to the local host or swarm. For more information, check out <https://docs.docker.com/network/>.

| Command                   | Description                                            |
| :------------------------ | :----------------------------------------------------- |
| docker network ls         | Lists networks.                                        |
| docker network inspect    | Displays detailed information on one or more networks. |
| docker network create     | Creates a network.                                     |
| docker network connect    | Connects a container to a network.                     |
| docker network disconnect | Disconnects a container from a network.                |
| docker network rm         | Removes one or more networks.                          |
| docker network prune      | Removes all unused networks.                           |

## Docker Volumes

One way to get data in and out of containers is to mount volumes to them. A volume can be a folder on the local file system of a Docker host or a remote file system on a network share or storage array. To learn more, check out <https://docs.docker.com/storage/volumes/> and <https://docs.docker.com/storage/bind-mounts/>.

| Command               | Description                                           |
| :-------------------- | :---------------------------------------------------- |
| docker volume create  | Creates a volumes.                                    |
| docker volume inspect | Displays detailed information on one or more volumes. |
| docker volume ls      | Lists volumes.                                        |
| docker volume prune   | Remove all unused local volumes.                      |
| docker volume rm      | Removes one or more volumes.                          |

## Docker Secrets

A secret is a blob of data, such as a password, SSH private key, SSL certificate, or another piece of data that should not be transmitted over a network or stored unencrypted. In a Docker swarm you can centrally manage these secrets and securely transmit them to only those containers that need access to them. To learn more, check out <https://docs.docker.com/engine/swarm/secrets/>.

| Command               | Description                                           |
| :-------------------- | :---------------------------------------------------- |
| docker secret create  | Creates a secret.                                     |
| docker secret inspect | Displays detailed information on one or more secrets. |
| docker secret ls      | Lists secrets.                                        |
| docker secret rm      | Removes one or more secrets.                          |

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
