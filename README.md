## Cài đặt Server CentOS 7 với các thành phần trên VirtualBox

- [1. Chuẩn bị VirtualBox, CentOS 7](#1)
- [2. Tạo máy ảo để cài CentOs](#2)
- [3. Cài đặt CentOS](#3)
- [4. Cài đặt Apache](#4)
- [5. Cài đặt MySQL](#5)
- [6. Cài đặt PHP](#6)
- [7. Cài đặt phpMyAdmin](#7)
- [8. Cấu hình Virtual Host cho Domain](#7)
- [9. Tạo project laravel](#8)
	
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
