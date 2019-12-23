# Docker
The modern way to run software on Linux is to use containers (e.g., docker).
You can almost follow [line-by-line instructions](https://docs.docker.com/install/linux/docker-ce/debian/)  with the caveat that whenever they write “amd64”, your need to substitute “arm64”.
I've choosen to install Docker from a package:
```
wget https://download.docker.com/linux/debian/dists/buster/pool/stable/arm64/docker-ce-cli_19.03.5~3-0~debian-buster_arm64.deb
wget https://download.docker.com/linux/debian/dists/buster/pool/stable/arm64/containerd.io_1.2.6-3_arm64.deb
wget https://download.docker.com/linux/debian/dists/buster/pool/stable/arm64/docker-ce_19.03.5~3-0~debian-buster_arm64.deb
sudo dpkg -i docker-ce-cli_19.03.5~3-0~debian-buster_arm64.deb
sudo dpkg -i containerd.io_1.2.6-3_arm64.deb 
sudo dpkg -i docker-ce_19.03.5~3-0~debian-buster_arm64.deb
```
The Docker daemon starts automatically.

Verify that Docker Engine - Community is installed correctly by running the hello-world image.
```
sudo docker run hello-world
```
