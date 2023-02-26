---
title: Linux 설치
layout: post
category: Docker
---

## 윈도우즈11에서 리눅스 설치



윈도우즈 11 기준으로 설명한다. 도커를 보다 자유롭게 사용하기 위해서 윈도우즈에 리눅스를 설치하였다. 여기서는 윈도우즈에 리눅스를 설치하는 방법을 정리한다. 



### 1. Linux용 Windows 하위 시스템

* 시작에서 windows 검색 -> Windows 기능 켜기/끄기
* Linux용 Windows 하위시스템 및 가상머신 플랫폼 선택
* 확인 후 컴퓨터 재시작하기 

![image-20230226091734742](/public/img/image-20230226091734742.png)



### 2. Ubuntu 설치

* Microsoft Store에서 Ubuntu22.04.5 LTS 설치 

* 500.7MB 라서 다운로드 하는데 시간이 걸릴 수 있음

* 열기 버튼을 누르면 설치를 진행함

  ![image-20230226092604388](/public/img/image-20230226092604388.png)

* 설치중 다음과 같은 오류를 만나면  WSL2 Linux Kernel Update를 설치해준다. (WSL = windows subsytem for linux)
* 다운로드 링크: https://wslstorestorage.blob.core.windows.net/wslblob/wsl_update_x64.msi

![img](/public/img/wslerror.png)



### 3. Ubutu 셋업

* ubuntu 설치가 되면 다음과 같이 설치 과정중 설정 작업을 요청한다. 

* ID, Password 작업을 설정하면 윈도우즈에서 리눅스를 사용할 수 있다.

  ```shell
  Enter new UNIX username: testuser
  Enter new UNIX password:
  Retype new UNIX password:
  ```

  