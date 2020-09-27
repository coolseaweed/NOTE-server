# Docker 정리 노트
  [1. Docker 설치](#1.-Docker-설치)

  [2. Commands](#2.-Commands)
  
  [3. 단축키](#3.-단축키)

  [9. References](#9.-References)

## 1. Docker 설치 <a name="1.-Docker-설치"></a>



---
## 2. Commands <a name="2.-Commands"></a>

  ```bash
  $ docker run -it -p [local_port]:[container_port] -v [local_dir]:[container_dir] --name [container_name] [docker_image] # 실행
  $ docker commit [container_name] [image_name] # 도커 이미지 
  $ docker images # 도커 이미지 리스트
  $ docker rmi # 도커 이미지삭제
  $ docker ps # 도커 컨테이너 리스트
  $ docker start [container] # 
  $ docker save -o <tar_file> <image_name> # docker_image --> .tar
  $ docker load -i <tar_file> # docker_image.tar -> docker_image
  $ docker exec -it <container> bash #  실행중인 컨테이너 접속
  $ docker build -i <imagenae:ver> . # dockefile build
  ```


---


## 3. 단축키 <a name="3.-단축키"></a>
  * ctrl + p + q (background로 전환)


---

## 9. References <a name="9.-References"></a>
  [Link01](https://www.44bits.io/ko/post/almost-perfect-development-environment-with-docker-and-docker-compose#%EA%B0%9C%EB%B0%9C%EC%9A%A9-dockerfile%EC%9D%84-%EB%B3%84%EB%8F%84%EB%A1%9C-%EA%B4%80%EB%A6%AC%ED%95%98%EA%B8%B0)

---





