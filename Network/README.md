# Network 커맨드 정리 노트

   [1. SSH](#1.-SSH)

   [2. Bonding](#2.-Bonding)



## 1. SSH <a name="1.-SSH"></a>
   ### 서버 접속
   ```bash
   $ ssh -p [port_num] [username]@[host_address]
   ```

   ### Tunneling
   ```bash
   $ ssh -L [local_port]:localhost:[server_port] [username]@[host_address] -p [portnum]
   
   # 사용예제
   $ ssh -L 1234:localhost:7777 coolseaweed@192.168.100.1 -p 5000
   ```
   ### Authorization
   >비밀번호 입력 없이 서버 접속 허가

   * Client
   ```bash
   $ ssh-keygen # Enter 연타
   $ cat ~/.ssh/id_rsa.pub # 내용 복사
   ```
   * Server
   ```bash
   $ mkdir ~/.ssh
   $ vi ~/.ssh/authorized_keys # client에서 복사한 id_rsa.pub 내용 붙여넣기
   ```

  
  
  
  
