# Uninstalling Pterodactyl

:::warning
You will lose all data and this action is unreversible. Do not perform uninstall process for upgrading, instead follow the official upgrade instructions for [the panel](https://pterodactyl.io/panel/1.0/upgrading.html) and [the wings.](https://pterodactyl.io/wings/1.0/upgrading.html)
:::

## Uninstall Panel

Perform the following commands to delete the files related to the panel

```bash
# Panel files
sudo rm -rf /var/www/pterodactyl

# Pteroq queue worker
sudo rm /etc/systemd/system/pteroq.service

# If using nginx
sudo unlink /etc/nginx/sites-enabled/pterodactyl.conf

# If using apache
sudo unlink /etc/apache2/sites-enabled/pterodactyl.conf
```

You will be left with a database and the web server, you can find a tutorial on how to remove them at the bottom of this page.

## Uninstall Wings

Perform the following commands to delete the files related to wings, game servers, and backups

Check your wings config file for the server files path, your files might be at `/srv/daemon-data` if you upgraded from the 0.7x version.

```bash
# Stop the Wings
sudo systemctl stop wings

# Game server files and backups
sudo rm -rf /var/lib/pterodactyl

# Wings config
sudo rm -rf /etc/pterodactyl

# Wings binary
sudo rm /usr/local/bin/wings

# Wings daemon file
sudo rm /etc/systemd/system/wings.service
```

### Uninstall Web Server (optional)

Uninstall and remove NGINX. This step can be skipped if you still need the web server.

```bash
# If using debian/ubuntu
sudo systemctl stop nginx

sudo apt purge nginx nginx-common
sudo apt autoremove # remove any leftover dependencies

# If using CentOS
sudo service nginx stop

sudo yum remove nginx

```

Uninstall and remove Apache. This step can be skipped if you still need the web server.

```bash
# If using Ubuntu/Debian
sudo systemctl stop apache2

sudo apt purge apache2
sudo apt autoremove

# If using CentOS
sudo service apache2 stop

sudo yum erase httpd httpd-tools apr apr-util
```

### Database (Work in progress, not finished)

We search for all available databases and users, then delete the pterodactyl user and database. Replace `your_database`, `example_username` and `host` with your own results.

```bash
# Login to MySQL
mysql -u root -p

# Search for database and DROP (delete) it. Replace your_database with your actual database
SHOW DATABASES;
DROP DATABASE your_database; # ex. database name 'panel'

# Search for existing user and DROP (delete) it
SELECT User, Host FROM mysql.user;
DROP USER 'example_username'@'host'; # ex: 'pterodactyl'@'127.0.0.1'
```
