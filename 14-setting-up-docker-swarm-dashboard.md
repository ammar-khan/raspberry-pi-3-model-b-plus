# Setting Up Docker Swarm Dashboard (Portainer)

## How to setup Docker Swarm Dashboard on Raspberry Pi 3 Model B+

#### Prerequisite(s):
- [Install and Configure Docker on your Raspberry Pi 3 Model B+](./11-setting-up-docker.md)
- [Initialise and Configure Docker Swarm Cluster on all yours Raspberry Pi 3 Model B+](./13-setting-up-docker-swarm-cluster.md)

#### 1 - Install Portainer (Swarm Dashboard)
----

```console
pi@swarm-manager:~ $ sudo docker service create --name=docker_board --publish=8080:9000/tcp --constraint=node.role==manager --mount=type=bind,src=/var/run/docker.sock,dst=/var/run/docker.sock portainer/portainer
```
---
#### 2 - Open Docker Swarm Dashboard
---

> _Open in browser_
```
http://localhost:8080
```
> _or_

```
http://192.168.1.111:8080
```
