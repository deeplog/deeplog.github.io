---
title: 08. Docker Commit
layout: post
category: Docker
---

출처: 본 문서는 [생활코딩 도커 이미지 만든 법 - commit](https://www.youtube.com/watch?v=RMNOQXs-f68)을 참고하여 작성하였습니다. 



## 도커 commit

나만의 도커 이미지를 만들고 싶을때, 도커 commit 을 이용한다. 다음과 같은 상황을 가정해서 도커 이미지를 만든다. 

* ubuntu 최신버전 도커이미지를 다운로드한다.
* git이 설치되어 있지 않으므로 git을 추가로 설치한다. 
* ubuntu-git 이라는 이름으로 deeplog 리포지토리에 commit 한다.
* 만들어진 도커 이미지 확인한다. 

### Ubuntu 도커 이미지 다운로드

``` shell
$ docker pull ubuntu  
```



### 컨테이너  실행

```shell
#bash 쉘을 입력할수 있도록 my-ubuntu란 이름으로 컨테이너 실행
$ docker run -it --name my-ubuntu ubuntu bash
```



### 컨테이너에 필요한 패키지 설치

```shell
#컨테이너 bash 쉘 안에서 실행
$ apt update
$ apt install git
```



### Docker 이미지 만들기

```shell
# 컨테이너 밖에서 실행
$ docker commit my-ubuntu deeplog:ubuntu-git
```



### Docker 이미지 확인

```shell
# docker 이미지 확인
$ docker images
----------------------------------
$ docker images
REPOSITORY      TAG          IMAGE ID       CREATED              SIZE
deeplog         ubuntu-git   533cbf9275a1   About a minute ago   195MB
```



