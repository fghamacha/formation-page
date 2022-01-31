# Lab 1 : Installation

According to [Docker Docs](https://docs.docker.com/engine/install/ubuntu/), Docker Engine can be installed in different ways, depending on our needs:
-   Most users set up Docker’s repositories and install from them, for ease of installation and upgrade tasks. This is the recommended approach.

-   Some users download the DEB package and install it manually and manage upgrades completely manually. This is useful in situations such as installing Docker on air-gapped systems with no access to the internet.

-   In testing and development environments, some users choose to use automated convenience scripts to install Docker.

##  Linux 
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



##  Windows 10 / 11
https://docs.docker.com/desktop/windows/install/ 
