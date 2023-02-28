---
title: Docker Compose
layout: post
category: Docker
---

출처: 본 문서는 [생활코딩 Docker Compose를 이용해서 복잡한 도커 제어하기](https://www.youtube.com/watch?v=EK6iYRCIjYs)을 참고하여 작성하였습니다. 

## Docker Compose

shell을 이용해서 DB 서버를 만들고, DB와 연동이 되는 App을 만들고 이를 각각의 컨테이너로 만들어서 연동하는 작업을 하기 위해서는 docker run으로 시작하는 쉘 스크립트를 여러 줄에 걸쳐서 작성해야 한다. 이러한 작업의 반복성을 줄이고 향후 유지보수가 용이하기 위해서 yml 파일로 만들어서 관리한다. yml을 실행시키기 위해서는 Docker에서 제공하는 docker compose를 이용한다.   



### Shell Script에 의한 APP 실행

```shell
# 도커간의 네트워킹을 위한 네트워크 생성
$ docker network create wordpress_net

$ docker \
  run \
    --name "db" \
    -v "$(pwd)/db_data:/var/lib/mysql" \
    -e "MYSQL_ROOT_PASSWORD=123456" \
    -e "MYSQL_DATABASE=wordpress" \
    -e "MYSQL_USER=wordpress_user" \
    -e "MYSQL_PASSWORD=123456" \
    --network wordpress_net \
    mysql:5.7
    
$ docker \
    run \
    --name app \
    -v "$(pwd)/app_data:/var/www/html" \
    -e "WORDPRESS_DB_HOST=db" \
    -e "WORDPRESS_DB_USER=wordpress_user" \
    -e "WORDPRESS_DB_NAME=wordpress" \
    -e "WORDPRESS_DB_PASSWORD=123456" \
    -e "WORDPRESS_DEBUG=1" \
    -p 8080:80 \
    --network wordpress_net \
    wordpress:latest
```

### Docker composer에 의한 APP 실행

도커 composer는 네트워크를 만드는 작업은 필요 없다. 왜냐면 Docker compose가 자동으로 네트워클 만들고 연결해 주기 때문이다. 

docker-compose.yml

```yaml
version: "3.7"

services:
  db:
    image: mysql:5.7
    volumes:
      - ./db_data:/var/lib/mysql
    restart: always
    environment:
      MYSQL_ROOT_PASSWORD: 123456
      MYSQL_DATABASE: wordpress
      MYSQL_USER: wordpress_user
      MYSQL_PASSWORD: 123456
  
  app:
    depends_on: 
      - db
    image: wordpress:latest
    volumes:
      - ./app_data:/var/www/html
    ports:
      - "8080:80"
    restart: always
    environment:
      WORDPRESS_DB_HOST: db:3306
      WORDPRESS_DB_NAME: wordpress
      WORDPRESS_DB_USER: wordpress_user
      WORDPRESS_DB_PASSWORD: 123456
```

Docker Compose 실행

```shell
$ docker-compose up
```

Docker Compose 종료

```shell
$ docker-compose down
```

