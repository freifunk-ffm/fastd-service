# some needed tools
apt-get install vim
apt-get install telnet

# Ruby Version 1.9.1
https://library.linode.com/frameworks/ruby-on-rails-apache/debian-7-wheezy

apt-get install build-essential libapache2-mod-passenger apache2 ruby rdoc ruby-dev libopenssl-ruby rubygems
gem install fastthread
gem install sinatra-contrib

add path to /root/.bashrc

Adopt settings in config/conf.yml (copied from conf.yml.template)
The username and password do have to be configured in the file
config/bot_auth.yml(.template) in the ff-serv application.


/srv/www/fastd1.ffm.freifunk.net/ff-serv

# Apache

https://library.linode.com/web-servers/apache/installation/debian-6-squeeze

a2dissite default
service apache2 reload

vim /etc/apache2/sites-available/fastd1.ffm.freifunk.net

 <VirtualHost *:80>
      ServerAdmin info@wifi-frankfurt.de
      ServerName fastd1.ffm.freifunk.net
      ServerAlias fastd1.ffm.freifunk.net
      DocumentRoot /srv/www/fastd1.ffm.freifunk.net/fastd-service/public
      <Directory /srv/www/fastd1.ffm.freifunk.net/fastd-service/public>
          Allow from all
          Options -MultiViews
      </Directory>
      ErrorLog /srv/www/fastd1.ffm.freifunk.net/logs/error.log
      CustomLog /srv/www/fastd1.ffm.freifunk.net/logs/access.log combined
 </VirtualHost>

mkdir -p /srv/www/fastd1.ffm.freifunk.net/logs
cd /srv/www/fastd1.ffm.freifunk.net

git clone https://github.com/freifunk-ffm/fastd-service.git
cd ff-serv
git checkout ffm

chown www-data /srv/www/fastd1.ffm.freifunk.net -R

a2ensite fastd1.ffm.freifunk.net
servivce apache2 reload

chmod 0666 /srv/www/fastd.ffm.freifunk.net/ff-serv/log
