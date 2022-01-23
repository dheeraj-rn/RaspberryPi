## Install
```
sudo apt install squid
sudo systemctl status squid.service
sudo mv /etc/squid/squid.conf /etc/squid/squid.conf.backup
sudo nano /etc/squid/squid.conf

sudo /usr/sbin/squid -k check
sudo /usr/sbin/squid -k parse

sudo squid -k reconfigure
sudo systemctl reload squid.service

sudo systemctl enable squid.service
sudo systemctl restart squid.service

curl -I https://google.com --proxy http://127.0.0.1:3128
```
Help: https://www.cyberciti.biz/faq/ubuntu-squid-proxy-server-installation-configuration/