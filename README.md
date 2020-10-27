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


[NextCloud](https://nextcloud.com) là một giải pháp lưu trữ dữ liệu giống như Dropbox, Google Drive hay OneDrive,... Bài viết này sẽ hướng dẫn các bạn cài đặt NextCloud trên CentOS 7.

| Thông tin máy chủ | |
|--|--|
| OS | CentOS 7 |
| CPU | 1 |
| RAM | 2 GB |
| IP Address | 192.168.100.192/24 |
| Gateway | 192.168.100.1 |


<a name="2" />
