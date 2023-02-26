---
title: 윈도우즈용 Linux에 Docker 설치
layout: post
category: Docker
---

## 윈도우즈용 ubuntu에 도커 설치



윈도우즈용 리눅스(Windows subsystem for linux)에 도커를 설치하는 방법을 정리한다. 윈도우즈용 리눅스를 설치하는 방법은 [윈도우즈11에서 리눅스 설치](./docker-setup.md) 를 참고하라. 

### 1. 윈도우즈 Ubuntu 버전 확인

```shell
c:\users\user>wsl -l -v

  NAME            STATE           VERSION
* Ubuntu-22.04    Running         2
```



### 2. Ubuntu에서 도커 설치

https://docs.docker.com/engine/install/ubuntu/  를 참고해서 설치한다.

#### 레포티토리 셋업

1. apt-get 업데이트 및 패키지 설치

   ```shell
   $ sudo apt-get update
   $ sudo apt-get install \
       ca-certificates \
       curl \
       gnupg \
       lsb-release
   ```

2. Docker GPG key 추가

   ```shell
   $ sudo mkdir -m 0755 -p /etc/apt/keyrings
   $ curl -fsSL https://download.docker.com/linux/ubuntu/gpg | sudo gpg --dearmor -o /etc/apt/keyrings/docker.gpg
   ```

3. 레포지토리 셋업

   ```shell
   $ echo \
     "deb [arch=$(dpkg --print-architecture) signed-by=/etc/apt/keyrings/docker.gpg] https://download.docker.com/linux/ubuntu \
     $(lsb_release -cs) stable" | sudo tee /etc/apt/sources.list.d/docker.list > /dev/null
   ```

#### 도커 엔진 설치

```shell
$ sudo apt-get update
$ sudo apt-get install docker-ce docker-ce-cli containerd.io 
$ sudo apt-get install docker-buildx-plugin docker-compose-plugin
```



### 3. IPTables 셋팅

 https://netmarble.engineering/docker-on-wsl2-without-docker-desktop/ 참고해서 iptables를 셋팅한다. 

*  우분투 버전이 22.04 버전부터 ‘iptables-nft’가 기본 설정으로 잡혀있어서, WSL에서 도커를 사용할 때 호환성 이슈가 발생한다.    

*  ‘iptables-nft’ 대신 ‘iptables-legacy’를 사용해야 도커 데몬 실행 가능

  ```shell
  $ sudo update-alternatives --config iptables
  
  There are 2 choices for the alternative iptables (providing /usr/sbin/iptables).
  
    Selection    Path                       Priority   Status
  ------------------------------------------------------------
  * 0            /usr/sbin/iptables-nft      20        auto mode
    1            /usr/sbin/iptables-legacy   10        manual mode
    2            /usr/sbin/iptables-nft      20        manual mode
  
  Press <enter> to keep the current choice[*], or type selection number: 1
  
  update-alternatives: using /usr/sbin/iptables-legacy to provide /usr/sbin/iptables (iptables) in manual mode
  ```

   

### 4. 도커 데몬 실행

 https://help.iwinv.kr/manual/read.html?idx=583 참고해서 Docker 데몬 실행

```shell
$ sudo service docker start 
```



### 5. docker 설치 확인

1. docker ps 로 확인하기

   ```shell
   $ docker ps
   CONTAINER ID   IMAGE     COMMAND   CREATED   STATUS    PORTS     NAMES
   ```

2. hello-world로 확인하기

   ```shell
   $ sudo docker run hello-world
   ```

   ```shell
   Hello from Docker!
   This message shows that your installation appears to be working correctly.
   
   To generate this message, Docker took the following steps:
    1. The Docker client contacted the Docker daemon.
    2. The Docker daemon pulled the "hello-world" image from the Docker Hub.
       (amd64)
    3. The Docker daemon created a new container from that image which runs the
       executable that produces the output you are currently reading.
    4. The Docker daemon streamed that output to the Docker client, which sent it
       to your terminal.
   ```

   
