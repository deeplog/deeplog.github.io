---
title: Git Rename
layout: post
category: Git
---

#### Reset 

HEAD reset
```
git reset --soft HEAD~
```

HEAD + Index reset 
```
# 아래 두개는 동일한 의미임
git reset --mixed HEAD~
git reset HEAD~
```

HEAD + Index + Working Directory Reset
```
git reset --hard HEAD~
```
Unstaged 상태로 만들기  
```
git reset file.txt
```  
reset을 하면 stage와 head를 이전 상태로 되돌리기 때문이다.  
대신 working directory에 영향을 주지는 않는다.  
git add 를 되돌리고 싶을때 사용하면 된다. 

