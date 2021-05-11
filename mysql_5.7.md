```
sudo apt remove --purge mysql* -y
sudo apt purge mysql* -y
sudo apt autoremove -y
sudo apt autoclean -y
sudo apt remove dbconfig-mysql -y
sudo apt dist-upgrade -y

sudo apt update
sudo apt install wget -y
wget https://dev.mysql.com/get/mysql-apt-config_0.8.12-1_all.deb
mkdir /vagrant
cd /vagrant
sudo dpkg -i mysql-apt-config_0.8.12-1_all.deb
bionic
5.7

cd

sudo vi /etc/multipath.conf
defaults {
    user_friendly_names yes
}
blacklist {
    devnode "^(ram|raw|loop|fd|md|dm-|sr|scd|st|sda)[0-9]*"
}

sudo apt-get update
sudo apt-cache policy mysql-server
sudo apt install -f -y mysql-client=5.7* mysql-community-server=5.7* mysql-server=5.7*

sudo mysql -u root -p
CREATE USER 'admin'@'%' IDENTIFIED BY 'Şifre';
GRANT ALL PRIVILEGES ON * . * TO 'admin'@'%';
FLUSH PRIVILEGES;
quit;
```
