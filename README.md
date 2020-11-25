# Ubuntu 20.04 Nginx PHP MySQL

## İşletim Sistemi

Ubuntu Server 20.04

## Kurulum Adımları

### Yönetici Olma

sudo su

### Paketlerin Depo Adreslerini Güncellenmesi

sudo apt update

### Varsa MySQL Sunucusu İle İlgili Tüm Verilerin Kaldırılması

sudo apt remove --purge mysql\*

sudo apt purge mysql\*

sudo apt autoremove

sudo apt autoclean

sudo apt remove dbconfig-mysql

sudo apt dist-upgrade

### Tüm Servislerin Kurulması (PHP, MySQL, Nginx) (Tek satır yapıldı)

sudo apt install -y mysql-server nginx php php-cli php-fpm php-json php-common php-mysql php-zip php-gd php-mbstring php-curl php-xml php-pear php-bcmath

### Servislerle Birlikte Gelen Apache Servisinin Kaldırılması

sudo service apache2 stop

sudo apt remove apache2

### MySQL Servisinin Kurulumu

sudo mysql\_secure\_installation

- disallow root login remotely sorusuna no cevabı verilecek

### MySQL Kullanıcı Tanımlanması

sudo mysql

CREATE USER &#39;admin&#39;@&#39;%&#39; IDENTIFIED BY &#39;Şifre&#39;;

GRANT ALL PRIVILEGES ON \* . \* TO &#39;admin&#39;@&#39;%&#39;;

FLUSH PRIVILEGES;

quit;

### PHP Servisinin Başlatılması &amp; Kontrolü

sudo systemctl restart php7.4-fpm.service

sudo systemctl status php7.4-fpm.service

### Composer Kurulumu

cd ~

curl -sS https://getcomposer.org/installer -o composer-setup.php

sudo php composer-setup.php --install-dir=/usr/local/bin --filename=composer

sudo ln /usr/local/bin/composer /usr/bin/composer

### Nginx Konfigürasyonu

rm /etc/nginx/sites-enabled/default

rm /etc/nginx/sites-enabled/site1

ln -s /etc/nginx/sites-available/site1 /etc/nginx/sites-enabled/site1

service nginx restart

### PHP Testi

mkdir /var/www/site1

mkdir /var/www/site1/public

echo "\<?php phpinfo();" \> /var/www/site1/public/index.php

### Test Sonrası Test Verilerinin Silinmesi

rm -rf /var/www/site1

### Projenin Sunucuya Getirilmesi

cd /var/www/

git clone git.com/site1 site1
