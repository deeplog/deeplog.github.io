---
title: Docker 및 Container 삭제
layout: post
category: Docker
---

## 도커 이미지 실행 및 삭제



### 컨테이너 삭제하기

실행중인 컨테이너를 멈추고 삭제해야 한다.

```shell
$ docker stop ws2
$ docker rm ws2
$ docker ps -a # 삭제되었는지 컨테이너 리스트 확인
```



###  도커 이미지 삭제하기 

만들어진 컨테이너를 모두 삭제한 후에 이미지를 삭제한다. 

```shell
$ docker rmi httpd
```

