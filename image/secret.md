CYBERPANEL - CẤU TRÚC FILE  
cyperpanel sử dụng cấu trúc file mặc định cho các service hệ thống  
/usr/local/CyberCP/CyberCP/settings.py - cấu hình chính cho cyberpanel  
Các file data của CyberPanel: /usr/local/CyberCP/  
cyberpanel tạo user cyberpanel, với một số cấu hình đặt ở /home/cyberpanel  
Các tool hỗ trợ xem thông tin pass: /etc/cyberpanel  
cyberpanel hỗ trợ cli với lệnh cyberpanel  

AAPANEL - CẤU TRÚC FILE  
/www - tấ t cả các file cấu hình của aaPanel sẽ được đặt ở trong /www, bao gồm:  
wwwroot - chứa các domains folder và src web   
wwwlogs - chứa logs  
server - chứa config của các service  
backup - chứa các file backup  
aaPanel hỗ trợ cli với lệnh: bt  

AAPANEL - CẤU TRÚC FILE  
/www - tất cả các file cấ u hình của aaPanel sẽ được đặt ở trong /www, bao gồm:  
wwwroot - chứa các domains folder và src web  
wwwlogs - chứa logs  
server - chứa config của các service  
backup - chứa các file backup  
aaPanel hỗ trợ cli với lệnh: bt   

DIRECT ADMIN - CẤU TRÚC FILE  
Main directories and configs  
/usr/local/directadmin/ - main server path for the DirectAdmin panel itself.  
/usr/local/directadmin/conf/directadmin.conf - main config file for the  
directadmin service.  
/usr/local/directadmin/custombuild/ - the directory for the CustomBuild service. 
/usr/local/directadmin/conf/my.cnf - default mysql connection details for the directadmin service.
/usr/local/directadmin/data/users/[USERNAME] - config for one user  
/var/log/[service] - log for service in directadmin  
Hỗ trợ API: https://www.directadmin.com/api.php  
