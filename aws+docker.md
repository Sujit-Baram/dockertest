Startup Command for docker instance creation.
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
#!/bin/bash
sudo apt update -y

sudo apt install apt-transport-https ca-certificates curl software-properties-common -y

curl -fsSL https://download.docker.com/linux/ubuntu/gpg | sudo apt-key add -

sudo add-apt-repository "deb [arch=amd64] https://download.docker.com/linux/ubuntu $(lsb_release -cs) stable"

sudo add-apt-repository "deb [arch=amd64] https://download.docker.com/linux/ubuntu $(lsb_release -cs) stable"

sudo apt update
sudo apt install docker-ce -y
sudo apt install apache2 -y 
sudo mkdir -p /tmp/deployment/
sudo apt install wget -y
sudo apt install winzip -y

a2enmod proxy
a2enmod proxy_http
a2enmod proxy_ajp
a2enmod rewrite
a2enmod deflate
a2enmod headers
a2enmod proxy_balancer
a2enmod proxy_connect
a2enmod proxy_html

sudo docker run -it -p 8090:80 -v /tmp/deployment/:/var/www/html/ --name dockertest -d ubuntu/apache2

<VirtualHost *:80>
    	ProxyPreserveHost On
            
    	ProxyPass / http://aws IP:8090/
    	ProxyPassReverse / http://aws Ip:8090/
            
</VirtualHost>

deploy code in /tmp/deploment



