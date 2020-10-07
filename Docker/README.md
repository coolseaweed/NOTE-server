# Docker 정리 노트
  
  Ubuntu 18.04 LTS 

  [1. Docker 설치](#1.-Docker-설치)
  
  [2. nvidia-docker 설치](#1.-nvidia-docker-설치)

  [3. Commands](#2.-Commands)
  
  [4. 단축키](#3.-단축키)

  [9. References](#9.-References)

## 1. Docker 설치 <a name="1.-Docker-설치"></a>
  ### Setup the repository
  ```
  $ sudo apt-get update

  $ sudo apt-get install apt-transport-https ca-certificates curl gnupg-agent software-properties-common
  $ curl -fsSL https://download.docker.com/linux/ubuntu/gpg | sudo apt-key add -
  $ sudo apt-key fingerprint 0EBFCD88
    pub   rsa4096 2017-02-22 [SCEA]
          9DC8 5822 9FC7 DD38 854A  E2D8 8D81 803C 0EBF CD88
    uid           [ unknown] Docker Release (CE deb) <docker@docker.com>
    sub   rsa4096 2017-02-22 [S]
    
  $ sudo add-apt-repository "deb [arch=amd64] https://download.docker.com/linux/ubuntu $(lsb_release -cs) stable"
  ```
  ### Install docker engine
  ```
  $ apt-cache madison docker-ce
    docker-ce | 5:18.09.1~3-0~ubuntu-xenial | https://download.docker.com/linux/ubuntu  xenial/stable amd64 Packages
    docker-ce | 5:18.09.0~3-0~ubuntu-xenial | https://download.docker.com/linux/ubuntu  xenial/stable amd64 Packages
    docker-ce | 18.06.1~ce~3-0~ubuntu       | https://download.docker.com/linux/ubuntu  xenial/stable amd64 Packages
    docker-ce | 18.06.0~ce~3-0~ubuntu       | https://download.docker.com/linux/ubuntu  xenial/stable amd64 Packages
    ...
  
  $ sudo apt-get install docker-ce=<VERSION_STRING> docker-ce-cli=<VERSION_STRING> containerd.io
  $ sudo docker run hello-world
  ```
  
  ### add sudo group docker
  ```
  $ sudo groupadd docker
  $ sudo usermod -aG docker ${USER}
  $ logout
  $ docker run hello-world
  ```
  
  ### ** Trouble shooting
  ```bash
  $ sudo apt-get purge docker-ce docker-ce-cli containerd.io
  $ sudo rm -rf /var/lib/docker
  ```
  
  
  ### ** Reference
  [Link01](https://docs.docker.com/engine/install/ubuntu/)
  
  
  
---

## 2. nvidia-docker 설치 <a name="2.-nvidia-docker-설치"></a>
  ### Remove nvidia-docker 1.0 dependency
  ```
  $ docker volume ls -q -f driver=nvidia-docker | xargs -r -I{} -n1 docker ps -q -a -f volume={} | xargs -r docker rm -f

  $ sudo apt-get purge nvidia-docker
  ```
  
  ### Installation
  ```
  $ distribution=$(. /etc/os-release;echo $ID$VERSION_ID)
  $ curl -s -L https://nvidia.github.io/nvidia-docker/gpgkey | sudo apt-key add -
  $ curl -s -L https://nvidia.github.io/nvidia-docker/$distribution/nvidia-docker.list | sudo tee /etc/apt/sources.list.d/nvidia-docker.list
  $ sudo apt-get update

  $ sudo apt-get install -y nvidia-docker2
  $ sudo systemctl restart docker
  $ sudo docker run --rm --runtime=nvidia nvidia/cuda:11.0-base nvidia-smi # test
  ```
  

  

---

## 2. Commands <a name="2.-Commands"></a>

  ```bash
  $ docker run -it -p [local_port]:[container_port] -v [local_dir]:[container_dir] --name [container_name] [docker_image] # 실행
  # nvidia tookit 사용시 (docker ver <= 19.3) 
  $ docker run --runtime=nvidia -it -p [local_port]:[container_port] -v [local_dir]:[container_dir] --name [container_name] [docker_image] # 실행
  $ docker commit [container_name] [image_name] # 도커 이미지 
  $ docker images # 도커 이미지 리스트
  $ docker rmi # 도커 이미지삭제
  $ docker ps # 도커 컨테이너 리스트
  $ docker start [container] # 
  $ docker save -o <tar_file> <image_name> # docker_image --> .tar
  $ docker load -i <tar_file> # docker_image.tar -> docker_image
  $ docker exec -it <container> bash #  실행중인 컨테이너 접속
  $ docker build --tag <imagenae:ver> . # dockefile build
  
  
  $ docker run --runtime=nvidia -it -p 5900:5900 -v ~/workspace:/workspace --name edges2portrait tom_workspace:base
  ```
---


## 3. 단축키 <a name="3.-단축키"></a>
  * ctrl + p + q (background로 전환)


---

## 9. References <a name="9.-References"></a>
  [Link01](https://www.44bits.io/ko/post/almost-perfect-development-environment-with-docker-and-docker-compose#%EA%B0%9C%EB%B0%9C%EC%9A%A9-dockerfile%EC%9D%84-%EB%B3%84%EB%8F%84%EB%A1%9C-%EA%B4%80%EB%A6%AC%ED%95%98%EA%B8%B0)

---





