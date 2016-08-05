apt-get install apt-transport-https ca-certificates
  461  apt-get autoremove 
  462  apt-get install apt-transport-https ca-certificates
  463  apt-get update 
  464  apt-get install apt-transport-https ca-certificates
  465  curl -sSL https://get.docker.com/ubuntu/ | sudo sh
  466  apt-key adv --keyserver hkp://p80.pool.sks-keyservers.net:80 --recv-keys 58118E89F3A912897C070ADBF76221572C52609D
  467  ls /etc/apt/sources.list.d/
  468  vim /etc/apt/sources.list.d/docker.list
  469  sudo apt-get update 
  470  cat /etc/apt/sources.list.d/docker.list 
  471  apt-cache policy docker-engine
  472  apt-get upgrade -y
