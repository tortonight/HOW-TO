# HOW-TO
- [How to Install Let’s Encrypt SSL in Apache on Debian 11](https://www.itzgeek.com/how-tos/linux/debian/how-to-install-lets-encrypt-ssl-certificate-in-apache-on-debian-11.html)
- [How to Install and Configure Apache Web Server on Debian 10](https://vitux.com/debian-apache/)
---
# Allow SSH root login on Debian Linux
```css
# su -
# sed -i 's/#PermitRootLogin prohibit-password/PermitRootLogin yes/' /etc/ssh/sshd_config
# /etc/init.d/ssh restart
```
```css
#############################################################
To enable SSH login for a root user on Debian Linux system you need to first configure SSH server.
 Open /etc/ssh/sshd_config and change the following line:
#############################################################
# nano /etc/ssh/sshd_config
FROM:
# PermitRootLogin without-password
TO:
# PermitRootLogin yes
Once you made the above change restart your SSH server:

# /etc/init.d/ssh restart
[ ok ] Restarting ssh (via systemctl): ssh.service.
#############################################################
```
# Allow SSH root login on Ubuntu 18.04
```css
# sudo passwd
[sudo] password for linuxconfig: 
Enter new UNIX password: 
Retype new UNIX password: 
passwd: password updated successfully

# sudo sed -i 's/#PermitRootLogin prohibit-password/PermitRootLogin yes/' /etc/ssh/sshd_config
# sudo service ssh restart
```
---
# All About Sudo on a Debian 10 Buster System
```css
# su -
# apt-get update
# apt-get install sudo
# visudo
%user       ALL=(ALL:ALL) ALL
```
---
