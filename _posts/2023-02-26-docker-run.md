---
title: Docker 이미지 실행 및 삭제하기
layout: post
category: Docker
---

출처: 본 강의는 [생활코딩 도커편](http://opentutorials.org/course/128/8657/)을 참고하여 작성하였습니다. 



## 도커 이미지 실행 및 삭제



다운로드 받은 Docker 이미지를 컨테이너로 실행하기



### 1. Docker 이미지를 컨테이너로 실행

```shell
$ docker run httpd
```



### 2. 생성한 도커 확인

```shell
$ docker ps
```

```shell
user@DESKTOP-PPEIC48:~$ docker ps
CONTAINER ID   IMAGE     COMMAND              CREATED         STATUS         PORTS     NAMES
f02c66106331   httpd     "httpd-foreground"   4 minutes ago   Up 4 minutes   80/tcp    admiring_herschel
```



### 3. 추가 컨테이너 실행하기

```shell
$ docker run --name ws2 httpd
```

```shell
$ docker ps

CONTAINER ID   IMAGE     COMMAND              CREATED          STATUS          PORTS     NAMES
b20a5bc2ed41   httpd     "httpd-foreground"   18 seconds ago   Up 17 seconds   80/tcp    ws2
f02c66106331   httpd     "httpd-foreground"   6 minutes ago    Up 6 minutes    80/tcp    admiring_herschel
```



### 4. 실행중인 컨테이터 멈추기

실행중인 컨테이너를 멈춘다고 해서 컨테이너가 사라지지 않는다. start를 통해 재 시작할 수 있다. 

```shell
$ docker stop ws2
$ docker ps -s  ## 전체 도커 리스트 확인 (꺼진것도 보여준다.)
$ docker start ws2 ## 재실행
```



### 5. docker 로그 확인

실행되고 있는 도커의 로그 확인하기

```shell
$ docker logs ws2
```

실시간으로 확인하는 방법

```shell
$ docker logs -f ws2
```



### 6. 컨테이너 삭제하기

실행중인 컨테이너를 멈추고 삭제해야 한다.

```shell
$ docker stop ws2
$ docker rm ws2
$ docker ps -a # 삭제되었는지 컨테이너 리스트 확인
```



### 7. 도커 이미지 삭제하기 

만들어진 컨테이너를 모두 삭제한 후에 이미지를 삭제한다. 

```shell
$ docker rmi httpd
```

다음 명령어를 통해 httpd를 이용해 만들어진 컨테이너가 있는 확인하고 있으면 docker rm 명령을 통해 지운다. 

```shell
$ docker ps -a | grep httpd
```

