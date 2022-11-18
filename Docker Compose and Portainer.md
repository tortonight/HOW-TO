## Install Docker, Docker Compose and Portainer (CE/EE)
Welcome to my first Tutorial. This video will guide you through the Docker and Docker-Compose installation. Afterwards we will install Portainer (CE and EE) to manage our Docker hosts or Docker containers.

```bash
sudo -I
apt update && apt upgrade
apt install docker docker-compose
docker ps
docker-compose --version
```
* CE
```bash
docker run -d -p 8000:8000 -p 9443:9443 --name portainer-ce --restart=always -v /var/run/docker.sock:/var/run/docker.sock -v portainer_data_ce:/data portainer/portainer-ce:latest
```
* EE
```bash
docker run -d -p 8000:8000 -p 9443:9443 --name portainer-ee --restart=always -v /var/run/docker.sock:/var/run/docker.sock -v portainer_data_ee:/data portainer/portainer-ee:latest
```

