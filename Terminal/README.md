# 자주쓰는 터미널 명령어 정리


  [1. screen](#1.-screen)

  [2. File search](#2.-File-search)
  
  [3. archive & compress](#3.-archive-&-compress)

  [4. Permission](#4.-Permission)
  
  [5. File transfer](#5.-File-transfer)

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

  ```bash
  find . -name "*.lst"
  ```

---

## 3. archive & compress <a name="3.-archive-&-compress"></a>
보통 Linux환경에서는 파일들을 묶고(archive)난 후 압축(compress)하는 방식(.tar.gz)이 많이 사용된다

압축 확장자: .tar (**t**ape **ar**chives), .tgz(=tar.gz), bz2

압축률: tar << tgz(**recommand**) < bz2

  ### tar
  |Option|Function|
  |:----|:----|
  |-x|압축 파일 풀기 (create)|
  |-c|압축 파일 생성 (extract / get)|
  |-z|gzip 방식 사용 (gzip / gunzip / ungzip)|
  |-j|bzup2 방식 사용 (bzip2)|
  |-p|권한(permission)을 원봔과 동일하게 유지|
  |-v|묶음/해제 과정을 화면에 표시 (verbose)|
  |-f|파일 이름을 지정 (file)|
  |--exclude|특정 폴더나 파일을 제외할때 사용 (리스트로 가능)|

  ```bash
  tar -czvf <target filename> <src file/dir> # 압축1
  tar -czvf <target filename> <src file/dir> --exclude <except file/dir1> # 압축2
  tar -xvzf <src archive> # 압축 해제  
  ```

  ### gz(gzip/gunzip)
  
  |Option|Function|
  |:----|:----|
  |-n|n은 1부터 9사이의 숫자를 지정 (숫자가 낮을수록 빠른 압축)|
  |-c|압축 결과를 출력하고, 원본 파일은 그대로 둔다|
  |-d|압축 해제 옵션 (gunzip과 같음)|
  |-f|강제 압축|
  |-l|압축 파일의 정보 출력|
  |-r|디렉토리를 지정 시 디렉토리에 포함된 모든 파일 압축|
  |-t|압축 파일 테스트|
  |-v|자세한 정보 출력|
  |-h|도움말 출력|
  |-V|버전 정보 출력|

  ```bash
  gzip <target filename> <src file/dir> #압축
  gunzip <src archive> # 압축 해제
  ```

  ### ** Reference
  
  [Link](https://ifuwanna.tistory.com/31)

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
## 5. File transfer <a name="5.-File-transfer"></a>

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

