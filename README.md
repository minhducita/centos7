## Cài đặt Server CentOS 7 với các thành phần trên VirtualBox

- [1. Chuẩn bị VirtualBox, CentOS 7](#1)
- [2. Tạo máy ảo để cài CentOs](#2)
	- [2.1 Cài đặt LAMP Stack](#21)
	- [2.2 Cấu hình MariaDB](#22)
	- [2.3 Tạo User và Database cho NextCloud](#23)
	- [2.4 Tải và giải nén NextCloud](#24)
	- [2.5 Cấu hình NextCloud](#25)
	
<a name="1" />
	
### 1. Giới thiệu

[NextCloud](https://nextcloud.com) là một giải pháp lưu trữ dữ liệu giống như Dropbox, Google Drive hay OneDrive,... Bài viết này sẽ hướng dẫn các bạn cài đặt NextCloud trên CentOS 7.

| Thông tin máy chủ | |
|--|--|
| OS | CentOS 7 |
| CPU | 1 |
| RAM | 2 GB |
| IP Address | 192.168.100.192/24 |
| Gateway | 192.168.100.1 |


<a name="2" />
