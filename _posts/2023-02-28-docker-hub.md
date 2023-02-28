---
title: Docker Hub
layout: post
category: Docker
---

본 문서는 [생활코딩 Docker hub로 이미지 공유하기](https://help.iwinv.kr/manual/read.html?idx=583)를 참고하여 만들었습니다.

## Docker Hub

일반적으로 파일을 만들어서 공유할때는 google drive에 올려서 공유하고 소스코드를 공유할때는 github에 올려서 공유한다. 마찬가지로 도커 이미지도 다른 사람과 공유할때는 [dockerhub](http://hub.docker.com)을 이용해서 공유하면 된다. 먼저 Repository를 아래와 같이 생성한다. 

![image-20230228202045707](\public\img\image-20230228202045707.png)

### create

create 버튼을 누르면 아래와 같은 결과가 나온다. 

![image-20230228202646956](\public\img\image-20230228202646956.png)

### ubuntu 컨테이너 실행  및 파이썬 설치

python 설치시에 옵션을 물어보면 -y 옵션을 줘서 설치 중단이 되지 않도록 한다.

```shell
$ docker run -it --name my-python ubuntu
# 컨테이너 쉘 진입 후
# apt update && apt install -y python3 
```



### 도커 이미지 만들기

docker 밖에서 현재 컨테이너 확인한 다음에 해당 컨테이너를 

```shell
$ docker ps
CONTAINER ID   IMAGE     COMMAND       CREATED         STATUS         PORTS     NAMES
a2c602074a37   ubuntu    "/bin/bash"   3 minutes ago   Up 3 minutes             my-

$ docker commit my-python deeplog/python3:1.0
sha256:dcef7d99508511b263d7c4e9350e752a948e70b07387d235d1ba8ebe7d207f27

$ docker images
REPOSITORY          TAG       IMAGE ID       CREATED          SIZE
deeplog/python3     1.0       dcef7d995085   10 seconds ago   149MB
```

### Dockerhub로 업로드

```shell
$ docker login

$ docker push deeplog/python3:1.0
```



### Dockerhub에서 확인

아래와 같이 dockerhub에서 새로 올라온 이미지가 있는지 확인한다. 

![image-20230228205010194](\public\img\image-20230228205010194.png)



### 업로드 제대로 되었는지 확인

만들어 놓은 이미지를 지우고 pull로 받아본다. docker images로 확인하면 내가 만든 이미지가 잘 download 되었는지 확인할 수 있다. 

```shell
$ docker rmi --force deeplog/python3:1.0
$ docker pull deeplog/python3:1.0

$ docker images
REPOSITORY        TAG       IMAGE ID       CREATED         SIZE
deeplog/python3   1.0       5f8b46e029c9   7 minutes ago   149MB
```



