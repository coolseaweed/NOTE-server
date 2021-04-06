# 자주쓰는 터미널 명령어 정리

  [1. File transfer](#1.-File-transfer)

  [2. File search](#2.-File-search)


  [3. screen](#3.-screen)
  
  [3. archive & compress](#3.-archive-&-compress)

  [4. Permission](#4.-Permission)
  
  [6. I/O](#6.-I/O)

## 1. File transfer <a name="1.-File-transfer"></a>

  ### scp
  [Detail](https://twpower.github.io/138-send-file-using-scp-command)
  
  * Local --> Remote
    ```bash
    scp [option] <SRC> <host>@<IP address>:<DST>
    ```
  * Remote --> Local
    ```bash
    scp [port_num] <host>@<IP address>:<SRC> <DST>
    ```

  ### rsync
  [Detail](https://blueyikim.tistory.com/562)

  * Local --> Remote
    ```bash
    rsync [option] <SRC> <host>@<IP address>:<DST>
    ```
  * Remote --> Local
    ```bash
    rsync [option] <host>@<IP address>:<SRC> <DST>
    ```
  * CMD 모음
    ```bash
    sudo rsync -rltD --info=progress2 -u -e 'ssh [option]' <SRC> <host>@<ip_address>:<DST> > trans.log 2>&1
    sudo rsync -av -e 'ssh [option]' <host>@<ip_address>:<DST> <SRC> > trans.log 2>&1
    ```

---
## 2. File search <a name="2.-File-search"></a>

  ```bash
  find . -name "*.lst"
  ```

---

## 3. screen <a name="3.-screen"></a>

  |Commands|Function|
  |:----|:----|
  |screen -S [name]|[name] 으로 screen 생성|
  |screen -ls|현재 생성된 screen list |
  |screen -r [name]|deatach 되어 있는 screen attach|
  |screen -X -S [name] kill|[name]screen 삭제|
  |screen -rd [name]|sreen 재시작|
  |ctrl+a+d|screen deatch 단축키|
  |ctrl+a+shift+'|다른 screen session  선택|
  |ctrl+a+shift+a|screen session 이름 편집|



---


## 3. archive & compress <a name="3.-archive-&-compress"></a>

  [Detail](https://ifuwanna.tistory.com/31)
  
  ### tar
  ```bash
  tar -czvf <target filename> <src file/dir> # 압축1
  tar -czvf <target filename> <src file/dir> --exclude <except file/dir1> # 압축2
  tar -xvzf <src archive> # 압축 해제  
  ```

  ### gz(gzip/gunzip)
  ```bash
  gzip <target filename> <src file/dir> #압축
  gunzip <src archive> # 압축 해제
  ```


---
## 4. Permission <a name="4.-Permission"></a>
  ```bash
  # owner change
  chown [new-owner]  <filename>

  # owner change
  chgrp [group] <filename>
  
  # both
  chown <new_owner>:<group> <dir/filename>

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
  $ sudo dd if=/dev/zero of=[filename]  bs=1M count=1024 oflag=direct

  # examples 
  $ sudo dd if=/dev/zero of=/test/bb  bs=1M count=1024 oflag=direct # local domain
  $ sudo dd if=/dev/zero of=/mnt/data/bb  bs=1M count=1024 oflag=direct # mount domain
  ```
  **[ ! ] /test/bb 에 실제 용량이 써지므로 테스트 후 삭제**

---

