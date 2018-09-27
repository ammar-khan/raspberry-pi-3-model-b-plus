# Setting Up Docker Swarm Cluster

# How to do a Raspberry Pi 3 Model B+ Docker Swarm Cluster setup

#### Prerequisite(s):
- [Install and Configure Docker on your Raspberry Pi 3 Model B+](./11-setting-up-docker.md)

#### 1 - Make Sure Docker is Working Correctly on Manager Pi
---

```console
pi@swarm-manager:~ $ sudo docker info
```

---
#### 2 - Initialise Docker Swarm (Manager)
---

```console
pi@swarm-manager:~ $ sudo docker swarm init
```

> _Note: above command gives you token to connect swarm worker with swarm manager `docker swarm join --token TOKEN IP-ADDRESS:2377`_

---
#### 3 - Join Docker Swarm (Worker)
---
##### a) Make Sure Docker is Working Correctly on Worker Pi (if not install Docker)
```console
pi@swarm-worker:~ $ sudo docker info
```

##### b) Join Worker Pi with Manager Pi
```console
pi@swarm-worker:~ $ sudo docker swarm join --token TOKEN IP-ADDRESS:2377
```

#### 4 - Confirm All Swarm Worker Pis are Joined with Docker Swarm Manager
```console
pi@swarm-manager:~ $ sudo docker node ls
```





