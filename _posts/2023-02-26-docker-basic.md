---
title: Docker Hub에서 이미지 가져오기
layout: post
category: Docker
---

## Docker Pull



Docker를 기본적으로 사용해보자



### 1. 도커 이미지 다운로드

* [dockerhub](http://hub.docker.com) 접속
* httpd 검색 및 다운로드

![image-20230226164546634](/public/img/image-20230226164546634.png)

```shell
$ docker pull httpd
```

 

### 2. 이미지 다운로드 확인

```shell
$ docker images
```

```shell
REPOSITORY    TAG       IMAGE ID       CREATED         SIZE
httpd         latest    3a4ea134cf8e   2 weeks ago     145MB
hello-world   latest    feb5d9fea6a5   17 months ago   13.3kB
user@DESKTOP-PPEIC48:~$
```

