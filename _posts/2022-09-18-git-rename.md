---
title: Git Reset
layout: post
category: Git
---

## Reset

 git에서 commit을 한 이후에 다시 커밋을 되돌리고 싶은 경우가 있다. 이때 git reset을 사용해서 commit을 되돌린다.git reset은 (1) soft reset (2) mixed reset (3) hard reset ,세가지의 옵션이 있다. 개인적으로 Soft와 Mixed는 거의 써 본 적이 없음. 

### 1. Soft reset

soft reset은 git head가 지시한 커밋을 가리키도록 한다. working directory와 staging area는 영향을 미치지 않는다.

```
git reset --soft HEAD~
```

### 2. Mixed reset

mixed reset은  지시한 커밋으로 Head가 가리키게 하며, staging area도  해당 커밋과 동일하게 한다.  

```
# 아래 두개는 동일한 의미임
git reset --mixed HEAD~
git reset HEAD~
```

### 3. Hard reset

Head, staging area, working directory 모두 가리키는 커밋으로 바꾼다. 

```
git reset --hard HEAD~
```
