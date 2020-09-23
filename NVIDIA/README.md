
# NVIDIA driver + CUDA + cudnn 설치 가이드
   [1. nvidia driver 설치](#1.-nvidia-driver-설치)

   [2. CUDA 설치](#2.-CUDA-설치)

   [3. cuDNN 설치](#3.-cuDNN-설치)


## 1. nvidia driver 설치 <a name="1.-nvidia-driver-설치"></a>

  ### GPU info 확인
  ```
  $ sudo lshw -C display # 그래픽카드 정보 확인
  $ ubuntu-drivers devices # 추천 드라이버 확인
  ```
  ### Ubuntu 16.04 LTS 
  나중에 깔게 되면 찾아서 넣음
  
  
  

  ### Ubuntu 18.04 LTS 
  ```shell
  $ sudo add-apt-repository ppa:graphics-drivers/ppa # repository 추가
  $ sudo apt update
  $ apt-cache search nvidia | grep nvidia-driver-{recommand_version}
  $ sudo apt-get install nvidia-driver-{recommand_version}
  $ sudo shutdown -r now
  $ nvidia-smi # 설치확인
  ```

  ### ** Trouble shooting
  기존에 설치된 프로그램과 충돌시 모두 삭제후 다시 설치
  ```
  $ sudo apt --purge autoremove nvidia*
  ```
  
---

## 2. CUDA 설치 <a name="2.-CUDA-설치"></a>
  ### CUDA runfile 다운로드
  <img src="/img/cuda_install.JPG">
  
  * [CUDA Toolkit 10.2](https://developer.nvidia.com/cuda-downloads) (Nov 2019), [Install Guide](https://docs.nvidia.com/cuda/archive/10.2/)
  * [CUDA Toolkit 10.1 update2](https://developer.nvidia.com/cuda-10.1-download-archive-update2) (Aug 2019), [Install Guide](https://docs.nvidia.com/cuda/archive/10.1/)
  * [CUDA Toolkit 10.1 update1](https://developer.nvidia.com/cuda-10.1-download-archive-update1) (May 2019), [Install Guide](https://docs.nvidia.com/cuda/archive/10.1/)
  * [CUDA Toolkit 10.1](https://developer.nvidia.com/cuda-10.1-download-archive-base) (Feb 2019), [Install Guide](https://docs.nvidia.com/cuda/archive/10.1/)
  * [CUDA Toolkit 10.0](https://developer.nvidia.com/cuda-10.0-download-archive) (Sept 2018), [Install Guide](https://docs.nvidia.com/cuda/archive/10.0/)
  * [CUDA Toolkit 9.2](https://developer.nvidia.com/cuda-92-download-archive) (May 2018), [Install Guide](https://docs.nvidia.com/cuda/archive/9.2/)
  * [CUDA Toolkit 9.1](https://developer.nvidia.com/cuda-91-download-archive-new) (Dec 2017), [Install Guide](https://docs.nvidia.com/cuda/archive/9.1/)
  * [CUDA Toolkit 9.0](https://developer.nvidia.com/cuda-90-download-archive) (Sept 2017), [Install Guide](https://docs.nvidia.com/cuda/archive/9.0/)

<!--<img src="/img/cuda_install.JPG"  width="700" height="370">-->
  ### CUDA 설치
  ```
  $ sudo sh cuda_10.0.130_410.48_linux.run
  
  <--- 옵션 설정 --->
  accept/decline/quit: accept

  Install NVIDIA Accelerated Graphics Driver // 위에서 설치했으므로 n
  (y)es/(n)o/(q)uit: n

  Install the CUDA 10.0 Toolkit? 
  (y)es/(n)o/(q)uit: y

  Enter Toolkit Location  [ default is /usr/local/cuda-10.0 ]: // 엔터 치면 default로 자동설정 (recommand)

  Do you want to install a symbolic link at /usr/local/cuda?

  (y)es/(n)o/(q)uit: y

  Install the CUDA 10.0 Samples? // sample code 필요하면 y

  (y)es/(n)o/(q)uit: n

  ```
  ### CUDA path 추가

  ```
  export PATH=/usr/local/cuda-10.0/bin${PATH:+:${PATH}} 
  export LD_LIBRARY_PATH=/usr/local/cuda-10.0/lib64\${LD_LIBRARY_PATH:+:${LD_LIBRARY_PATH}}
  $ nvcc --version # 설치 확인
  ```
  
  ### **Trouble shooting
  기존에 설치된 cuda 폴더 삭제 후 다시 시도
  ```
  $ sudo rm -rf /usr/local/cuda-10.0
  $ sudo rm -rf /usr/local/cuda
  ```

---

## 3. cuDNN 설치 <a name="3.-cuDNN-설치"></a>
  ### CUDA 버전에 맞는 cuDNN 라이브러리 다운로드
  [cuDNN archive](https://developer.nvidia.com/rdp/cudnn-archive)

  [ ! ] tensorflow의 경우 버전마다 cuDNN 버전이 다르니 확인!

   ### ** Trouble shooting
   cuDNN Library for Linux의 파일을 window로 받을 경우 확장자명이 *.solitairetheme8 으로 변경 될 수 있다
   *.solitairetheme8 --> *.tgz 로 확장자명을 변경 후 진행
  


