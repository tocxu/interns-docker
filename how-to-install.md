#1. Prepare

**step 1.1:** Đảm bảo trước khi cài đăt:

(đẻ chắc chắn APT làm việc được với https method và các chứng chỉ CA đã được cài đặt)
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

> apt-get autoremove

**step 1.2:**

> apt-get install apt-transport-https ca-certificates
> apt-get update
> apt-get install apt-transport-https ca-certificates
> curl -sSL https://get.docker.com/ubuntu/ | sudo sh
> apt-key adv --keyserver hkp://p80.pool.sks-keyservers.net:80 --recv-keys 58118E89F3A912897C070ADBF76221572C52609D
> ls /etc/apt/sources.list.d/

> sudo apt-get update
> cat /etc/apt/sources.list.d/docker.list
> apt-cache policy docker-engine
> apt-get upgrade -y
