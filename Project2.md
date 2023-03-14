# Documentation of Project 2

`sudo apt update`

`sudo apt install nginx`

`sudo systemctl status nginx`

![Nginx Status](./Images/nginx-status.png))

 *curl http://localhost:80*

 ![Nginx Server Status](./images/nginx-server-status.png)


 `sudo apt install mysql-server`

 `sudo mysql`

 ![mysql ouput1](./images/mysql%20password%20output.png)

 `sudo mysql_secure_installation`

 `sudo mysql -p`

 ![mysql server installed](./images/mysql%20server%20installed.png)



`sudo apt install php-fpm php-mysql`


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



`sudo nano /var/www/projectLEMP/info.php`

`<?php
phpinfo();`

- [Nginx website url](http://18.119.123.254/info.php)

`sudo mysql -p`

`mysql> CREATE DATABASE `example_database`;`

`mysql>  CREATE USER 'example_user'@'%' IDENTIFIED WITH mysql_native_password BY 'password';`

`mysql> GRANT ALL ON example_database.* TO 'example_user'@'%';`

`mysql> exit`

`mysql> SHOW DATABASES;`

![Database](./Images/DatabaseOutput.png)

`CREATE TABLE example_database.todo_list (
mysql>     item_id INT AUTO_INCREMENT,
mysql>     content VARCHAR(255),
mysql>     PRIMARY KEY(item_id)
mysql> );`

`mysql> INSERT INTO example_database.todo_list (content) VALUES ("My first important item");`

`mysql> INSERT INTO example_database.todo_list (content) VALUES ("My second important item");`

`mysql> INSERT INTO example_database.todo_list (content) VALUES ("My third important item");`

`mysql> INSERT INTO example_database.todo_list (content) VALUES ("My fourth important item");`

![Output2](./Images/Output2.png)

`mysql> exit`

`nano /var/www/projectLEMP/todo_list.php`

`<?php
$user = "example_user";
$password = "password";
$database = "example_database";
$table = "todo_list";
try {
  $db = new PDO("mysql:host=localhost;dbname=$database", $user, $password);
  echo "<h2>TODO</h2><ol>";
  foreach($db->query("SELECT content FROM $table") as $row) {
    echo "<li>" . $row['content'] . "</li>";
  }
  echo "</ol>";
} catch (PDOException $e) {
    print "Error!: " . $e->getMessage() . "<br/>";
    die();
}`

