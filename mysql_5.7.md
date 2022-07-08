```sh
sudo rm -rf mysql*
sudo apt remove --purge mysql* -y
sudo apt purge mysql* -y
sudo apt autoremove -y
sudo apt autoclean -y
sudo apt remove dbconfig-mysql -y

sudo apt dist-upgrade -y # Gerekli

sudo apt update
sudo apt install wget -y --fix-missing
sudo apt-key adv --keyserver hkp://keyserver.ubuntu.com:80 --recv-keys 6494C6D6997C215E
wget http://repo.mysql.com/mysql-apt-config_0.8.10-1_all.deb
sudo dpkg -i mysql-apt-config_0.8.10-1_all.deb
# bionic
# 5.7

# sudo vi /etc/multipath.conf
# defaults {
#     user_friendly_names yes
# }
# blacklist {
#     devnode "^(ram|raw|loop|fd|md|dm-|sr|scd|st|sda)[0-9]*"
# }
echo $'defaults {\n\tuser_friendly_names yes\n}\nblacklist {\n\tdevnode "^(ram|raw|loop|fd|md|dm-|sr|scd|st|sda)[0-9]*"\n}' > /etc/multipath.conf

sudo apt-get update
sudo apt-cache policy mysql-server
sudo apt install -f -y mysql-client=5.7* mysql-community-server=5.7* mysql-server=5.7* --fix-missing

sudo mysql -u root -p
CREATE USER 'admin'@'%' IDENTIFIED BY 'Şifre';
GRANT ALL PRIVILEGES ON * . * TO 'admin'@'%';
FLUSH PRIVILEGES;
quit;




# Gerekli değil, yapılmasada olur
sudo mysql_secure_installation
- disallow root login remotely sorusuna no cevabı verilecek
```
