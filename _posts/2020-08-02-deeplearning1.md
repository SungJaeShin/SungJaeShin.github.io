---
layout: post
title: Chapter 1 - Introduction of Neural Network and Deep Learning
date: 2020-08-02 16:14:53
---

# <What is Neural Network?>
## (Example) House Price Prediction  
### * Assumption : 6개의 집값의 데이터가 존재한다고 가정

<br>

!

[그림 1]은 집의 크기에 따른 가격을 그래프로 나타낸 그림이다. x축은 집의 크기를 나타내고, y축은 가격을 의미한다. <br>

여기서 6개의 point들을 가장 나타내는 직선은 그림과 같이 나타낼 수 있다고 가정하였을 때, (Area 1)처럼 0으로 만든 부분이 존재하는데 이 경우는 주택의 가격은 음수가 될 수 없기 때문에 나머지를 0으로 만듦으로서 더 좋은 함수를 표현할 수 있기 때문이다. <br>

[그림 1]을 우리는 간단한 Neural Network로 만들 수 있다. [그림 2]와 같이 Single Neural Network로 표현될 수 있다.

!

여기서 Node를 __"Neuron"__ 이라고 부르고, Neuron의 역할은 __주택의 크기를 입력으로 받아서 선형함수를 계산하고 결과 값과 0 중에서 큰 값을 주택의 가격으로 예측한다.__ <br>


* 참고 : Function들 중에서 다음과 같은 ReLU(=Rectified Linear Unit)함수를 많이 볼 수 있다. 여기서 Rectified라는 의미는 __0과 결과 값 중에서 큰 값을 취라하는 의미로 사용되었다.__ <br>
* [그림 3]이 ReLU Function이다.

!

사실 집값을 예측하는데에 있어 여러 가지 특징들이 존재한다. 
