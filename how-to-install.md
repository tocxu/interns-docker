#1. Prepare

**step 1.1 Kiểm tra trước khi cài đăt: **

(để chắc chắn *APT* làm việc được với *https method* và các chứng chỉ *CA* đã được cài đặt)
> apt-get install apt-transport-https ca-certificates

**step 1.2 add *GPG* key:**

> apt-key adv --keyserver hkp://p80.pool.sks-keyservers.net:80 --recv-keys 58118E89F3A912897C070ADBF76221572C52609D

**step 1.3:**

> vim /etc/apt/sources.list.d/docker.list

(tạo file docker.list nếu chưa có)
 Sau đó thêm 1 entry như sau (chọn theo ver ubuntu của bạn):
```
 The possible entries are:

    On Ubuntu Precise 12.04 (LTS)

  >  deb https://apt.dockerproject.org/repo ubuntu-precise main

    On Ubuntu Trusty 14.04 (LTS)

  >  deb https://apt.dockerproject.org/repo ubuntu-trusty main

    Ubuntu Wily 15.10

  >  deb https://apt.dockerproject.org/repo ubuntu-wily main

    Ubuntu Xenial 16.04 (LTS)

  >  deb https://apt.dockerproject.org/repo ubuntu-xenial main
```

**step 1.4  update APT package index:**

> apt-get update

Xóa repo cũ (nếu có)

> apt-get purge lxc-docker

**step 1.5 Verify that APT is pulling from the right:** repository

> apt-cache policy docker-engine

Có thể chạy thêm lệnh:

> apt-get upgrade

**Install the recommended package**

> apt-get install linux-image-extra-$(uname -r)

**step 1.6 Install Docker:**

> apt-get install docker-engine
> apt-get install -y docker-engine

**step 1.7 check that it's running:**

> systemctl status docker
<src ='http://imgur.com/a/b3MpD'>

#2. Using the Docker Command

Xem tất cả các câu lệnh có trong *docker*:

>  docker

Xem thông tin về Docker:

> docker info

#3. Docker Images

Để kiểm tra liệu rằng bạn có thể truy cập và download images từ Docker Hub hay không:

> docker run hello-world

Bạn cũng có thể tìm images có tồn tại trên Docker Hub hay không:

> docker search ubuntu

Để kéo (tải) nó:

> docker pull ubuntu

run image:

> docker run ubuntu

xem các images đã được download về máy:

> docker images

#4. Running a Docker Container

> docker run -it ubuntu

![alt tag](http://imgur.com/a/fhohe)

<img src="http://i.imgur.com/gsMJTo5.png"/>
