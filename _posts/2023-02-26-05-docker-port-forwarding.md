---
title: 05. Docker 포트포워딩
layout: post
category: Docker
---

출처: 본 문서는 [생활코딩 도커편](http://opentutorials.org/course/128/8657/)을 참고하여 작성하였습니다. 



* 선행 작업으로 [Docker pull](https://deeplog.github.io/docker/2023/02/26/03-docker-pull.html)을 통한 아파치 서버 이미지가 먼저 pull 되어 있어야 됩니다. 

## 포트 포워딩



호스트의 포트와 컨테이너 포트를 연동하면 도커 내부 포트를 연결할 수 있다.  이를 port forwarding이라고 한다. [공식문서참고](https://docs.docker.com/engine/reference/commandline/run/#publish)

외부에서 8081로 접속하면 컨테이너 80 포트로 연결되도록 실행하려면 아래와 같이 명령을 입력한다. 

```shell
user@DESKTOP-PPEIC48:~$ docker run --name ws2 -p 8081:80 httpd
```



실행되고 있는 컨테이너 확인

```shell
$ docker ps
```

실행 결과는 아래와 같다. 

```shell
b4d647717358   httpd     "httpd-foreground"   About a minute ago   Up About a minute   0.0.0.0:8081->80/tcp, :::8081->80/tcp   ws2
```

웹으로 접속하면 다음과 같은 결과를 볼 수 있다. 

![image-20230226184144910](/public/img/image-20230226184144910.png)
