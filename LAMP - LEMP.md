# LAMP 

# Update
```
sudo apt update
```

# Bước 1: Install apache2
```
sudo apt install apache2
```

## Firewall allow apache và kiểm tra
```
ufw allow 'apache full'
ufw status
```
**Kiểm tra**
http: ServerIP

# Bước 2: Install MySQL
```
sudo apt install mysql-server
```
## Cài đặt cấu hình mysql
```
mysql_secure_installation
```
**Tạo database và user**
```
mysql
Create database wordpress_db;
CREATE USER 'user_name'@'%' IDENTIFIED BY 'password';
GRANT ALL ON wordpress_db.* TO 'user_name'@'localhost' WITH GRANT OPTION;
FLUSH PRIVILEGES;

Create database laravel_db;
CREATE USER 'user_name'@'%' IDENTIFIED BY 'password';
GRANT ALL ON laravel_db.* TO 'user_name'@'localhost' WITH GRANT OPTION;
FLUSH PRIVILEGES;
exit;
```
# Bước 3: Install PHP
```
sudo apt install php libapache2-mod-php php-mysql php-fpm
```
# Bước4: Install laravel và wordpress
**Install laravel**
```
apt install composer
composer create-project --prefer-dist laravel/laravel lavarel
```
**Cấu hình laravel**
```
sudo mv ~/lavarel/ /var/www/laravel
chown -R www-data:www-data laravel/*
```
**kết nối database**
```
vi .env 
```
**Install wordpress**
```
cd /var/www/
wget https://wordpress.org/latest.tar.gz
tar -xvzf latest.tar.gz
sudo chown -R www-data:www-data wordpress/*
cd wordpress
cp wp-config-sample.php wp-config.php
```
**Kết nối database**
```
vi wp-config.php
```
**Cấu hình Apache và VirtualHost**
```
cd /etc/apache2/sites-available/
```
```
cp 000-default.conf laravel.training.vn.conf

  <VirtualHost *:80>
   ServerName laravel.training.vn
   ServerAdmin webmaster@thedomain.com
   DocumentRoot /var/www/laravel/public

   <Directory /var/www/laravel>
       AllowOverride All
   </Directory>
   ErrorLog ${APACHE_LOG_DIR}/error.log
   CustomLog ${APACHE_LOG_DIR}/access.log combined
</VirtualHost>

```
```
cp 000-default.conf wordpress.training.vn.conf

  <VirtualHost *:80>
   ServerName wordpress.training.vn
   ServerAdmin webmaster@thedomain.com
   DocumentRoot /var/www/wordpress/

   <Directory /var/www/wordpress>
       AllowOverride All
   </Directory>
   ErrorLog ${APACHE_LOG_DIR}/error.log
   CustomLog ${APACHE_LOG_DIR}/access.log combined
</VirtualHost>

```
```
a2ensite laravel.training.vn
a2ensite wordpress.training.vn
```
**restart apache**
```
systemctl restart apache2.service
```
--- 
---
---
---
---

# LEMP

# Bước 1: Install Nginx

```
apt install Nginx
```
# Bước 2: Cài mysql và tạo database
```
sudo apt install mysql-server
mysql_secure_installation
mysql
Create database wordpress_db;
CREATE USER 'user_name'@'%' IDENTIFIED BY 'password';
GRANT ALL ON wordpress_db.* TO 'user_name'@'localhost' WITH GRANT OPTION;
FLUSH PRIVILEGES;

Create database laravel_db;
CREATE USER 'user_name'@'%' IDENTIFIED BY 'password';
GRANT ALL ON laravel_db.* TO 'user_name'@'localhost' WITH GRANT OPTION;
FLUSH PRIVILEGES;
exit;
```

# Bước 3: Cài php
```
sudo apt install php libapache2-mod-php php-mysql php-fpm
```
# Bước4: Install laravel và Wordpress
**Install laravel**
```
apt install composer
composer create-project --prefer-dist laravel/laravel lavarel
```
**Cấu hình laravel**
```
sudo mv ~/lavarel/ /var/www/laravel
chown -R www-data:www-data laravel/*
```
**kết nối database**
```
vi .env
```
```
cd /var/www/
wget https://wordpress.org/latest.tar.gz
tar -xvzf latest.tar.gz
sudo chown -R www-datall:www-data wordpress/*
cd wordpress
cp wp-config-sample.php wp-config.php
```
**Kết nối database**
```
vi wp-config.php
```

# Bước 5:Cấu hình nginx
```
cd /etc/nginx/sites-available
vi wordpress.training.vn
```
Nội dung
```
server {
    listen 80 default_server;

    root /var/www/html/wordpress;
    index index.php index.html index.htm;

    server_name wordpress.training.vn;
    location / {
        try_files $uri $uri/ /index.php;
    }

    location ~ \.php$ {
        fastcgi_pass unix:/run/php/php7.4-fpm.sock;
        include snippets/fastcgi-php.conf;
    }
}
```
vi laravel.training.vn
```
Nội dung
```
server {

    root /var/www/laravel/public;
    index index.php index.html index.htm;

    server_name laravel.training.vn;
    location / {
        try_files $uri $uri/ /index.php;
    }

    location ~ \.php$ {
        fastcgi_pass unix:/run/php/php7.4-fpm.sock;
        include snippets/fastcgi-php.conf;
    }
}

```
**Đồng bộ file cấu hình**
```
ln -s /etc/nginx/sites-available/wordpress.training.vn /etc/nginx/sites-enabled/
ln -s /etc/nginx/sites-available/laravel.training.vn /etc/nginx/sites-enabled/
rm /etc/nginx/sites-enabled/default
```
**Kiểm tra**
```
nginx -t
```
**Nếu đã đúng sẽ hiện:**
```
nginx: the configuration file /etc/nginx/nginx.conf syntax is ok
nginx: configuration file /etc/nginx/nginx.conf test is successful
```
**Restart Nginx**
```
systemctl restart nginx.service
```
