# xVPS
Bash Script for manage Nginx reverse proxy for Apache webserver in Ubuntu System

I'm bored with repetitive tasks, so i created it, can setup nginx reverse proxy for apache, create virtualhost, install wordpress with wp-cli, create database, etc.

This script created by following tutorial from : https://www.digitalocean.com/community/tutorials/how-to-configure-nginx-as-a-web-server-and-reverse-proxy-for-apache-on-one-ubuntu-14-04-droplet

### Using

```sh
wget https://raw.githubusercontent.com/sonajiyusup/xvps/master/xvps && chmod +x xvps
mv xvps /usr/local/bin
```

If show error cause certificate not valid, use --no-check-certificate

```sh
wget --no-check-certificate https://raw.githubusercontent.com/sonajiyusup/xvps/master/xvps && chmod +x xvps
mv xvps /usr/local/bin
```

Then just run, choose task and follow the instruction
```sh
xvps
```

### Screenshot

![Task Option](http://i.imgur.com/GOkbKn2.png)