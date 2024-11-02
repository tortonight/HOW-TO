# Upgrade to php 7.4

[[toc]]

For for anyone with a `Malformed Communication Packet` error in their panel

You need to update php from 7.2 to 7.4.
:::tip
Add `sudo` as necessary if you are not `root`
:::
## Install php 7.4
### Install repository
```bash
# Ubuntu
## Install ondrej php repo
apt-add-repository ppa:ondrej/php

# Debian
## Install sury repo
sudo wget -O /etc/apt/trusted.gpg.d/php.gpg https://packages.sury.org/php/apt.gpg
echo "deb https://packages.sury.org/php/ $(lsb_release -sc) main" | sudo tee /etc/apt/sources.list.d/php.list

# CentOS 7
## Install Repos
yum install -y epel-release yum-utils
yum install -y http://rpms.remirepo.net/enterprise/remi-release-7.rpm
yum-config-manager --disable remi-php*
yum-config-manager --enable remi-php74

# CentOS 8
## Install Repos
dnf install epel-release
dnf install https://rpms.remirepo.net/enterprise/remi-release-8.rpm
dnf module reset php
dnf module enable php:remi-7.4
```

### Install php 7.4
```bash
# Ubuntu and Debian
apt update
apt -y install php7.4 php7.4-{cli,gd,mysql,pdo,mbstring,tokenizer,bcmath,xml,fpm,curl,zip}

# CentOS 7
## Install PHP 7.4
yum update -y
yum install -y php php-{common,fpm,cli,json,mysqlnd,mcrypt,gd,mbstring,pdo,zip,bcmath,dom,opcache}

# CentOS 8
## Install PHP 7.4
dnf update -y
dnf install -y php php-{common,fpm,cli,json,mysqlnd,gd,mbstring,pdo,zip,bcmath,dom,opcache}
```
## Update Webserver
### Nginx
```bash
nano /etc/nginx/sites-available/pterodactyl.conf
```
Change `fastcgi_pass unix:/run/php/php7.2-fpm.sock;` to `fastcgi_pass unix:/run/php/php7.4-fpm.sock;`
Note the change from 7.2 to 7.4
```bash
systemctl restart nginx
```
### Apache
```bash
# Enable php 7.4
a2enmod php7.4
# Disable php 7.2 
a2dismod php7.2
```
