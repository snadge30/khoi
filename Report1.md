## SSL

SSL là tiêu chuẫn mã hóa giữa trình duyệt và web server. 

# Có bao nhiêu cách chứng thực SSL ?
Domain Validation – DV SSL: là chứng chỉ xác thực tên miền dành cho các website cá nhân với khả năng mã hóa cơ bản.  
Organization Validation – OV SSL: là chứng chỉ xác thực dành cho các tổ chức và doanh nghiệp có độ tin cậy cao.  
Extended Validation – EV SSL: là loại chứng chỉ xác thực mở rộng, có độ tin cậy cao nhất thường được sử dụng cho các doanh nghiệp và tổ chức đang hoạt động.  
Wildcard SSL: dành cho các website có nhu cầu sử dụng SSL cho nhiều subdomain khác nhau. Đặc biệt, Wildcard SSL Certificate khác với các loại SSL thông thường là có thể chạy cho nhiều subdomain khác nhau và không bị giới hạn và chỉ cần một chứng chỉ SSL duy nhất.  
Subject Alternative Names – SANs SSL: Đây là loại chứng chỉ được thiết kế cho các ứng dụng Communication của Microsoft Exchange server, Microsoft Office Communications, Lync và cũng là giải pháp tiết kiệm cho Web Hosting và QA Testing.  


# CSR file dùng làm gì trong quá trình tạo SSL
Đây là 1 đoạn text chứa thông tin của chủ sở hữu tên miền được mã hóa. Thông tin này được gửi đến nhà cung cấp dịch vụ SSL để xác nhận.  
Sử dụng OpenSSL để gen file CSR sau đó request SSL cho domain tech.training.vietnix.tech  
**Tạo file csr**
```
https://csrgenerator.com/
```
**chuyển đổi 2 file .csr và .key sang .crt** : 
```
openssl x509 -req -in tech.training.vietnix.tech.csr -signkey tech.training.vietnix.tech.key -out tech.training.vietnix.tech.crt
```
# Pem file là gì ?
PEM là tệp văn bản chứa một hoặc nhiều mục trong mã hóa Base64 ASCII.  

# Private key ssl là gì ?
là file mã hoá được sinh ra cùng lúc khi tạo CSR.  

# PFX file là gì ? 
file .pfx là một loại tệp định dạng khóa cá nhân chứng thực, chứa một chứng chỉ số ký số SSL.  

# Cách chuyển từ file crt file sang PFX file.
openssl pkcs12 -export -out domain.name.pfx -inkey domain.name.key -in domain.name.crt  

## Domain
# Domain là gì ?
Domain (hay tên miền) là địa chỉ của một website trên Internet. Người dùng truy cập website bằng cách nhập tên miền vào trình duyệt.  

# Các trạng thái của domain
OK / activ :Tên miền hoạt động bình thường sau khi đăng ký.  
clientHold	:Trạng thái tạm ngừng tên miền 
addPeriod			         :         Trạng thái sau khi vừa đăng ký tên miền.  
autoRenewPeriod         :         Thời gian tự động gia hạn tên miền.  

inactive	 		           :      Name Server chưa thể liên kết với tên miền.  
pendingCreate			       :  Tên miền đang chờ được đăng ký.  
pendingDelete			       : Tên miền hết hạn đăng ký và chuẩn bị xóa.  
pendingRenew			       :   Tên miền đang chờ gia hạn.  
pendingRestore	       : Tên miền đã hết hạn đang chờ về trạng thái khôi phục (Active).  
pendingTransfer		    : Tên miền chờ chuyển đổi nhà đăng ký.  
pendingUpdate			     :   Tên miền đang chờ cập nhật.  
redemptionPeriod       : Tên miền đã hết hạn, cần thanh toán phí gia hạn  
renewPeriod		          :  Trạng thái tên miền được gia hạn.  
serverDeleteProhibited	 :	Ngăn tên miền của bạn bị xóa.  
serverHold			          :    Trạng thái tên miền không được kích hoạt trong DNS.  
serverRenewProhibited   : Trạng thái tên miền không thể được gia hạn.  
serverTransferProhibited :	Trạng thái không cho phép transfer tên miền.  
serverUpdateProhibited	 : Trạng thái không cho phép cập nhật tên miền.  
transferPeriod			     : Đây là trạng thái cho phép sau khi transfer tên miền thành thông thì nhà đăng ký mới có thể yêu cầu nhà cung cấp xóa tên miền.  

# Subdomain là gì?
Subdomain là phần mở rộng, phần bổ sung xuất hiện trước của tên miền chính.  

# Virtual Hosts là gì?
Virtual Host là một dạng lưu trữ mà bạn lưu được nhiều domain khác nhau trên cùng một máy chủ sever  

# Mail Server
Mail Server là một hệ thống máy chủ được cấu hình để thực hiện việc gửi và nhận thư điện tử.  

