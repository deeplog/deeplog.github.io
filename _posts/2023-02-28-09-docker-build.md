---
title: 09. Docker Build
layout: post
category: Docker
---

출처: 본 문서는 [생활코딩 도커 이미지 만든 법 - Dockerfile & build](https://www.youtube.com/watch?v=0kQC19w0gTI)을 참고하여 작성하였습니다. 



## 도커 이미지 만들기

나만의 도커 이미지를 만들고 싶을때, 첫번째 방법은 도커 commit 을 이용하는 것이다. 또 하나의 방법은 Dockerfile을 만들어서 Build 는 방법이 있다.  본 문서는 Dockerfile에 build를 적용한 도커 이미지 만들기를 진행한다.

###  단계  1. 도커  파일 만들기  

* 기본 이미지는 ubuntu:20.04로 설정
* python3를 이미지를 만들면서 설치, 옵션 질문시 yes
* /var/www/html로 이동 (없으면 폴더를 만들고)
* python3 기반의 웹서버를 실행

```dockerfile
FROM ubuntu:20.04
RUN apt update && apt install -y python3
WORKDIR /var/www/html
CMD ["python3", "-u", "-m", "http.server"]
```



### 단계2. Dockerfile을 이용한 이미지 만들기

* 이미지의 이름은  web-server-build (-t 옵션)
* 컨테이너가 실행되고 강제로 삭제 

```shell
$ docker build -t web-server-build .
$ docker rm --force web-server
$ docker run -p 8888:8000 --name web-server web-server-build pwd
```

