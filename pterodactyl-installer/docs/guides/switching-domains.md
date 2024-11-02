# Switching Domains
::: tip
When switching domains, you will need to re-create any SSL certificates you may have been using, otherwise, your panel *and* nodes will be using invalid certificates.
See [Creating SSL Certificates](https://pterodactyl.io/tutorials/creating_ssl_certificates.html) for how to create these certificates before continuing.
:::

## The Panel
You must edit the `APP_URL` in the panel's `.env` file, *with `http://` or `https://`* (found at `/var/www/pterodactyl/.env`)

You will also need to edit the domain in your Webserver Configuration. See  [0.7 Webserver Configuration](https://pterodactyl.io/panel/0.7/webserver_configuration.html) or [1.0 Webserver Configuration](https://pterodactyl.io/panel/1.0/webserver_configuration.html) and edit the `<domain>` fields as appropriate.
## The Daemon/Wings
You must change the url for every node you wish to convert to the new domain in the panel's node settings (the `FQDN` field)

::: tip
You only need to do either the wings or daemon! you must also restart the daemon with `systemctl restart wings` once you change the file!
:::
### 1.0 Wings
Recopy the `config.yml` or manually edit the `remote` field in the existing file to match the panel's new url (found at `/etc/pterodactyl/config.yml`)
### 0.6 Daemon
Recopy the `core.json` or manually edit the `base_url` field in the existing file to match the panel's new url (found at `/srv/daemon/config/core.json`)

