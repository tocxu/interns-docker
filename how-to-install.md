#1. Prepare

**step 1.1 Kiểm tra trước khi cài đăt:**

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

#2.Install Docker

> apt-get install docker-engine
> apt-get install -y docker-engine

**check that it's running:**

> systemctl status docker
<src ='http://imgur.com/a/b3MpD'>

#3. Using the Docker Command

Xem tất cả các câu lệnh có trong *docker*:

>  docker

Xem thông tin về Docker:

> docker info

#4. Docker Images

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

#5. Running a Docker Container

> docker run -it ubuntu

<img src="http://i.imgur.com/gsMJTo5.png"/>

**2119b163b5a2** tại dấu nhắc lệnh là Id của container

Bây giờ bạn có thể chạy lệnh bất kỳ bên trong container. Ví dụ, chúng ta hãy cập nhật cơ sở dữ liệu gói bên trong container. Không cần phải thêm tiền tố **sudo**, bởi vì bạn đang hoạt động bên trong container với quyền root:
> apt-get update

cài đặt bất kỳ app nào bạn muốn. Ví dụ cài NodeJS:

> apt-get install -y nodejs

**Enable UFW forwarding**

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




#6. Committing Changes in a Container to a Docker Image
Bắt đầu với một Docker image, bạn có thể tạo, chỉnh sửa, và xóa các tập tin giống như một máy ảo. Nhưng tất cả hệ thống và thay đổi đó đều là tạm thời và sẽ mất đi nếu bạn chạy lại nó lần tiếp theo.

Để giữ lại những thay đổi trong container khi khởi động lại của container cần phải sử dụng [Docker Data Volumes]().

Trong phần này trình bày cách làm thế nào để lưu lại trạng thái của một container như một image Docker mới.

**To Save**

> exit

> docker commit -m "What did you do to the image" -a "Author Name" container-id repository/new_image_name

Ví dụ:

> docker commit -m "added node.js" -a "I'm Tocxu" 2119b163b5a2 finid/ubuntu-nodejs

<img src="http://i.imgur.com/L2FR3FX.png"/>
