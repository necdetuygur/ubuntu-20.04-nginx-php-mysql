```sh
apt purge php* -y
apt autoclean -y
apt autoremove -y

apt install software-properties-common -y
add-apt-repository ppa:ondrej/php -y
apt update

apt install -y nginx php php-cli php-fpm php-json php-common php-mysql php-zip php-gd php-mbstring php-curl php-xml php-pear php-bcmath --fix-missing

apt install libpcre2-8-0 -y

apt install php8.0-intl -y
apt install php8.0-xmlrpc -y
apt install php8.0-soap -y
apt install php8.0-mcrypt -y
apt install php8.0-ldap -y

service apache2 stop
apt remove apache2 -y
apt autoremove -y

systemctl restart php8.0-fpm.service
service nginx restart
systemctl status php8.0-fpm.service
```
