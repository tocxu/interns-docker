
#1. Enable UFW forwarding
kiểm tra:
> sudo ufw status

Nếu chưa active:
> ufw enable

Edit file: **/etc/default/ufw**

Set the DEFAULT_FORWARD_POLICY policy to:

```
DEFAULT_FORWARD_POLICY="ACCEPT"
```
reload ufw
> ufw reload

**Allow incoming connections on the Docker port** (Mở cổng kết nối trên Docker:)

> sudo ufw allow 2375/tcp

#2. Configure a DNS server for use by Docker

Hệ thống chạy Ubuntu hoặc một dẫn xuất Ubuntu trên máy tính để bàn thường sử dụng 127.0.0.1 như máy chủ mặc định trong file ```/etc/resolv.conf```. Các NetworkManager cũng thiết lập ```dnsmasq``` để sử dụng các máy chủ DNS thực của kết nối và thiết lập ```nameserver``` **127.0.0.1** trong ```/etc/resolv.conf```.

Cảnh báo: DNS phân giái cục bộ (127.0.0.1) tìm thấy trong ```resolv.conf``` và container
không thể sử dụng nó. Sử dụng máy chủ mặc định bên ngoài: ```[8.8.8.8 8.8.4.4]```

**Để chỉ định một máy chủ DNS để sử dụng bởi Docker:**
> sudo nano /etc/default/docker

**Thêm một cài đặt cho Docker:**
```
DOCKER_OPTS="--dns 8.8.8.8"
```
Thay 8.8.8.8 với một máy chủ DNS cục bộ như 192.168.1.1. Bạn cũng có thể chỉ định nhiều máy chủ DNS. Phân cách chúng với khoảng trắng, ví dụ:

```
--dns 8.8.8.8 --dns 192.168.1.1
```

**Restart the Docker daemon**
```
sudo service docker restart
```

Hoặc nhanh gọn hơn thì vô hiệu hóa ```dnsmasq``` trong NetworkManager (điều này có thể làm chậm mạng của bạn).

> sudo vim /etc/NetworkManager/NetworkManager.conf

Comment out the dns=dnsmasq line:
```
dns=dnsmasq
```
Sau đó save and exit:

> sudo restart network-manager

> sudo restart docker

#3. Configure Docker to start on boot

Với ubuntu 15.04 trở lên:
> sudo systemctl enable docker

#4. Upgrade Docker
> sudo apt-get upgrade docker-engine

#5. Uninstallation
uninstall the Docker pagkage:
> sudo apt-get purge docker-engine

Để gỡ bỏ cài đặt các gói Docker và các gói phụ thuộc mà không còn cần thiết:
> sudo apt-get autoremove --purge docker-engine

Để xóa hết images, containers, and volumes:
> rm -rf /var/lib/docker

**You must delete the user created configuration files manually.**




DOCKER_OPTS="-D --tls=true --tlscert=/var/docker/server.pem --tlskey=/var/docker/serverkey.pem -H tcp://45.124.93.110:80"

when cannot connect to daemon:
> sudo nohup docker daemon -H tcp://0.0.0.0:2375 -H unix:///var/run/docker.sock &
