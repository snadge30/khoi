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
sudo apt install php libapache2-mod-php php-mysql
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

