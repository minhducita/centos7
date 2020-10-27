## Cài đặt Server CentOS 7 với các thành phần trên VirtualBox

- [1. Chuẩn bị VirtualBox, CentOS 7](#1)
- [2. Tạo máy ảo để cài CentOs](#2)
- [3. Cài đặt CentOS](#3)
- [4. Cài đặt mạng](#4)
- [5. Thiết lập IP tĩnh cho CentOS](5)
- [6. Cài đặt Apache](#6)
- [7. Cài đặt MySQL](#7)
- [8. Cài đặt PHP](#8)
- [9. Cài đặt phpMyAdmin](#9)
- [10. Cấu hình Virtual Host cho Domain](#10)
- [11. Tạo project laravel](#11)
	
<a name="1" />
	
### 1. Chuẩn bị VirtualBox, CentOS 7

Trước tiên cần tải về VirtualBox sau đó chạy bộ cài để cài đặt nó giống nhiều phần mềm khác trên Windows - [Tải VirtualBox](https://www.virtualbox.org/wiki/Downloads)

Tải file (ISO) của CentOS 7 tại: [Tải CentOS 7 ISO](https://www.centos.org/download/), để sử dụng làm Server với giao diện dòng lệnh, chọn DVD ISO, trong các list ISO có thể chọn CentOS-7-x86_64-DVD-1804.iso (chọn các host ở Việt Nam tải cho nhanh)

<a name="2" />

### 2. Tạo máy ảo để cài CentOs
- **Bước 1**:
- Chạy Oracle VM VirtualBox Manager đã cài đặt ở trên. Chọn New trên thanh công cụ, hộp thoại hiện thị hãy điền các thông tin muốn tạo máy ảo (đặt tên là CentOS, chọn Type = Linux, chọn Version = RedHat) như hình:

![alt text](https://xuanthulab.net/photo/cai-dat-centos-virtualbox-1-4374.PNG?raw=true)

- **Bước 2**:
- Từ hộp thoại trên, chọn Create a virtual hard disk now, rồi nhấn Create. Hộp thoại tạo ra để bạn thiết lập đĩa ảo cho máy. Có thể cấu hình các mục như hình, rồi bấm Create:

![alt text](https://camo.githubusercontent.com/e0683eb347bbad391d975debc2d48d645820cc6a/68747470733a2f2f7875616e7468756c61622e6e65742f70686f746f2f6361692d6461742d63656e746f732d7669727475616c626f782d312d343337342e504e473f7261773d74727565?raw=true)

- **Bước 3**:
- Từ danh sách các máy áo trong VirtualBox, nhấn phải chuột vào máy ảo mới tạo ra và chọn Setting để thiết lập thêm.

![alt text](https://xuanthulab.net/photo/cai-dat-centos-virtualbox-15-4377.png?raw=true)

- Chọn Display thiết lập bộ nhớ cho màn hình, cũng chọn Enable 3D Acceleration

![alt text](https://xuanthulab.net/photo/cai-dat-centos-virtualbox-4-4378.PNG?raw=true)

- Tại mục Storage chọn Controller: IDE > Empty (đây là ổ DVD ảo), sau đó bấm vào biểu tượng ổ đĩa và chọn gắn file ISO CentOS đã tải về ở trên vào.

![alt text](https://xuanthulab.net/photo/cai-dat-centos-virtualbox-15-4379.png?raw=true)

<a name="3" />
	
### 3. Cài đặt CentOS
Chọn máy ảo và nhấn vào Start, máy ảo sẽ khởi động và tự động boot từ DVD CentOS được gắn vào.
![alt text](https://xuanthulab.net/photo/cai-dat-centos-virtualbox-15-4380.PNG?raw=true)

Chờ một chút, sẽ tới màn hình tùy chọn đầu tiên để cài đặt.
![alt text](https://xuanthulab.net/photo/cai-dat-centos-virtualbox-15-4382.PNG?raw=true)

Ở màn hình này bạn có thể chọn English rồi nhấn Continue, ở màn hình tiếp theo chờ một chút nó kiểm tra các mục như màn hình.
![alt text](https://xuanthulab.net/photo/cai-dat-centos-virtualbox-15-4384.PNG?raw=true)

Chú ý ở mục này cần phải chọn ngay muc INSTALLATION DESTINATION nhằm chọn ổ đĩa để cài CentOS, khi chọn mục này hộp thoại như sau:
![alt text](https://xuanthulab.net/photo/cai-dat-centos-virtualbox-9-4385.PNG?raw=true)

Đánh dấu, chọn ổ đĩa cứng cần cài đặt sau đó nhấn vào DONE, cuối cùng nhấn Begin installation
Quá trình cài đặt CentOS sẽ bắt đầu
![alt text](https://xuanthulab.net/photo/cai-dat-centos-virtualbox-15-4386.PNG?raw=true)

Trong quá trình cài đặt đang diễn ra, bạn có thể chọn ROOT PASSWORD để đặt password cho user root (user root là user có quyền cao nhất để quản trị toàn bộ hệ thống server linux này).
Chờ cho quá trình cài đặt kết thúc thì khởi động lại máy ảo, từ đây bạn đã có một máy ảo chạy hệ điều hành CentOS để làm Server nghiên cứu.
![alt text](https://xuanthulab.net/photo/cai-dat-2-4387.PNG?raw=true)

Sau khi khởi động lại, CentOS yêu cầu đăng nhập hệ thống, bạn nhập user là root và password đã đặt ở trên để login vào hệ thống. Từ đây bạn bắt đầu phiên làm việc với CentOS. Đầu tiên gõ lệnh xem phiên bản CentOS đang sử dụng.
```sh
cat /etc/redhat-release
```


<a name="4" />
	
### 4. Cài đặt mạng
Mặc dù đã có máy ảo Cent OS 7, nhưng chưa cấu hình mạng nên chưa truy cập internet được, bước này ta thiết lập mạng cho CentOS và cập nhật CentOS
Đầu tiên kiểm tra card mạng, gõ lệnh sau:
```sh
nmcli d
```
![alt text](https://xuanthulab.net/photo/cai-dat-centos-virtualbox-15-4388.PNG?raw=true)

Do chưa được thiết lập bạn sẽ thấy thiết bị có tên enp0s3 có trạng thái là disconnected
Để cấu hình, gõ dòng lệnh sau:
```sh
nmtui
```

Giao diện xuất hiện bạn điều hướng bằng phím mũi tên lên xuống và phím tab để chọn các mục. Đầu tiên chọn đến Edit a connection rồi nhấn Enter
![alt text](https://xuanthulab.net/photo/cai-dat-centos-virtualbox-15-4389.PNG?raw=true)

Ở hộp thoại tiếp theo, chọn đến enp0s3, rồi chọn đến Edit ...
![alt text](https://xuanthulab.net/photo/cai-dat-centos-virtualbox-15-4390.PNG?raw=true)

Ở hộp thoại xuất hiện chọn đánh dấu vào mục: Automatically connect, rồi chọn OK
![alt text](https://xuanthulab.net/photo/cai-dat-centos-virtualbox-16-4391.PNG?raw=true)

Cuối cùng thoát trình cấu hình ra, (bạn cũng có thể nhập hostname ví dụ mydomain.com bằng tiện ích này) tiến hành khởi động lại card mạng bằng lệnh:
```sh
service network restart
```

Kiểm tra lại IP của máy ảo
```sh
ip a
```

```sh
# ip a

[root@mydomain ~]# ip a

1: lo: LOOPBACK,UP,LOWER_UP> mtu 65536 qdisc noqueue state UNKNOWN group default qlen 1000
    link/loopback 00:00:00:00:00:00 brd 00:00:00:00:00:00
    inet 127.0.0.1/8 scope host lo
       valid_lft forever preferred_lft forever
    inet6 ::1/128 scope host
       valid_lft forever preferred_lft forever
2: enp0s3: BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc pfifo_fast state UP group default qlen 1000
    link/ether 08:00:27:1e:a8:e7 brd ff:ff:ff:ff:ff:ff
    inet 192.168.1.6/24 brd 192.168.1.255 scope global noprefixroute dynamic enp0s3
       valid_lft 84530sec preferred_lft 84530sec
    inet6 fe80::f54e:d4a5:aaa0:345d/64 scope link noprefixroute
       valid_lft forever preferred_lft forever
[root@mydomain ~]#
```
Như vậy đã thiết lập mang xong cho CentOS, ở trường hợp trên đã được cấp phát IP là 192.168.1.6
Gõ lại lệnh sau để cập nhật các bản vá mới nhất của CentOS
```sh
yum -y update
```


<a name="5" />
	
### 5. Thiết lập IP tĩnh cho CentOS
Nếu muốn cấp phát IP tĩnh, cố định làm như sau:
Mở file thiết lập mạng ra để chỉnh sửa
```sh
vi /etc/sysconfig/network-scripts/ifcfg-enp0s3
```
Cập nhật IP chính các thông số như sau, nếu chưa có thì gõ vào
```sh
BOOTPROTO=static
IPADDR=192.168.1.99
NETMASK=255.255.255.0
GATEWAY=192.168.1.1
```
Địa chỉ IP tĩnh ở trên (192.168.1.99) bạn gán theo hệ thống mạng. Chỉnh xong khởi động lại mạng service network restart


<a name="6" />
	
### 6. Cài đặt Apache
Đầu tiền cần đảm bảo đã thiết lập hostname, bằng cách gõ lệnh hostname, nếu chưa thiết lập xem lại phần thiết lập mạng ở trên.
Chạy lệnh cài Apache
```sh
yum -y update
yum install httpd
```
Sau khi cài xong thì hãy chạy Apache
```sh
service httpd start
```
Để kiểm tra xem chạy OK chưa thì dùng lệnh:
```sh
# service httpd status

httpd.service - The Apache HTTP Server
Loaded: loaded (/usr/lib/systemd/system/httpd.service; enabled; vendor preset: disabled)
Active: active (running) since Sat 2018-11-03 06:32:09 EDT; 18min ago
Docs: man:httpd(8)
   man:apachectl(8)
```
Thiết lập để khởi động cùng hệ thống:
```sh
systemctl enable httpd.service
```
Apache đã hoạt động, tuy nhiên từ trình duyệt truy cập vào địa chỉ IP của máy ảo vẫn không thấy Apache hoạt động trả về trang web vì bị Firewall cản lại. Đến đây kiểm tra xem Firewall đang cho những dịch vụ nào truyền dữ liệu ra ngoài bằng lệnh
```sh
# firewall-cmd --list-all

public (active)
  target: default
  icmp-block-inversion: no
  interfaces: enp0s3
  sources:
  services: ssh dhcpv6-client
  ports:
  protocols:
  masquerade: no
  forward-ports:
  source-ports:
  icmp-blocks:
  rich rules:
```
Ở kết quả trên thì có các dịch vụ cho phép truyền dữ liệu ra ngoài đó là ssh, dhcpv6-client và chưa có Apache (httpd)

Cho thêm Apache được phép truyền dữ liệu ra ngoài bằng lệnh
```sh
firewall-cmd --add-service=http --permanent
firewall-cmd --add-service=https --permanent
```
Sau đó khởi động lại Firewall
```sh
firewall-cmd --reload
```
Lúc này từ trình duyệt ở máy host, có thể truy cập đến Webserver máy ảo bằng địa chỉ http://ip, ví dụ máy ảo có IP là 192.168.1.99 thì địa chỉ truy cập web lúc này là http://192.168.1.99, kết quả là:

![alt text](https://xuanthulab.net/photo/webserver-4394.PNG?raw=true)

Bỏ trang webcome mặc định của Apache
```sh
rm -f /etc/httpd/conf.d/welcome.conf
```
Mở file cấu hình Apache ra chỉnh sửa
```sh
vi  /etc/httpd/conf/httpd.conf
```
Mặc định trong đó có các thiết lập để chạy các file tại /var/www/html

Giờ thiết lập một số thông số sau
```sh
# dòng 151
AllowOverride All

# dòng 164 - tự động đọc index.html hoặc index.php truy cập thư mục
DirectoryIndex index.html index.php


# Thêm vào cuối
KeepAlive On
```
Cuối cùng khởi động lại Apache service httpd restart

Giờ nếu bạn có một file .html thì khi truy cập địa chỉ http://192.168.1.99 sẽ mở file đó. Hoặc sau khi cài PHP thì nếu có index.php thì truy cập http://192.168.1.99 sẽ chạy PHP

<a name="7" />
	
### 7. Cài đặt MySQL
Để tải code MySQL về và buil đầu tiên cài đặt tiên ích wget
```sh
yum install wget
```
Sau đó tải vào địa chỉ sau Repo MySQL tìm tên phiên bản mong muốn

Ví dụ tìm thấy tên mysql57-community-release-el7-9.noarch.rpm là phiên bản phù hợp muốn cài đặt, thì tải về với lệnh sau:
```sh
wget https://repo.mysql.com/mysql57-community-release-el7-9.noarch.rpm
```
Cập nhật Repo
```sh
rpm -ivh mysql57-community-release-el7-9.noarch.rpm
yum update
```
Giờ đã có thể dùng Yum để cài đặt MySQL
```sh
yum install mysql-community-server
```
Chạy MySQL
```sh
service mysqld start
```
Thiết lập MySQL tự động chạy
```sh
chkconfig mysqld on
```
Giờ đã có MySQL trong hệ thống, hãy tham khảo về Quản trị cơ bản MySQL

Password mặc định của root quản trị MySQL tự động sinh ra trong log
```sh
grep 'temporary password' /var/log/mysqld.log
```


<a name="8" />
	
### 8. Cài đặt PHP
Ở đây mình cài đặt là PHP 7.2
```sh
yum install https://dl.fedoraproject.org/pub/epel/epel-release-latest-7.noarch.rpm
yum install http://rpms.remirepo.net/enterprise/remi-release-7.rpm
yum install yum-utils
yum-config-manager --enable remi-php72
yum install php php-mcrypt php-cli php-gd php-curl php-mysql php-ldap php-zip php-fileinfo
```
Sau khi cài đặt gõ lệnh kiểm tra
```sh
php -v
```

<a name="9" />
	
### 9. Cài đặt phpMyAdmin
Để cài đặt PhpMyAdmin các bạn chỉ cần chạy lần lượt các lệnh sau
```sh
cd /usr/share
wget https://files.phpmyadmin.net/phpMyAdmin/5.0.2/phpMyAdmin-5.0.2-all-languages.zip
unzip phpMyAdmin-5.0.2-all-languages.zip
mv phpMyAdmin-5.0.2-all-languages phpMyAdmin
rm -rf phpMyAdmin-5.0.2-all-languages.zip
rm -rf /usr/share/phpMyAdmin/setup
```
 Cấu hình phpMyAdmin
 File cấu hình của PhpMyadmin là file config.inc.php. Trước tiên các bạn cần chạy lệnh sau
 ```sh
mv /usr/share/phpMyAdmin/config.sample.inc.php /usr/share/phpMyAdmin/config.inc.php
```
Tiếp theo mở file /usr/share/phpMyAdmin/config.inc.php
 ```sh
vi /usr/share/phpMyAdmin/config.inc.php
```
– Tìm
 ```sh
$cfg['blowfish_secret'] = '';
```
thêm một đoạn ký tự bất kỳ vào giữa cặp nháy đơn. Ví dụ:
 ```sh
$cfg['blowfish_secret'] = 'dsa123e12rwDSADs1few12tr3ewg3s2df3sAD';
```
– Tiếp theo thêm vào cuối file doạn code sau
 ```sh
$cfg['TempDir'] = '/usr/share/phpMyAdmin/tmp/';
```
Lưu file

Sau đó các bạn cần tạo thư mục tmp cho PhpMyAdmin
 ```sh
mkdir -p /usr/share/phpMyAdmin/tmp
chown -R nginx:nginx /usr/share/phpMyAdmin/tmp
```
Tiếp theo cấu hình vhost cho PhpMyAdmin
Để có thể truy cập được PhpMyAdmin các bạn sẽ cần tại vhost cho nó. Tạo file /etc/httpd/conf.d/phpmyadmin.conf với nội dung sau
 ```sh
Alias /pma /usr/share/phpMyAdmin
Alias /phpmyadmin /usr/share/phpMyAdmin
 
<Directory /usr/share/phpMyAdmin/>
    AddDefaultCharset UTF-8
    <IfModule mod_authz_core.c>
    # Apache 2.4
    <RequireAny>
        <RequireAll>
            Require all granted
        </RequireAll>
    </RequireAny>
    </IfModule>
    <IfModule !mod_authz_core.c>
        # Apache 2.2
        Order Deny,Allow
        Deny from All
        Allow from All
        Allow from ::1
    </IfModule>
</Directory>
<Directory /usr/share/phpMyAdmin/log/>
    Order Deny,Allow
    Deny from All
    Allow from None
</Directory>
<Directory /usr/share/phpMyAdmin/libraries/>
    Order Deny,Allow
    Deny from All
    Allow from None
</Directory>
<Directory /usr/share/phpMyAdmin/templates/>
    Order Deny,Allow
    Deny from All
    Allow from None
</Directory>
<Directory /usr/share/phpMyAdmin/tmp/>
    Order Deny,Allow
    Deny from All
    Allow from None
</Directory>
```

Cuối cùng khởi động lại apache để load cấu hình
 ```sh
systemctl restart httpd
```

Để truy cập giao diện phpMyAdmin, hãy mở trình duyệt của bạn và truy cập http://192.168.1.99/phpmyadmin:

![alt text](https://blog.hostvn.net/wp-content/uploads/2020/05/Screenshot_54.png?raw=true)
