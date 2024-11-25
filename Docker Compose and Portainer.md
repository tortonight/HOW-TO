## Install Docker, Docker Compose and Portainer (CE/EE)
Welcome to my first Tutorial. This video will guide you through the Docker and Docker-Compose installation. Afterwards we will install Portainer (CE and EE) to manage our Docker hosts or Docker containers.

```bash
sudo -i
apt update && apt upgrade
snap install docker          # version 27.2.0, or
apt  install docker-compose  # version 1.29.2-6
docker ps
docker-compose --version
```
* CE
```bash
docker run -d -p 8000:8000 -p 9443:9443 --name portainer-ce --restart=always -v /var/run/docker.sock:/var/run/docker.sock -v portainer_data_ce:/data portainer/portainer-ce:latest
```
* EE
* Here is your Portainer Business Edition license key:
* https://www.portainer.io/take-5
```bash
docker run -d -p 8000:8000 -p 9443:9443 --name portainer-ee --restart=always -v /var/run/docker.sock:/var/run/docker.sock -v portainer_data_ee:/data portainer/portainer-ee:latest
```
Links:

[Portainer](https://www.portainer.io)

* Install Portainer with Docker on Linux

[Portainer Docs](https://docs.portainer.io/start/install/server/docker/linux)
