# Docker Lab - Intro

##  Lab 1 : Installation

According to [Docker Docs](https://docs.docker.com/engine/install/ubuntu/), Docker Engine can be installed in different ways, depending on our needs:
-   Most users set up Docker’s repositories and install from them, for ease of installation and upgrade tasks. This is the recommended approach.

-   Some users download the DEB package and install it manually and manage upgrades completely manually. This is useful in situations such as installing Docker on air-gapped systems with no access to the internet.

-   In testing and development environments, some users choose to use automated convenience scripts to install Docker.

###  Linux 

#### For Ubuntu
#### 1. Set up the repository (Docker CE):

* Install packages to allow apt to use a repository over HTTPS.
```
sudo apt-get update
sudo apt-get install apt-transport-https ca-certificates curl gnupg-agent software-properties-common
``` 
* Add Docker’s official GPG key:

```sh
curl -fsSL https://download.docker.com/linux/ubuntu/gpg | sudo apt-key add -
```
* Set up the stable repository (amd64):
```sh
sudo add-apt-repository "deb [arch=amd64] https://download.docker.com/linux/ubuntu $(lsb_release -cs) stable"
```
#### 2. Install Docker
```
sudo apt-get update
sudo apt-get install docker-ce docker-ce-cli containerd.io
```
Executing the Docker Command Without Sudo (Optional):
```
sudo usermod -aG docker $(whoami)
```
Using the Docker Command

```
 sudo docker --help
 sudo docker info
 sudo docker "subcommand" --help
```
#### For CentOS
- Installation options are available on [Docker Docs for Centos](https://docs.docker.com/engine/install/centos/)
- Install using the repository
```
sudo yum install -y yum-utils
sudo yum-config-manager  --add-repo https://download.docker.com/linux/centos/docker-ce.repo
sudo yum install docker-ce docker-ce-cli containerd.io
```
- Start Docker Daemon
```
sudo systemctl start docker
sudo usermod -aG docker $USER
sudo chmod 777 /var/run/docker.sock
```
###  Windows 10 / 11
https://docs.docker.com/desktop/windows/install/ 

## Lab 2: Build and Manager images (Dockerfile)
- Docker offers two types of images:
    - OS images (ubuntu, debian, etc)
    - Dockerized Services /Apps Images (http, nodejs, mongodb, etc)
- Images are stored in the Docker Registry (Local, or remote like Docker Hub and Docker Store)

- Different methods to create Docker image :

    1. Image pull : loads an archive of files, as a base layer
    2. Container commit : create new couche (+ image) from current container
    3. Image build : construction form a Dockerfile (commands list)
### Working with Docker Images

Search for images available on Docker Hub:
```
sudo docker search Ubuntu
```
Download ubuntu image to your computer
```
sudo docker pull ubuntu 
Using default tag: latest
```
List all local docker images: 
```
sudo docker images
```
Pull Ubuntu 16.04 image
```
sudo docker pull ubuntu:16.04 
```
List all local docker images: 
```
sudo docker images
```
- Run a new container docker1
```
sudo docker run -it --name docker1 ubuntu:16.04 
```
- Run a new container docker2
```
sudo docker run -dt --name docker2 ubuntu:16.04 
```
Note:: -d (detach): Run container in background and print container ID 
-i (interactive): Keep STDIN open even if not attached 
-t (tty): Allocate a pseudo-TTY  
Use the following combination of keys instead: CTRL + P + Q. This command allows to leave the container without turning it off. If you use the exit command again within the container, it will shut down