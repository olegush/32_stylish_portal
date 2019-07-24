# Shared CSS Library

This is the test stand for developing new css library. Uses [nginx](http://nginx.org/) on localhost as reverse proxy. Nginx proxying requests to the tested site except css file which replaced from local directory.


# How to Test

1. Install nginx:
```bash
sudo apt update
sudo apt install nginx
```

Goto http://127.0.0.1/ where you'll see welcome nginx page, if you don't, explore **/var/log/nginx/error.log** and **/var/log/nginx/access.log**. To reload server use `sudo nginx -s reload`.

2. Create config files and copy text from repository inside:
```bash
sudo nano /etc/nginx/sites-available/site1.conf
sudo nano /etc/nginx/sites-available/site2.conf
```

3. Create symlinks:
```bash
sudo ln -sf /etc/nginx/sites-available/site1.conf /etc/nginx/sites-enabled
sudo ln -sf /etc/nginx/sites-available/site2.conf /etc/nginx/sites-enabled
```

4. Create new css files with new styles according paths in the config files

5. Reload nginx:
```bash
sudo nginx -s reload
```

6. Goto http://127.0.0.1:8081 or http://127.0.0.1:8082 and enjoy your new stylish sites.


# Project Goals

The code is written for educational purposes. Training course for web-developers - [DEVMAN.org](https://devman.org)
