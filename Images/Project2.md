# Documentation of Project 2

### Installing nginx package
`sudo apt update`
`sudo apt install nginx`
`sudo systemctl status nginx`
![Nginx Status](./images/nginx-status.png))
 *curl http://localhost:80*
 ![Nginx Server Status](./images/nginx-server-status.png)


### Installing DBMS to be able to store and manage data for your site in a relational database
 `sudo apt install mysql-server`
 `sudo mysql`
 ![mysql ouput1](./images/mysql%20password%20output.png)
 `sudo mysql_secure_installation`
 `sudo mysql -p`
 ![mysql server installed](./images/mysql%20server%20installed.png)


### Installing PHP to proess code and generate dynamic content for the web browser
`sudo apt install php-fpm php-mysql`


### configuring nginx to use php processor
`sudo mkdir /var/www/projectLEMP`
`sudo chown -R $USER:$USER /var/www/projectLEMP`
`sudo nano /etc/nginx/sites-available/projectLEMP`
`sudo ln -s /etc/nginx/sites-available/projectLEMP /etc/nginx/sites-enabled/`
`sudo nginx -t`
![Checking syntax error](./images/checking%20syntax%20errors.png)
`sudo unlink /etc/nginx/sites-enabled/default'`
`sudo systemctl reload nginx`
`sudo echo 'Hello LEMP from hostname' $(curl -s http://169.254.169.254/latest/meta-data/public-hostname) 'with public IP' $(curl -s http://169.254.169.254/latest/meta-data/public-ipv4) > /var/www/projectLEMP/index.html`
![echo text returned](./images/hello%20LEMP%20word.png)


### Testing php with nginx
`sudo nano /var/www/projectLEMP/info.php`
`<?php
phpinfo();`
[My Nginx website url](http://18.119.123.254/info.php)