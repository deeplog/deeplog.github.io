---
title: MA 이해하기
layout: post
category: TimeSeries
---

출처: 본 문서는 [Time Series Talk : Moving Average Model](https://www.youtube.com/watch?v=voryLhxiPzE)을 참고하여 작성하였습니다. 

## 시계열에서 MA 이해하기

시계열에서 MA는 moving average 모형으로서, 과거의 값이 현재의 값에 영향을 주는 모형이며, 과거의 오차를 이용해서 회귀식을 세운다. 이에 대한 차수가 q인 모델의 정의는 다음과 같다. 

$$y_t=c+\epsilon_t+\theta_1\epsilon_{t-1}+\theta_2\epsilon_{t-2}+\dots+\theta_1\epsilon_{t-1}+\theta_q\epsilon_{t-q},    \epsilon_t \sim N(0, \sigma^2)$$

처음 봤을때 이걸 이해한다는 것은 쉽지 않다. 이게 무슨 소리인가? 그런데 이러한 모형을 아주 쉽게 설명해 주는  [Time Series Talk : Moving Average Model](https://www.youtube.com/watch?v=voryLhxiPzE) 유튜브가 있어서 이해할 수 있게 되었다. 이를 풀어서 설명해 본다. 

###  상황

* 어떤 교수가 있는데 Crazy한 교수라고 한다. 한달에 한번씩 파티를 여는데 컵케이크를 준비하라고 시켰다. 평균 10개의 컵케이크를 준비하는데  그런데 만약에 오차가 발생한다면 다음달에는 그 차이의 절반을 반영해서 컵케이크를 준비하도록 하였다. 일반적으로 이렇게 예상하는 것은 자연스러운 방법이다.

* 예를들어 1월에 10개의 컵케이크를 준비하였는데 8명이 파티에 와서 2개가 초과되면 다음달에는 2*0.5=1개의 컵케이크를 줄여서 준비한다. 

  ![MA](\public\img\MA.png)

* 이러한 상황에서 moving average 모형은 다음과 같다. 

  $$\hat{f_t}=\mu+\theta_1\epsilon_{t-1}$$

  $$\mu=10, \theta_1=0.5$$

* 즉, 이번달에 예측할 양은 평균 10개에 저번달의 오차에 가중치를 반영해서 더한 값이다. 저번달의 오차양이 이번달의 예측할 양에 가중치에 비례해서 영향을 주는 모형이 MA 모형이다 . 

* 한가지 흥미로운 점은, 이 영상에서 Moving average에 대해서 설명을 하였는데, 실제 필요했던 컵케이크는 8, 10, 10.5, 12, 12개가 각각 평균이 moving 하지만 그것은 결국에는 전체 평균 10을 갖게 된다고 하였다. 이것이 Moving average라고 하였다.  
