# xVPS
Bash Script for manage Nginx reverse proxy for Apache webserver in Ubuntu System

I'm bored with repetitive tasks, so i created it, can setup nginx reverse proxy for apache, create virtualhost, install wordpress with wp-cli, create database, etc.

This script created by following tutorial from : https://www.digitalocean.com/community/tutorials/how-to-configure-nginx-as-a-web-server-and-reverse-proxy-for-apache-on-one-ubuntu-14-04-droplet


### Tested in
Ubuntu 14.04
Ubuntu 15.04

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

### Option
##### MySQL
If you want to automatic authentication for MySql, create file /etc/xvps/mysql-auth.cnf
```sh
#MySQL auth
[client]
user=root
password=your-mysql-root-password
```
##### Wordpress
If you want to using default user account in every new wordpress installation, create file /etc/xvps/wp-config
```sh
#Default Wordpress user account
WPUSER=user-to-login
WPPASSWD=password-to-login
WPEMAIL=your@mail.com
```
If you want to custom in every new wordpress installation with wp-cli, create file /etc/xvps/wp-custom

```sh
sudo -u www-data -s -- <<-EOF
    wp --path=$WEBDIR (wp-cli option)
EOF
```
for example
```sh
#Input wordpress description
read -p "Wordpress - Description : " WPDESCRIPTION
#######
# With wp-cli, install plugin "disable-comments" and activate, etc..
# With wp-cli, delete default widget (recent-comment, archive, categories, meta)
# With wp-cli, execute database query to change blog description
# You can read wp-cli documentation for more information
########
sudo -u www-data -s -- <<-EOF
    wp --path=$WEBDIR plugin install disable-comments --activate
    wp --path=$WEBDIR plugin install google-sitemap-generator --activate
    wp --path=$WEBDIR widget delete recent-comments-2 archives-2 categories-2 meta-2
    wp --path=$WEBDIR db query "UPDATE wp_options SET option_value = '$WPDESCRIPTION' WHERE wp_options.option_name = 'blogdescription';"
EOF
EOF
```

### Screenshot
![Task Option](http://i.imgur.com/XriGKtb.png)