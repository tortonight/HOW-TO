# Reverse Proxy

## For the Panel

As the panel is a basic PHP application running in the Laravel framework there isn't a lot to change here. Most Importantly we need to edit the `.env` file to tell Laravel(The panel) that it is running behind a reverse proxy and what IPs to trust with its traffic.

:::danger Backup your ENV file
In order to backup the `.env` file run the following
```bash
cd /var/www/pterodactyl
cp .env .env.back
```

In a case where you might need to restore the `.env` file run:
```bash
cd /var/www/pterodactyl
mv .env .env.old
cp .env.back .env
```
:::

### ENV Configuration

Use your favorite editor to open the `.env` file in the panel directory, Continue by adding or editing the following lines, omitting the `<>` brackets

```
TRUSTED_PROXIES=<IP Of your proxy>
APP_URL=<full URL your panel uses(Should include `http or https`)>
```

### Web Server Configuration

In order to use the panel behind a reverse proxy, you should use the HTTP configuration for the webserver. This is done as most reverse proxies break the encryption chain. 

You can find the official web server configuration here [Web server Configuration](https://pterodactyl.io/panel/1.0/webserver_configuration.html#nginx-without-ssl)

## For Wings

As Wings is controlled from the panel you need to enable the `Behind Proxy` option in the panel and redo the configuration step. Then restart wings by running `systemctl restart wings` to apply the config. Make sure your port configuration is correct as this may cause errors connecting to Wings websocket.
