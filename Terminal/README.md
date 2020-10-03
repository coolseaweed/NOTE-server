# 자주쓰는 터미널 명령어 정리


  [1. screen](#1.-screen)

  [2. find](#2.-find)
  
  [3. ](#3.-)

  [4. authority](#4.-authority)
  
  [5. scp](#5.-scp)

  [6. I/O](#6.-I/O)

## 1. screen <a name="1.-screen"></a>

  |Commands|Function|
  |:----|:----|
  |screen -S [name]|[name] 으로 screen 생성|
  |screen -ls|현재 생성된 screen list |
  |screen -r [name]|deatach 되어 있는 screen attach|
  |screen -X -S [name] kill|[name]screen 삭제|
  |screen -r d|sreen 강제로 detach|
  |Ctrl+a+d|screen deatch 단축키|


---

## 2. find <a name="2.-find"></a>

  ```
  $ find . -name "*.lst"
  ```

---

## 3. dd <a name="2.-dd"></a>
> File read write 속도 측정에 사용되는 커맨드


---
## 4. authority <a name="4.-authority"></a>
  ```
  # owner change
  $ chown <new-owner>  [filename]

  # owner change
  $ chgrp <group> [filename]

  ```
---
## 5. scp <a name="5.-scp"></a>

  ### 기본
  ```bash
  $ scp -P [port_num] [username]@[host_address]:<src_path> <dest_path>

  # 사용예제 (server wavfile local에서 재생)
  $ scp -P 5000 coolseaweed@192.168.100.1:~/temp.wav /dev/stdout | play /dev/stdin 
  ```
  ### rsync
  ```
  $ sudo rsync -av -e 'ssh -p [Port num]' --delete [source_dir] [user@host]:[dest_dir]
  ```

---
## 6. I/O <a name="6.-I/O"></a>

  ### I/O monitoring
  ```bash
  # iotop
  $ iotop -oPa # 누적 I/O 량 측정
  $ iotop -o # output 만을 

  # iostat
  $ iostat -dx 5

  # atop
  $ atop

  ```

  ### I/O speed check
  ```bash
  $ sudo dd if=/dev/zero of=<filename>  bs=1M count=1024 oflag=direct

  # examples 
  $ sudo dd if=/dev/zero of=/test/bb  bs=1M count=1024 oflag=direct # local domain
  $ sudo dd if=/dev/zero of=/mnt/data/bb  bs=1M count=1024 oflag=direct # mount domain
  ```
  [ ! ] /test/bb 에 실제 용량이 써지므로 테스트 후 삭제

---

