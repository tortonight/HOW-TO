---
layout: page
#cover-img: https://live.staticflickr.com/4844/45489311404_0567577113_b.jpg
title: Using S3 for backups
subtitle: For when you would rather upload backups to the cloud
---

Create the following variables inside your `.env` file which is located at `/var/www/pterodactyl`

```bash
# Set your panel to use s3 for backups
APP_BACKUP_DRIVER=s3

# Info to actually use s3

AWS_DEFAULT_REGION=

AWS_ACCESS_KEY_ID=
AWS_SECRET_ACCESS_KEY=

# Name of the bucket that you created
AWS_BACKUPS_BUCKET=

# Only required if you're not using AWS
AWS_ENDPOINT=
```
