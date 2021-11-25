```sh
sudo apt-get update
sudo apt -y install software-properties-common
sudo add-apt-repository ppa:ondrej/php
sudo apt-get update
sudo apt -y install php7.4
sudo apt-get install -y php7.4-{bcmath,bz2,intl,gd,mbstring,mysql,zip,common,soap,intl,curl}
sudo systemctl disable --now apache2
service apache2 stop
apt remove apache2 -y
apt autoremove -y
sudo apt-get install nginx php7.4-fpm
```
