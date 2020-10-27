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
