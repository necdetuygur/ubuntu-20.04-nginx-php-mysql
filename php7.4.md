```sh
sudo su
apt update
apt -y install software-properties-common
add-apt-repository ppa:ondrej/php
apt update
apt -y install php7.4
apt install -y php7.4-{bcmath,bz2,intl,gd,mbstring,mysql,zip,common,soap,intl,curl,gd,intl,xsl}
systemctl disable --now apache2
service apache2 stop
apt remove apache2 -y
apt autoremove -y
apt-get install nginx php7.4-fpm
```
