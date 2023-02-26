---
title: Git Branch
layout: post
category: Git
---

### 브랜치 관리
* ```git branch``` :  브랜치의 목록을 보여준다.
* ```git branch --merged``` : merged 목록을 보여준다.
* ```git branch --no-merged```

### 브랜치 워크 플로우
##### Long-Running 브랜치 
Master를 기본으로 하고 develop으로 개발하다가 안정적이 되면 master에 머지한다.
##### 토픽 브랜치
어떤 한가지 주제나  작업을 위해 만든 짧은 호흡의 브랜치

### 리모트 브랜치
##### git fetch / push
리무트 트래킹 브랜치는 로컬에 있지만 임의로 움직일 수 없다. <br> ```origin/master``` 는 origin에 있는 branch 마스터를 가리키는 포인터이다.  
origin에서 데이터 가져오기: ```git fetch origin```  
이 명령어는 origin서버의 데이터를 가져와서 origin/master가 서버의 commit을 가리키도록 한다.  
git fetch 는 수정할 수 있는 브랜치가 아니며 단순히 수정을 하지 못하는 origin/master라는 브랜치 포인터를 생성한다.  
git push remote branch - 서버에 푸시한다.

##### 브랜치 tracking
```git merge origin/serverfix``` 명령을 사용한다.  
```git checkout -b serverfix origin/serverfix``` 추적할 수 있는 트래킹 브랜치를 로컬에 만들고 체크아웃한다.  
 ```git brach -vv```: 로컬 브랜치와 추적하는 리무트 브랜치를 같이 보여준다.

##### Pull
서버로부터 데이터를 가져와서 현재 로컬 브랜치와 추적 브랜치를 merge한다.  
git fetch를 실행한후 git merge를 생하는 것과 같은 의미

##### 리무트 브랜치 삭제하기
 ```git push origin --delete serverfix```

##### Rebase
한 브랜치의 base를 다른 브랜치의 최신 커밋으로 옮기는 것
복잡한 형태의 브랜치를 단순하게 유지시킬 수 있는 장점이 있다.  
로컬에서 히스토리 정리하는데 사용하는 용도가 됨

__주의사항: Push로 내보낸 commit은 절대 rebase 하지 말것__

* step1: ```git checkout feature```  
* step2: ```git rebase master```

##### git rebase 예제


![](/public/img/merge_rebase.png)