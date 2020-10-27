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
