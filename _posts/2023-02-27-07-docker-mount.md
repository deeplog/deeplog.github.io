---
title: 07. Docker Mount
layout: post
category: Docker
---

출처: 본 문서는 [생활코딩 도커편](http://opentutorials.org/course/128/8657/)을 참고하여 작성하였습니다. 



## 도커 마운트

컨테이너 안의 파일은 컨테이너가 종료되면 Reset된다. 이러한 문제를 해결하기 위해 저장이 필요한 파일은 외부에 셋팅하고 컨테이너에서 마운트하여 사용한다.   다음과 같이 host에 있는 ~/htdocs/ 폴더를 컨테이너에 있는  /usr/local/apache2/htdocs/ 에 연결시킨다. 호스트에서 파일을 수정하면 도커의 내용이 반영된다. 

``` shell
$ docker run -p 8889:80 -v ~/htdocs/:/usr/local/apache2/htdocs/ httpd
```

