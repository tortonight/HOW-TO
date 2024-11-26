## Install Docker, Docker Compose and Portainer (CE/EE)

Welcome to my first Tutorial. This video will guide you through the Docker and Docker-Compose installation. Afterwards we will install Portainer (CE and EE) to manage our Docker hosts or Docker containers.

[Docker Install](https://docs.docker.com/engine/install/)
```bash
sudo -i
apt update && apt upgrade

# Add Docker's official GPG key:
sudo apt-get update
sudo apt-get install ca-certificates curl
sudo install -m 0755 -d /etc/apt/keyrings
sudo curl -fsSL https://download.docker.com/linux/ubuntu/gpg -o /etc/apt/keyrings/docker.asc
sudo chmod a+r /etc/apt/keyrings/docker.asc

# Add the repository to Apt sources:
echo \
  "deb [arch=$(dpkg --print-architecture) signed-by=/etc/apt/keyrings/docker.asc] https://download.docker.com/linux/ubuntu \
  $(. /etc/os-release && echo "$VERSION_CODENAME") stable" | \
  sudo tee /etc/apt/sources.list.d/docker.list > /dev/null
sudo apt-get update
```
* Install the Docker packages.
```
sudo apt-get install docker-ce docker-ce-cli containerd.io docker-buildx-plugin docker-compose-plugin
```
```
docker ps
docker-compose --version
```
Portainer Install
* CE Community Edition
```
docker volume create portainer_data_ce
```
```bash
docker run -d -p 8000:8000 -p 9443:9443 --name portainer-ce --restart=always -v /var/run/docker.sock:/var/run/docker.sock -v portainer_data_ce:/data portainer/portainer-ce:latest
```
* EE Business Edition Here is your Portainer Business Edition license key:

[license key](https://www.portainer.io/take-5)
```
docker volume create portainer_data_ee
```
```bash
docker run -d -p 8000:8000 -p 9443:9443 --name portainer-ee --restart=always -v /var/run/docker.sock:/var/run/docker.sock -v portainer_data_ee:/data portainer/portainer-ee:latest
```
Links:

[Portainer Install](https://www.portainer.io/install)

* Install Portainer with Docker on Linux

[Portainer Docs](https://docs.portainer.io/start/install/server/docker/linux)
