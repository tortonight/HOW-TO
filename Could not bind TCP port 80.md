If you get following error, when you try to start nginx…

[emerg]: bind() to 0.0.0.0:80 failed (98: Address already in use)

Then it means nginx or some other process is already using port 80.

You can kill it using:
```
sudo fuser -k 80/tcp
```
And then try restarting nginx again:
```
service nginx start
```