##Tìm hiểu MX Record
MX (mail exchanger) record là một bản ghi trong DNS zone xác định mail server nào chịu trách nhiệm nhận email.  

# Tìm hiểu DKIM, SPF, PTR
DKIM (DomainKeys Identified Mail) là một phương pháp xác thực email dựa trên chữ ký số. Phương pháp này có thể giúp giảm thiểu spam và email giả mạo  
SPF, SPF (Sender Policy Framework) là một tiêu chuẩn xác thực email sử dụng bản ghi DNS để xác định những máy chủ nào được phép gửi email từ một tên miền cụ thể. Khi một email được gửi đến một người dùng, máy chủ nhận email sẽ sử dụng bản ghi SPF của tên miền gửi để xác minh xem máy chủ gửi có được phép gửi email từ tên miền đó hay không. Nếu không, email có thể bị đánh dấu là thư rác hoặc bị từ chối.  

## DNS

# DNS là gì ?
DNS viết tắt của Domain Name System có nghĩa là hệ thống phân giải tên miền. DNS là hệ thống cho phép thiết lập tương ứng giữa địa chỉ IP và tên miền trên Internet.  

# Các loại recored DNS
CNAME Record: 	Là một bản ghi tên quy chuẩn (Canonical Name Record). Đây là một dạng bản ghi tài nguyên trong hệ thống tên miền.  
A Record: 	Dùng để trỏ tên miền website tới một địa chỉ IP cụ thể. Đây được xem là bản ghi DNS đơn giản nhất.  
MX Record: 	Bản ghi này bạn có thể sử dụng để trỏ tên miền đến mail server. MX Record chỉ định server nào quản lý các dịch vụ Email của tên miền đó.  
AAAA Record: 	Dùng để trỏ tên miền đến địa chỉ IPv6 và cho phép thêm host mới, TTL và IPv6.  
TXT Record: 	Ngoài ra, có thể thêm giá trị TXT, Host mới, TTL và Point To để chứa các thông tin định dạng văn bản domain.  
SRV Record: 	Đây là bản ghi DNS đặc biệt, dùng để xác định chính xác dịch vụ nào đang chạy Port nào.   
NS Record: 	Bản ghi này có thể chỉ định Name Server cho từng tên miền phụ và bên cạnh đó có thể tạo tên Name Server, TTL hay host mới.  

# Nguyên tắc làm việc của DNS
Khi người dùng truy cập một website, máy tính sẽ gửi yêu cầu đến máy chủ DNS cục bộ để tìm địa chỉ IP của website đó. Máy chủ DNS cục bộ sẽ kiểm tra cơ sở dữ liệu của mình xem có chứa địa chỉ IP của website hay không. Nếu có, sẽ trả về địa chỉ IP cho máy tính của người dùng.  

# Cách phân giải địa chỉ DNS
Bước 1: Khi bạn sẽ truy cập vào website của www.example.com bằng máy tính cá nhân, lúc này máy client sẽ gửi đến yêu cầu tìm địa chỉ IP của tên miền www.example.com đến máy chủ tên miền cục bộ.   

Bước 2: Tiếp tục, máy chủ miền cục bộ sẽ thực hiện rà soát các cơ sở dữ liệu để xem có những thông tin vào khác có tương ứng IP  tên miền “www.example.com” nữa không? Nếu không thì sẽ nhanh chóng trả IP của www.example.com cho máy Client.   

Trường hợp, nếu sau khi rà soát và không phát hiện cơ sở dữ liệu có liên quan đến miền www.example.com máy chủ miền cục bộ sẽ tiếp tục gửi yêu cầu đến ROOT Name Server.   

Bước 3: Tuy nhiên, Root Name Server không chứa thông tin về địa chỉ IP của www.example.com, mà chỉ chứa thông tin về máy chủ quản lý tên miền .com  

Khi đó Root Name Server sẽ gửi thông tin về địa chỉ máy chủ quản lý tên miền .com cho máy chủ tên miền cục bộ.  

Bước 4: Lúc này, máy chủ tên miền cục bộ sau đó sẽ gửi yêu cầu tìm kiếm đến máy chủ quản lý tên miền .com để tìm địa chỉ IP của www.example.com  

Máy chủ quản lý tên miền .com có cơ sở dữ liệu chứa thông tin về tất cả các tên miền .com, bao gồm cả www.example.com. Vì vậy, máy chủ quản lý tên miền .com sẽ trả lại địa chỉ IP của www.example.com cho máy chủ tên miền cục bộ.  

Bước 5: Bởi vì máy chủ quản lý tên miền com có chứa cơ sở dữ liệu của tất cả các website có đuôi .com  nên sẽ trả lại địa chỉ IP tên miền www.example.com cho máy chủ tên miền cục bộ.   

Bước 6: Cuối cùng máy chủ tên miền cục bộ sẽ gửi thông tin về tên miền www.example.com đến máy Client, sau đó client sẽ tiếp tục sử dụng ip vừa được cấp để truy cập tới máy  Server www.example.com. 
