# ping/hping3 ping đến domain vietnix.vn sau đó giải thích
## ping  

![ss1](/image/screenshot1.png)  

<strong>ICMP sed</strong> = số thứ tự của mỗi gói ICMP.  
<strong>from</strong> = Chỉ điểm đến và địa chỉ IP của nó.  
<strong>ttl</strong> = Chỉ giá trị Thời gian tồn tại từ 1 đến 255. Nó đại diện cho số bước nhảy mạng mà một gói tin có thể thực hiện trước khi bộ định tuyến loại bỏ nó.  
<strong>time</strong> = Chỉ thời gian gói tin đến đích và quay trở lại nguồn. Đơn vị đo lượng là mili giây.  


## hping3  

![ss2](/image/screenshot2.png)  
**len** = kích thước, tính bằng byte, của dữ liệu được thu thập từ tầng data link.   
**ip** = source ip address.  
**id** = trường ID IP.
**rtt** = thời gian khứ hồi tính bằng mili giây.  
**tos** = service của IP header.  
**iplen** = tổng của IP.  

# ssh command  

## Dùng password  
```
ssh username@serverip  
sau đó nhập password của user.
```
## Dùng key  
**Bước 1**: Tạo SSH Keygen  
ssh-keygen -t rsa  
Nếu bạn muốn chỉ định đường dẫn cho file SSH key thì thay thế “id_rsa” trong lệnh bằng đường dẫn tuyệt đối đến file.  
**Bước 2**: Nhập tên file  
Bạn cần đặt tên file cho SSH Keygen khi được yêu cầu.  
**Bước 3**: Nhập passphrase  
Sau khi đặt tên xong, hãy đặt (mật khẩu) cho tệp khi được yêu cầu. Thường mục này là không bắt buộc, bạn có thể để trống nếu muốn.  
**Bước 4**: Phân phối public key – SSH Keygen  
Thêm public key đã tạo đến máy chủ SSH. Bằng cách thêm nội dung của file public key vào file ‘authorized_keys’ trên máy chủ SSH của bạn.  
ssh-copy-id -i /path/to/key/file user@serverip  
**Bước 5**: Hoàn tất  
Kết nối vào máy chủ SSH Keygen sử dụng private key:  
```
ssh username@serverip -i ~/.ssh/private_key  
```
## Dùng port custom  
```
ssh username@serverip -p port_number  
```
# scp command
-P : Chỉ định port.  
-p : thời gian sửa đổi và truy cập file.  
-q : tùy chọn này nếu bạn muốn loại bỏ đo lường tiến trình và thông báo không lỗi.  
-C : Tùy chọn này buộc scp nén dữ liệu khi nó được gửi đến máy đích  
-r : sao chép các thư mục  

## scp 1 file
```
scp file.txt username@serverip:destination  
```
## scp 1 folder
```
scp -r folder username@serverip:destination  
```
# rsync command
Đồng bộ dữ liệu trên linux  

## rsync file
```
rsync -a file.txt file_backup.txt
```
## rsync folder
```
rsync -a /var/www/public_html/ /var/www/public_html_backup/
```
## rsync incremental
```
rsync -a source/oldfolder remote:source/folder source/newfolder  
```
# cat command
Dùng để hiển thị nội dung của file/tập tin ra màn hình hoặc copy nội dung tập tin, tạo mới tập tin,…   
```
cat [OPTIONS] [FILE_NAMES]
```
## cat nội dung 1 file
```
cat filename
```
## cat dòng thứ n trong file
```
cat -n filename | sed -n [n]p 
```
## cat nhiều dòng vào 1 file bằng EOF
```
cat <<EOF>> filename
```
# echo command
```
echo abc
```
## Dùng echo để chèn thêm 1 dòng vào cuối file
```
echo 'hello' >> filename
```
## Dùng echo để overwirte nội dung của file
```
echo 'hello' > filename
```
## tail/head command
```
head -n 3 text  
tail -n 7 text
```
## tail và tailf  
```
tail-f   // theo dõi sự thay đổi của file  
```
# sed command

## Dùng sed để find and replace một string trong file
```
sed -i 's/unix/linux/g' text  //replace unix = linux  
```
# traceroute/tracert commandl

