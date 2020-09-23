# Network 커맨드 정리 노트
   [1. SSH authorization](#1.-SSH-authorization)

   [2. CUDA 설치](#2.-CUDA-설치)

   [3. cuDNN 설치](#3.-cuDNN-설치)


## 1. SSH authorization <a name="1.-SSH-authorization"></a>
>비밀번호 입력 없이 서버 접속 허가
  
  ### Client
  ```
  $ ssh-keygen # Enter 연타
  $ cat ~/.ssh/id_rsa.pub # 내용 복사
  ```
  ### Server
  ```
  $ mkdir ~/.ssh
  $ vi ~/.ssh/authorized_keys # client에서 복사한 id_rsa.pub 내용 붙여넣기
  ```

  
  
  
  
