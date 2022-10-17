# sshd_config on Ubuntu
```css
sudo passwd
[sudo] password for linuxconfig: 
Enter new UNIX password: 
Retype new UNIX password: 
passwd: password updated successfully

sudo sed -i 's/#PermitRootLogin prohibit-password/PermitRootLogin yes/' /etc/ssh/sshd_config
sudo service ssh restart
```
# sshd_config on Debian
```css
su -
sed -i 's/#PermitRootLogin prohibit-password/PermitRootLogin yes/' /etc/ssh/sshd_config
/etc/init.d/ssh restart
```
# Install SUDO on Debian
```css
su -
apt-get update
apt-get install sudo
visudo
%user       ALL=(ALL:ALL) ALL
```
```css
sudo apt-get install wget curl git screen -y
```
# 🐦 pterodactyl-installer
```
bash <(curl -s https://pterodactyl-installer.se)
```
[Link](https://github.com/vilhelmprytz/pterodactyl-installer)
# 👷🏻‍♂️ ForestRacks Pterodactyl Installer
```
bash <(curl -s https://raw.githubusercontent.com/ForestRacks/PteroInstaller/main/install.sh)
```
[Link](https://github.com/ForestRacks/PteroInstaller)
# Pterodactyl-AutoAddons
```
bash <(curl -s https://raw.githubusercontent.com/Ferks-FK/Pterodactyl-AutoAddons/main/install.sh)
```
[Link](https://github.com/Ferks-FK/Pterodactyl-AutoAddons)
# 👨🏼‍💻 AMP CubeCoders
```
bash <(wget -qO- getamp.sh)
```
Debian 8 64-bit or newer (Debian 10 or 11 Recommended)
Root access via SSH

[Link](https://cubecoders.com/AMPInstall)
# 👨‍🚒 Secure MariaDB Server
[mysql_secure_installation](https://github.com/tortonight/My-Virtual-Hosts-Configure/blob/main/mysql_secure_installation.md)

# Arma 3 Server on Linux
[link](https://github.com/tortonight/ArmA3-Server-on-Linux/blob/main/README.md)
# Jexactyl
[Jexactyl](https://docs.jexactyl.com/#/latest/panel/install/dependencies)
# hPanel
[hPanel](https://docs.halexnodes.net/hpanel/installation)
