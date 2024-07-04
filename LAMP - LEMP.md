# LAMP + Larave

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
# Bước4: Install laravel
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
vi .env //
```
**Cấu hình apache và port 8001**
```
vi /etc/apache2/ports.conf
chỉnh port từ 80 thành 8001
```
```
cd /etc/apache2/sites-available/
cp 0000-default.conf laravel.conf
```
```
  <VirtualHost *:8001>
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
a2ensite laravel.conf
```
**restart apache**
```
systemctl restart apache2.service
```

# Kiểm tra
Serverip:8001

--- 
---

LEMP + Wordpress

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
exit;
```

# Bước 3: Cài php
```
sudo apt install php libapache2-mod-php php-mysql php-fpm
```
# Bước4: Cài wordpress
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

# Bước 5:Cấu hình nginx
```
cd /etc/nginx/sites-available
vi wordpress
```
Nội dung
```
server {
    listen 80;
    root /var/www/html/wordpress;
    index  index.php index.html index.htm;
    server_name nameserver or ip;
    client_max_body_size 500M;
    location / {
        try_files $uri $uri/ /index.php?$args;
    }
    location = /favicon.ico {
        log_not_found off;
        access_log off;
    }
    location ~* \.(js|css|png|jpg|jpeg|gif|ico)$ {
        expires max;
        log_not_found off;
    }
    location = /robots.txt {
        allow all;
        log_not_found off;
        access_log off;
    }
    location ~ \.php$ {
         include snippets/fastcgi-php.conf;
         fastcgi_pass unix:/var/run/php/php7.4-fpm.sock;
         fastcgi_param SCRIPT_FILENAME $document_root$fastcgi_script_name;
         include fastcgi_params;
    }
}
```
**Đồng bộ file cấu hình**
```
ln -s /etc/nginx/sites-available/wordpress /etc/nginx/sites-enabled/
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

# Kiểm tra
ServerIP:80
