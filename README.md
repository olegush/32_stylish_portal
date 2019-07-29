# Shared CSS Library

This is the test stand for developing new css library. Uses [nginx](http://nginx.org/) on localhost as reverse proxy. Nginx proxying requests to the tested site except css file which replaced from local directory.


# How to Test

1. Install nginx:
```bash
sudo apt update
sudo apt install nginx
```

Goto http://127.0.0.1/ where you'll see welcome nginx page, if you don't, explore **/var/log/nginx/error.log** and **/var/log/nginx/access.log**. To reload server use `sudo nginx -s reload`.

2. Copy files from repository to local

3. **nginx.conf.template** file has two server blocks for proxying two sites. You can add or delete blocks if you need.

4. Create local css files to replace.

4. Create bash script, **run.sh**, for instance and put inside variables for template, bash commands and paths:

```bash
#!/usr/bin/env bash
export PORT1=port1
export SITE1=url1
export CSS_FILE1=css_filename1
export CSS_ALIAS_FILE1=abs/path/to/local.css1
export PORT1=port2
export SITE1=url2
export CSS_FILE1=css_filename2
export CSS_ALIAS_FILE1=abs/path/to/local.css2
envsubst < nginx.conf.template > nginx.conf
sudo ln -sf abs/path/to/created/nginx.conf /etc/nginx/sites-enabled
nginx -g 'daemon off;'
```

5. Run script:
```bash
sudo run.sh
```
The script creates **nginx.conf** based on **nginx.conf.template** with exported variables, creates symlink to nginx **sites-enabled** directory and reloads nginx.

6. Goto http://127.0.0.1:port1 or http://127.0.0.1:port2 and enjoy your new stylish sites.


# Project Goals

The code is written for educational purposes. Training course for web-developers - [DEVMAN.org](https://devman.org)
