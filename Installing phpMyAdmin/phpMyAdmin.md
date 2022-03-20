# Installing phpMyAdmin

- Dependencies

The following guide assumes installation of phpMyAdmin alongside pterodactyl on a single web server, therefore it skips dependency installation
- Installation
```
mkdir /var/www/pma.mcpanalunit.net && cd /var/www/pma.mcpanalunit.net
wget https://www.phpmyadmin.net/downloads/phpMyAdmin-latest-english.tar.gz
tar xvzf phpMyAdmin-latest-english.tar.gz
mv /var/www/pma.mcpanalunit.net/phpMyAdmin-latest-english/* /var/www/pma.mcpanalunit.net
```
- Post Install
```
chown -R www-data:www-data * 
mkdir config
chmod o+rw config
cp config.sample.inc.php config/config.inc.php
chmod o+w config/config.inc.php
cp config/config.inc.php config.inc.php
rm -rf /var/www/pma.mcpanalunit.net/config
```
- Web Server Configuration
```
nano /etc/nginx/sites-available/pma.mcpanalunit.net.conf
```
NGINX without SSL
```
server {
    listen 80;
    server_name pma.mcpanalunit.net;

    root /var/www/pma.mcpanalunit.net;
    index index.php;

    # allow larger file uploads and longer script runtimes
    client_max_body_size 100m;
    client_body_timeout 120s;

    sendfile off;

    # See https://hstspreload.org/ before uncommenting the line below.
    # add_header Strict-Transport-Security "max-age=15768000; preload;";
    add_header X-Content-Type-Options nosniff;
    add_header X-XSS-Protection "1; mode=block";
    add_header X-Robots-Tag none;
    add_header Content-Security-Policy "frame-ancestors 'self'";
    add_header X-Frame-Options DENY;
    add_header Referrer-Policy same-origin;

    location / {
        try_files $uri $uri/ /index.php?$query_string;
    }

    location ~ \.php$ {
        fastcgi_split_path_info ^(.+\.php)(/.+)$;
        fastcgi_pass unix:/run/php/php8.0-fpm.sock;
        fastcgi_index index.php;
        include fastcgi_params;
        fastcgi_param PHP_VALUE "upload_max_filesize = 100M \n post_max_size=100M";
        fastcgi_param SCRIPT_FILENAME $document_root$fastcgi_script_name;
        fastcgi_param HTTP_PROXY "";
        fastcgi_intercept_errors off;
        fastcgi_buffer_size 16k;
        fastcgi_buffers 4 16k;
        fastcgi_connect_timeout 300;
        fastcgi_send_timeout 300;
        fastcgi_read_timeout 300;
        include /etc/nginx/fastcgi_params;
    }

    location ~ /\.ht {
        deny all;
    }
}
```
Ctrl+O To save | Ctrl+X To Exit
- Applying Configuration
```
sudo ln -s /etc/nginx/sites-available/pma.mcpanalunit.net.conf /etc/nginx/sites-enabled/pma.mcpanalunit.net.conf

systemctl restart nginx
```
- Install Let’s Encrypt Certificate Use the certbot command to create a Let’s Encrypt certificate and configure Nginx to use the certificate.
```
sudo certbot --nginx
```
