# Install
```css
# su -
# sed -i 's/#PermitRootLogin prohibit-password/PermitRootLogin yes/' /etc/ssh/sshd_config
# /etc/init.d/ssh restart
```
```css
# su -
# apt-get update
# apt-get install sudo
# visudo
%user       ALL=(ALL:ALL) ALL
```
```css
# sudo apt-get install wget curl git screen -y
```
# 🐦 pterodactyl-installer
```css
# bash <(curl -s https://pterodactyl-installer.se)
```
# 👨‍🚒 Secure MariaDB Server
[mysql_secure_installation](https://github.com/tortonight/My-Virtual-Hosts-Configure/blob/main/mysql_secure_installation.md)
