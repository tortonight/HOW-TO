# phpMyAdmin with Pterodactyl

[[toc]]

**phpMyAdmin** is a database administration tool. This guide aims to walk you through the setup of phpMyAdmin alongside pterodactyl panel in a non-destructive way.

:::danger Support Information
This guide or any other guides are not supported by Pterodactyl as `Pterodox` is a 3rd party. The guide is also proven to work in a non-destructive manner. <br />
**Proceed at own risk as we do not take responsibility for any data loss!**
:::

## Installing phpMyAdmin

:::warning Dependencies
The following guide assumes installation of phpMyAdmin alongside pterodactyl on a single web server, therefore it skips dependency installation
:::

### Installation 

```bash
mkdir /var/www/phpmyadmin && mkdir /var/www/phpmyadmin/tmp/ && cd /var/www/phpmyadmin
wget https://www.phpmyadmin.net/downloads/phpMyAdmin-latest-english.tar.gz
tar xvzf phpMyAdmin-latest-english.tar.gz
mv /var/www/phpmyadmin/phpMyAdmin-*-english/* /var/www/phpmyadmin
```

### Post Install

```bash
chown -R www-data:www-data * 
mkdir config
chmod o+rw config
cp config.sample.inc.php config/config.inc.php
chmod o+w config/config.inc.php
```

## Web Server Configuration


:::tip PHP Version
We assume you have followed the latest panel guide using PHP `8.1` <br />
You can easily update the version `fastcgi_pass unix:/run/php/php8.1-fpm.sock;` to suit your needs in the configuration below
:::

### NGINX

Create a file `phpmyadmin.conf` in `/etc/nginx/sites-available/` <br />
Replace `<domain>` with your desired phpMyAdmin domain

#### NGINX with SSL
<<< @/docs/.snippets/webservers/phpmyadmin/SSLnginx.nginx{3,9,21-22}

#### NGINX without SSL

<<< @/docs/.snippets/webservers/phpmyadmin/nginx.nginx{3}


**Applying Configuration**
```bash
# You do not need to symlink this file if you are using CentOS.
sudo ln -s /etc/nginx/sites-available/phpmyadmin.conf /etc/nginx/sites-enabled/phpmyadmin.conf

systemctl restart nginx
```

### Apache2
Create a file `phpmyadmin.conf` in `/etc/apache2/sites-available` <br />
Replace `<domain>` with your desired phpMyAdmin domain

#### Apache2 with SSL

<<< @/docs/.snippets/webservers/phpmyadmin/SSLapache.apacheconf{2,8,17-18}

#### Apache2 without SSL

<<< @/docs/.snippets/webservers/phpmyadmin/apache.apacheconf{2}


**Applying Configuration**

```bash
sudo ln -s /etc/apache2/sites-available/phpmyadmin.conf /etc/apache2/sites-enabled/phpmyadmin.conf
sudo a2enmod rewrite
systemctl restart apache2
```

## Configuring phpMyAdmin

Go to and follow instructions on  `<domain>/setup/index.php`

## Setting `blowfish_secret`
In order to use `Cookie` authentication, phpMyAdmin requires to use a blowfish secret in the `config.inc.php` file that needs to be copied out of the `config` directory.
```bash
cp /var/www/phpmyadmin/config/config.inc.php /var/www/phpmyadmin
```

after copying the file, edit it using your favorite editor and fill in the `blowfish_secret` with a 32 character string.

## Finalizing

To finish the setup, make sure to remove the config and setup folders of phpMyAdmin, this is done to prevent anyone from being able to administrate phpMyAdmin in the future
```bash
rm -rf /var/www/phpmyadmin/config
rm -rf /var/www/phpmyadmin/setup
```
