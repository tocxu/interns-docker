#1. Prepare

**step 1.1:** Đảm bảo trước khi cài đăt:

(để chắc chắn APT làm việc được với https method và các chứng chỉ CA đã được cài đặt)
> apt-get install apt-transport-https ca-certificates

**step 1.2:** add *GPG* key.

> apt-key adv --keyserver hkp://p80.pool.sks-keyservers.net:80 --recv-keys 58118E89F3A912897C070ADBF76221572C52609D

**step 1.3:**

> vim /etc/apt/sources.list.d/docker.list

(if docker.list doesn't exist, create it)
 add an entry/edit:
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

**step 1.4:** update APT package index

> apt-get update

purge the old repo if it exists

> apt-get purge lxc-docker

Verify that APT is pulling from the right repository

> apt-cache policy docker-engine

after all

> apt-get upgrade

#1.2: To install the linux-image-extra package

**Install the recommended package**

> apt-get install linux-image-extra-$(uname -r)

#Start Install Docker

**Install Docker**

> apt-get install docker-engine
> apt-get install -y docker-engine

**check that it's running**

> systemctl status docker
<src ='http://imgur.com/a/b3MpD'>
