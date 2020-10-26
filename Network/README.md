# Network 커맨드 정리 노트

   [1. ssh](#1.-SSH)
   
   [2. ](#2.-)

   [3. Bonding](#3.-Bonding)

   [4. iperf](#4.-iperf)

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
   
   ### Port forwarding
   ```bash
   echo "/usr/sbin/sshd -p <portnum>">> ~/.bashrc
   source ~/.bashrc
   ```
   
   
---

## 2. Network performance check <a name="2.-Network-performance-check"></a>
   ### iperf
   > To check bonding network speed 
   - Server
   ```bash
   $ iperf -s
   ```
   - Client
   ```bash
   $ iperf -c <host ip> -P <parallel num>
   ```
   
   ### speedtest-cli
   > To check upload & download speed
   ```bash
   $ speedtest-cli -h
   ```
   
---



## 3. Bonding <a name="3.-Bonding"></a>
   > 네트워크 interface의 bandwidth를 늘리기 
   ### Bonding driver/interface 확인
   ```bash
   # bonding kernel 확인
   $ sudo modprobe bonding
   $ lsmod | grep bond
   bonding        163840   0
   
   # LAN card 확인 (ex. enp4s0, enp6s0)
   $ ifconfig -a 
   
   # 옛날 버전 Debian/Ubuntu 일때
   $ sudo apt-get install ifenslave
   ```
   
   ### network interface 수정 
   ```bash
   $ sudo nano /etc/network/interfaces
   # This file describes the network interfaces available on your system
   # and how to activate them. For more information, see interfaces(5).

   source /etc/network/interfaces.d/*

   # The loopback network interface
   #auto lo
   #iface lo inet loopback

   # The primary network interface
   auto enp4s0 # LAN card 1
   iface enp5s0 inet manual
      bond-master bond0

   auto enp6s0 # LAN card 2
   iface enp6s0 inet manual
      bond-master bond0

   auto bond0
   iface bond0 inet static
      address 192.168.1.150 # machine ip address
      gateway 192.168.1.1
      netmask 255.255.255.0
      network 192.168.1.0
      broadcast 192.168.1.255
      dns-nameservers 8.8.8.8

      bond-mode 0
      bond-miimon 100
      bond-slaves none
   ```
   ### bond interface 활성화
   ```bash
   $ sudo shutdown -r now # best option
   or
   $ sudo ifdown enp4s0 && ifdown enp5s0 && ifup bond0
   or
   $ sudo systemctl restart networking.service
   $ sudo service networking restart
   $ ethtool bond0 # bonding check
  ```
  
   ### ** Reference
   [link](https://www.tecmint.com/configure-network-bonding-teaming-in-ubuntu/)

---


   ```

---



