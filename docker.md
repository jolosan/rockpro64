# Docker
The modern way to run software on Linux is to use containers (e.g., docker).
You can almost follow [line-by-line instructions](https://docs.docker.com/install/linux/docker-ce/debian/)  with the caveat that whenever they write “amd64”, your need to substitute “arm64”.
I've choosen to install Docker from a package:
```
$ wget https://download.docker.com/linux/debian/dists/buster/pool/stable/arm64/docker-ce-cli_19.03.5~3-0~debian-buster_arm64.deb
$ wget https://download.docker.com/linux/debian/dists/buster/pool/stable/arm64/containerd.io_1.2.6-3_arm64.deb
$ wget https://download.docker.com/linux/debian/dists/buster/pool/stable/arm64/docker-ce_19.03.5~3-0~debian-buster_arm64.deb
$ sudo dpkg -i docker-ce-cli_19.03.5~3-0~debian-buster_arm64.deb
$ sudo dpkg -i containerd.io_1.2.6-3_arm64.deb 
$ sudo dpkg -i docker-ce_19.03.5~3-0~debian-buster_arm64.deb
```
The Docker daemon starts automatically.

Verify that Docker Engine - Community is installed correctly by running the hello-world image.
```
$ sudo docker run hello-world
```

Now follow the [Post-installation steps for Linux](https://docs.docker.com/install/linux/linux-postinstall/)

# Docker Compose
Compose is a tool for defining and running multi-container Docker applications. With Compose, you use a YAML file to configure your application’s services. Then, with a single command, you create and start all the services from your configuration.
Using Compose is basically a three-step process:

* Define your app’s environment with a Dockerfile so it can be reproduced anywhere.
* Define the services that make up your app in docker-compose.yml so they can be run together in an isolated environment.
* Run docker-compose up and Compose starts and runs your entire app.

```
sudo apt install docker-compose
```
A **docker-compose.yml** looks like this:
```
version: '3'
services:
  web:
    build: .
    ports:
    - "5000:5000"
    volumes:
    - .:/code
    - logvolume01:/var/log
    links:
    - redis
  redis:
    image: redis
volumes:
  logvolume01: {}
```