Sau khi traceroute xong giải thích chi tiết kết quả trả về  
Dòng đầu tiên hiển thị tên máy chủ và ip đích, số bước nhảy tối đa đến máy chủ và kích thước của các gói được gửi.  
Các dòng tiếp theo là tên máy chủ được cung cấp, theo sau là ip của tên máy chủ, theo sau là thời gian cần cho một gói để đến máy chủ và quay lại.  

# netstat command

## hiển thị các socket đang listen
```
netstat -tln
```
## don't resolve hostname
```
netstat --numeric-hosts
```
## don't resolve portname
```
netstat --numeric-ports
```
## display process name/PID
```
netstat -tp
```
## only show tcp socket
```
netstat -at
```
## only show udp socket
```
netstat -au
```
# sort command
```
sort filename
```
## sort theo thứ tự tăng dần
```
sort filename
```
## sort theo thứ tự giảm dần
```
sort -r filename
```
## sort theo column
```
sort -k filename
```
## uniq command
-u Chỉ hiển thị các dòng không lặp lại  
-d Không hiển thị các dòng không lặp lại  
-c Hiển thị một báo cáo gồm dòng và số lần xuất hiện trong văn bản, khi tùy chọn này được sử dụng, hai tùy chọn -u và -d bị bỏ qua dù có được đưa vào lệnh hay không.  
-i Bỏ qua hoa - thường khi so sánh các dòng  
-f Bỏ qua một số trường trong mỗi dòng  
-s Bỏ qua một số ký tự trong mỗi dòng  
-w Chỉ định số ký tự cần so sánh khi so sánh dòng, các ký tự sau đó được bỏ qua  
--help Hiển thị thông báo trợ giúp  
--version Hiển thị thông tin phiên bản  
    
## lọc ra các dòng lặp lại trong một file
```
uniq -d
```
## lọc ra các dòng lặp lại trong file và đếm số lượng các dòng lặp lại
```
uniq -dc
```
#wc command

## Đếm số dòng trong file
```
ls | wc -l
```
## Đếm số kí tự trong file
```
ls | wc -w
```
# chmod, chown, chattr command

## Phân quyền bằng số, phân quyền bằng chữ
0 none  
1 execute only  
2 write only  
3 write and execute  
4 read only  
5 read and execute  
6 read and write  
7 read, write, execute  

# Đổi owner user/group
```
chown USER FILE
```
## Set Immutable Attribute
```
chattr [options] [attribute] [file]  
```
options   
    -R: Áp dụng thay đổi thuộc tính cho thư mục và tất cả các tệp con.  
    -v: Hiển thị thông báo khi thực hiện thay đổi thuộc tính.  
    -l: Hiển thị danh sách tất cả các thuộc tính của tệp tin. 
attribute  
    +i: Đặt thuộc tính chỉ đọc, ngăn chặn việc xóa hoặc chỉnh sửa tệp tin.  
    -i: Hủy bỏ thuộc tính chỉ đọc  
    +a: Đặt thuộc tính ghi thêm, chỉ cho phép thêm dữ liệu vào tệp tin, nhưng không được phép chỉnh sửa hoặc xóa.  
    +u: Đặt thuộc tính bảo vệ, ngăn chặn việc xóa tệp tin.  
    +d: Đặt thuộc tính không sao chép, ngăn chặn việc sao chép tệp tin.  


# find command

## find các file có đuôi .log
```
find . -type f -name "*.log"
```
## find các folder có tên abc
```
find . -name abc
```
## find các file có tên abc
```
find . -name abc
```
## find các file có tên abc và thực hiện phần quyền read only cho file
```
find . -name 'abc' -exec chmod 444 {} \;
```
# cp command

## cp file
```
cp file.txt file_backup.txt
```
## cp folder
```
cp -r /home/Video /home/new-folder
```
# mv command

## mv file, folder
```
mv filename/ newlocation/
```
# cut command

## cut kí tự thứ n trong string
```
cut -c [n] filename
```
## cut từ kí tự thứ n trở về sau
```
cut -c [n]- filename
```
## cut từ kí tự thứ n trở về trước
```
cut -c -[n] filename
```
# dig command

## Dùng Dig command để kiểm tra resolv record A, MX, NS
```
dig +short www.example.com A  
dig +short www.example.com MX  
dig +short www.example.com NS  
```
## Dùng Dig command để kiểm tra resolv record A, MX, NS với custom DNS

