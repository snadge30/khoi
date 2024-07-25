2. Khác nhau giữa MultiPHP Manager và Select PHP Version   
❌ Select PHP Version cho phép điều chỉnh php.ini (php config)  
câu đúng có thể là    
```
MultiPHP Manager hỗ trợ bởi cPanel
Select PHP Version hỗ trợ bởi cloudlinux
```

4. Cách download Access Log của user ở hosting cPanel  
B Sai  ❌ Login user cPanel -> Metrics -> Awstats  
✅ Login user cPanel -> Metrics -> Raw Access ~Logs~ 

6. Cách tìm add-on domain thuộc user nào trong WHM  
D Sai  ❌ Vào WHM -> List Add-on Domains -> nhập vào domain cần tìm  
✅ Vào WHM -> List Subdomains -> nhập vào domain cần tìm  

8. PHP X-Ray là gì ?   
A Sai  ❌ PHP X-Ray phân tích website trên hosting giúp tìm ra các vấn đề về cấu hình hosting.  
✅ php x-ray 

10. MultiPhp Manager là gì ?    
D Sai  ❌ Là ứng dụng thay đổi version PHP của Wordpress  
✅ L: Là ứng dụng quản lý phiên bản PHP của cpanel

12.  Khách nên trỏ record nào khi sử dụng hosting Vietnix   
D Sai  ❌ Record A  

13. E Đúng ✅  

14. Sự khác nhau giữa Jetbackup và tính năng Backup Wizard trong cPanel  
C Sai  ❌ Jetbackup yêu cầu người dùng backup thủ công, Backup Wizard được tự động backup   
D Sai  ❌ Backup Wizard hỗ trợ backup dữ liệu lên Google Drive, One Drive   

16. Cách kiểm tra số lượng của Number Of Processes đang chạy trong user cPanel ?   
B Sai  ❌ SSH vào hosting và kiểm tra bằng lệnh ps -aux | grep lsphp  | wc -l  
✅ Login vào user cPanel kiểm tra thong tin Number of Processes

18. Tính năng Mailing List trong cPanel là gì ?  
B Sai  ❌ Mailing List trong cPanel cung cấp tính năng tự động gửi thư theo lịch trình  
✅ dai nhat

20. Các cách có thể upload dữ liệu của user lên Hosting cPanel ?  
D Sai  ❌ Sử dụng File Upload, FTP, WinSCP, RSYNC  
✅ File Manager , FTP , ? scp ... FileZilla, WinSCP  

22. Plugin cache Wordpress tốt nhất khi sử dụng hosting cPanel Vietnix    
D Sai  ❌ ✅lightspeed cache

23. Khác nhau giữa Alias Domain và Redirect Domain ?   
D Sai  ❌ Alias Domain và Redirect Domain đều có chức năng chia sẻ nội dung giữa các tên miền khác nhau trên cùng một trang web  

|                Alias Domain               	|                     Redirect Domain                     	|
|:-----------------------------------------	  |:-------------------------------------------------------   |
| Là tên miền khác cho một website hiện có. 	| Chuyển hướng lưu lượng truy cập đến một website khác.   	|
| Chỉ hiển thị website chính.               	| Có thể hiển thị website riêng hoặc website chính.       	|
| Chia sẻ địa chỉ IP với website chính.     	| Có thể có địa chỉ IP riêng hoặc chung với website đích. 	|
| Tốt cho SEO.                              	| Ít ảnh hưởng SEO hơn.                                   	|
| Dễ sử dụng và quản lý.                    	| Có thể phức tạp hơn để thiết lập và quản lý.            	|


24. Select PHP Version là gì ?  
D Sai  ❌ Là ứng dụng quản lý bật tắt phiên bản PHP  
✅ Select PHP Version (hỗ trợ bởi cloudlinux): Có thể tùy chọn các phiên bản PHP khác nhau cho từng website.  

26. Phát biểu nào sau đây là đúng nhất về Redirect Domain trong cPanel?   
E Sai  ❌ Chuyển hướng domain ABC.com sang domain khác  l  
Chuyển hướng từ một tên miền cũ sang tên miền mới  
Chuyển hướng từ một tên miền phụ sang tên miền chính  
Chuyển hướng lưu lượng truy cập từ một trang web sang trang web khác  

28. Cấu hình trỏ domain về NS host179.vietnix.vn ?   
F Sai  ❌ Trỏ về NS ns1.vietnix.net, ns2.vietnix.net  
✅ ns1.host179.vietnix.vn ns2.host179.vietnix.vn  

30. File manager ở user cPanel hỗ trợ giao thức nào ?   
C Sai  ❌ FTP
✅ Http

32. Cách reload hosting cPanel khi full Number Of Processes tại Vietnix  
A Sai  ❌ Vào WHM -> Terminal -> chạy command cagefsctl  --reload <user>  
✅ > cagefs -m <user>  

33. Chọn câu đúng khi phát biểu về cPanel ở hosting Vietnix   
F Sai  ❌ cPanel hosting không hỗ trợ tính năng quản lý tài khoản, website, email, cơ sở dữ liệu
cPanel hosting hỗ trợ cài đặt nhiều phiên bản PHP khác nhau. 

35.  Cách truy cập giao diện quản lý cPanel WHM ?  
C Sai  ❌ https://host247.vietnix.vn:2083
✅ https://host247.vietnix.vn/whm
     
30. Vị trí access log mặc định trên hosting cPanel  
Không chọn đáp án  
✅ var/log/*apache2*/domlogs/


13. Cách chặn truy cập quốc tế đến 1 domain ở user cPanel   
✅ .htacces  

6. Cách hiện file ẩn trong File Manager.  
✅ đăng nhập -> files -> file manager -> settings - > chọn show hidden files (dotfiles). -> save  

Cách bật truy cập MySQL từ xa trên Hosting cPanel >>  
✅ Login user cPanel -> Databases -> Remote MySQL -> Add Access Host   

Cách xem log IP truy cập vào Domain ở user trên Hosting cPanel   
✅ Login user cPanel -> Metrics -> Visitors  

Cách tạo thêm một trang web của user trong Hosting cPanel ? >>   
✅ Login cPanel -> Domain -> Addon Domain -> Cấu hình database -> Kiểm tra website  
