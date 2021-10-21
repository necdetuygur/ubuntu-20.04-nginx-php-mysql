# Ubuntu 20.04 Nginx PHP MySQL

## İşletim Sistemi
```sh
Ubuntu Server 20.04
```
## Kurulum Adımları

### Yönetici Olma
```sh
sudo su
```
### Paketlerin Depo Adreslerini Güncellenmesi
```sh
sudo apt update
```
### Varsa MySQL Sunucusu İle İlgili Tüm Verilerin Kaldırılması
```sh
sudo rm -rf mysql*
sudo apt remove --purge mysql\* -y
sudo apt purge mysql\* -y
sudo apt autoremove -y
sudo apt autoclean -y
sudo apt remove dbconfig-mysql -y
sudo apt dist-upgrade -y
```
### Tüm Servislerin Kurulması (PHP, MySQL, Nginx) (Tek satır yapıldı)
```sh
sudo apt install -y nginx php php-cli php-fpm php-json php-common php-mysql php-zip php-gd php-mbstring php-curl php-xml php-pear php-bcmath
```
### Servislerle Birlikte Gelen Apache Servisinin Kaldırılması
```sh
sudo service apache2 stop
sudo apt remove apache2 -y
sudo apt autoremove -y
```
### MySQL Servisinin Kurulumu
```sh
sudo mysql_secure_installation
- disallow root login remotely sorusuna no cevabı verilecek
```
### MySQL Kullanıcı Tanımlanması
```sh
sudo mysql
CREATE USER 'admin'@'%' IDENTIFIED BY 'Şifre';
GRANT ALL PRIVILEGES ON * . * TO 'admin'@'%';
FLUSH PRIVILEGES;
quit;
```
### PHP Servisinin Başlatılması &amp; Kontrolü
```sh
sudo systemctl restart php7.4-fpm.service
sudo systemctl status php7.4-fpm.service
```
### Composer Kurulumu
```sh
cd ~
curl -sS https://getcomposer.org/installer -o composer-setup.php
sudo php composer-setup.php --install-dir=/usr/local/bin --filename=composer
sudo ln /usr/local/bin/composer /usr/bin/composer
```
### Nginx Konfigürasyonu
```sh
rm /etc/nginx/sites-enabled/default
rm /etc/nginx/sites-enabled/site1
ln -s /etc/nginx/sites-available/site1 /etc/nginx/sites-enabled/site1
service nginx restart
```
### PHP Testi
```sh
mkdir /var/www/site1
mkdir /var/www/site1/public
echo "<?php phpinfo();" > /var/www/site1/public/index.php
```
### Test Sonrası Test Verilerinin Silinmesi
```sh
rm -rf /var/www/site1
```
### Projenin Sunucuya Getirilmesi
```sh
cd /var/www/
git clone git.com/site1 site1
```
### PhpMyAdmin
```sh
sudo apt install -y phpmyadmin
```