# tar/zip/unzip command

# Nén/Giải nén file tar.gz - Nén/Giải nén file .zip
```
tar -zxvf [file.tar.gz] - giai nen  
tar -zcvf [file.tar.gz] - nen  
```
# mount/umount command

## Add thêm một ổ cứng sdb ~ 5gb
```
fdisk /dev/sdb  
```
## Kiểm tra được có bao nhiêu ổ cứng trên máy chủ
```
fdisk -l  
```
## Mount ổ cứng vào /mnt/test
```
mount /dev/sdb /mnt/test  
```
## Umount /mnt/test
```
umount /mnt/test  
```
# Symbolic Links, Hard Links command

## Định nghĩ Sym Link
là một file tham chiếu đến file khác hoặc thư mục khác dưới dạng đường dẫn tương đối hoặc tuyệt đối  
```
ln -s [file nguồn] [file đích]
```
## Định nghĩ Hard Link
là các liên kết cấp thấp ( low-level links) mà hệ thống sử dụng để tạo các thành phần của chính hệ thống file, chẳng hạn như file và thư mục.  
```
ln [file nguồn] [file đích]  
```
## Ví dụ về Sym Link và Hard Link
| Hard links | Symbolic links |
|:-------|:------|
|  Chỉ liên kết được tới file, không liên kết được tới thư mục  |  Có thể liên kết được tới thư mục  |
|  Không tham chiếu được tới file trên ổ đĩa khác  |  Có thể tham chiếu tới file/thư mục khác ổ đĩa  |
| Liên kết tới một file vẫn còn ngay cả khi file đó đã được di chuyển | Liên kết không còn tham chiếu được nữa nếu file được di chuyển |
| Được liên kết với inode tham chiếu vật lý trên ổ cứng nơi chứa file | Liên kết tham chiếu tên file/thư mục trừu tượng mà không phải địa chỉ vật lý. Chúng được cung cấp inode riêng của mình |
| Có thể làm việc với mọi ứng dụng | Một số ứng dụng không cho phép symbolic link |

# ls command

## Liệt kê danh sách file/thư mục
```
ls
```
## Liệt kê danh sách file/thư mục và thuộc tính
```
ls -l
```
## Show file ẩn
```
ls -a
```
# ps command

## show tiến trình
```
ps aux
```
## kill tiến trình
```
kill [pid]
```
# top command

## Kiểm tra tài nguyên cpu đang sử dụng của một vài process đang chạy
```
top
```
## Giải thích về Load average, us, sy, ni, id, wa, hi, si, st, zombie process, sleeping process
us: thời gian CPU của người dùng (hoặc) % thời gian CPU dành cho không gian người dùng  
sy: thời gian CPU hệ thống (hoặc) % thời gian CPU dành cho không gian kernel  
ni: thời gian CPU đẹp của người dùng (hoặc) % thời gian CPU dành cho các quy trình có mức độ ưu tiên thấp  
id: thời gian CPU nhàn rỗi (hoặc) % thời gian CPU không hoạt động  
wa: io chờ thời gian CPU (hoặc) % thời gian CPU dành để chờ  
xin chào: irq phần cứng (hoặc) % thời gian CPU dành cho việc bảo trì/xử lý các gián đoạn phần cứng  
si: irq phần mềm (hoặc) % thời gian CPU dành để bảo trì/xử lý các gián đoạn phần mềm  
st:  thời gian CPU bị CPU ảo hoá  

# free command

## Giải thích ram used, free, shared, buff/cache, free
free : bộ nhớ chưa sử dụng , đây là tất cả bộ nhớ chưa được sử dụng cho bất kỳ thứ gì (kể cả bộ đệm) trong RAM  
shared : đây là dung lượng bộ nhớ được sử dụng chủ yếu cho tmpfs  
buff/cache , tổng số bộ đệm và bộ đệm:  
 -buff: bộ nhớ được sử dụng bởi bộ đệm kernel , là bộ nhớ mà kernel có thể tận dụng  
 -cache: Bộ đệm chứa nội dung của các tệp trong hệ thống tệp được lưu vào RAM và nói chung đây là một con số cao.  

# df command

## Xem dung lượng disk
```
df -h
```
## Phân vùng / là gì
là sự phân chia của đĩa cứng riêng biệt.
