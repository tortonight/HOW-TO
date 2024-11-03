# By default the root’s password on Ubuntu 24.10
```css
sudo passwd
[sudo] password for linuxconfig: 
Enter new UNIX password: 
Retype new UNIX password: 
passwd: password updated successfully
```
# sshd config root login on Ubuntu 24.10
```css
sudo sed -i 's/#PermitRootLogin prohibit-password/PermitRootLogin yes/' /etc/ssh/sshd_config
sudo service ssh restart
```
```bash
echo "Set disable_coredump false" >> /etc/sudo.conf
```
# Install older PHP versions on 24.10
```css
sudo add-apt-repository --remove ppa:ondrej/php
sudo add-apt-repository ppa:ondrej/php
sudo sed -i 's/oracular/noble/g' /etc/apt/sources.list.d/ondrej-ubuntu-php-oracular.sources
sudo apt update
sudo apt install php8.2 php8.1 php8.0 php7.4
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
sudo apt update && sudo apt upgrade -y
apt-get install sudo
visudo
%user       ALL=(ALL:ALL) ALL
```
```css
sudo apt-get install wget curl git screen net-tools -y
```
```bash
sudo timedatectl set-timezone Asia/Hong_Kong
```
# 🐦 pterodactyl-installer
```bash
bash <(curl -s https://pterodactyl-installer.se)
```
[Link](https://github.com/vilhelmprytz/pterodactyl-installer)
# 👷🏻‍♂️ ForestRacks Pterodactyl Installer
```bash
bash <(curl -Ss https://raw.githubusercontent.com/ForestRacks/PteroInstaller/Production/install.sh || wget -O - https://raw.githubusercontent.com/ForestRacks/PteroInstaller/Production/install.sh) auto
```
[Link](https://github.com/ForestRacks/PteroInstaller)
# 📝 dactyl-installer Official Pterodactyl Project.
```bash
bash <(curl -s https://dactyl.shardbyte.com)
```
[Link](https://github.com/Shardbyte/dactyl-installer)
# Pterodactyl-AutoAddons
```bash
bash <(curl -s https://raw.githubusercontent.com/Ferks-FK/Pterodactyl-AutoAddons/main/install.sh)
```
[Link](https://github.com/Ferks-FK/Pterodactyl-AutoAddons)
# 👨🏼‍💻 AMP CubeCoders
```bash
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
