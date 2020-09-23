
# NVIDIA + CUDA + cudnn 설치 가이드



## 1. nvidia driver 설치 

  ### GPU info 확인
  ```
  $ sudo lshw -C display # 그래픽카드 정보 확인
  $ ubuntu-drivers devices # 추천 드라이버 확인
  ```
  ### Ubuntu 16.04 LTS 
  나중에 깔게 되면 찾아서 넣음
  
  
  

  ### Ubuntu 18.04 LTS 
  ```
  $ sudo add-apt-repository ppa:graphics-drivers/ppa # repository 추가
  $ sudo apt update
  $ apt-cache search nvidia | grep nvidia-driver-{recommand_version}
  $ sudo apt-get install nvidia-driver-{recommand_version}
  $ sudo shutdown -r now
  $ nvidia-smi # 설치확인
  ```

  ### **Trouble shooting
  기존에 설치된 프로그램과 충돌시 모두 삭제후 다시 설치
  ```
  $ sudo apt --purge autoremove nvidia*
  ```
---

## 2. CUDA 설치
  Release
  * [CUDA Toolkit 10.2](https://developer.nvidia.com/cuda-downloads) (Nov 2019), Versioned Online Documentation
  * CUDA Toolkit 10.1 update2 (Aug 2019), Versioned Online Documentation
  * CUDA Toolkit 10.1 update1 (May 2019), Versioned Online Documentation
  * CUDA Toolkit 10.1 (Feb 2019), Online Documentation
  * CUDA Toolkit 10.0 (Sept 2018), Online Documentation
  * CUDA Toolkit 9.2 (May 2018),Online Documentation
  * CUDA Toolkit 9.1 (Dec 2017), Online Documentation
  * CUDA Toolkit 9.0 (Sept 2017), Online Documentation


---
