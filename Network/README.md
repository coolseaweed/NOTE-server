# Network 커맨드 정리 노트

   [1. SSH](#1.-SSH)
   
   [2. SCP](#2.-SCP)

   [3. Bonding](#3.-Bonding)



## 1. SSH <a name="1.-SSH"></a>
   ### 서버 접속
   ```bash
   $ ssh -p [port_num] [username]@[host_address]
   
   # 사용예제 (default port: 22)
   $ ssh -p 5000 coolseaweed@192.168.100.1
   ```

   ### Tunneling
   ```bash
   $ ssh -L [local_port]:localhost:[server_port] [username]@[host_address] -p [portnum]
   
   # 사용예제 (local machine의 1234 port와 server의 7777 port 연결/ 5000번은 port forwarding )
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

## 2. SCP <a name="2.-SCP"></a>

   ### 기본
   ```bash
   $ scp -P [port_num] [username]@[host_address]:<src_path> <dest_path>
   
   # 사용예제 (server wavfile local에서 재생)
   $ scp -P 5000 coolseaweed@192.168.100.1:~/temp.wav /dev/stdout | play /dev/stdin 
   ```

  
  
  
  
  
