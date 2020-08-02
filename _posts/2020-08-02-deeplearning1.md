---
layout: post
title: Chapter 1 - Introduction of Neural Network and Deep Learning
date: 2020-08-02 16:14:53
---

# < What is Neural Network? >
## (Example) House Price Prediction  
### * Assumption : 집값을 예측할 수 있는 6개의 데이터가 존재한다고 가정, <x, y> = <size, price>

<br>
<center><img src="https://github.com/SungJaeShin/SungJaeShin.github.io/blob/master/imgs/deeplearning/fundamental/1-1.PNG?raw=true" width="500px" height="300px"></center>


[그림 1]은 집의 크기에 따른 가격을 그래프로 나타낸 그림이다. x축은 집의 크기를 나타내고, y축은 가격을 의미한다. <br>

여기서 6개의 point들을 가장 나타내는 직선은 그림과 같이 나타낼 수 있다고 가정하였을 때,  
(Area 1)처럼 0으로 만든 부분이 존재하는데 이 경우는 주택의 가격은 음수가 될 수 없기 때문에 나머지를 0으로 만듦으로서 더 좋은 함수를 표현할 수 있기 때문이다. <br>

[그림 1]을 우리는 간단한 Neural Network로 만들 수 있다. [그림 2]와 같이 Single Neural Network로 표현될 수 있다.

<center><img src="https://github.com/SungJaeShin/SungJaeShin.github.io/blob/master/imgs/deeplearning/fundamental/1-2.PNG?raw=true"></center>

여기서 Node를 **<u>"Neuron"</u>** 이라고 부르고, Neuron의 역할은 __주택의 크기를 입력으로 받아서 선형함수를 계산하고 결과 값과 0 중에서 큰 값을 주택의 가격으로 예측한다.__ <br>


* 참고 : Function들 중에서 다음과 같은 **<u>"ReLU(=Rectified Linear Unit)"</u>** 함수를 많이 볼 수 있다.
  　　　여기서 __Rectified라는 의미는 0과 결과 값 중에서 큰 값을 취라하는 의미로 사용되었다.__ [그림 3]이 ReLU Function이다.

<center><img src="https://github.com/SungJaeShin/SungJaeShin.github.io/blob/master/imgs/deeplearning/fundamental/1-3.PNG?raw=true" width="30%" height="30%"></center>

사실 집값을 예측하는데에 있어 여러 가지 특징(features)들이 존재한다. <br>
* Input X &nbsp; : size -> size, number of bedrooms, zip code(posted code), wealth <br>
* Output y : price <br>

<center><img src="https://github.com/SungJaeShin/SungJaeShin.github.io/blob/master/imgs/deeplearning/fundamental/1-4.PNG?raw=true" width="70%" height="70%"></center> <br>

[그림 4]에서 (Area 2)에 있는 Node들을 __<u>"Hidden Unit"</u>__ 이라고 부르고 이들은 ReLU가 될 수 있고 아니면 다른 비선형 함수가 될 수도 있다. <br>
family size, walkability, school quality와 같은 feature들은 Traning Set인 Input X & Output y의 많은 Sample들을 주고 스스로 알아내게 된다. (Prediction!!) <br>
그 결과 최종 집의 가격을 예측하는 결과 y가 나오게 된다.

## In General 및 정리
<center><img src="https://github.com/SungJaeShin/SungJaeShin.github.io/blob/master/imgs/deeplearning/fundamental/1-5.PNG?raw=true" width="70%" height="70%"></center> <br>

* Node 1 은 x<sub>1</sub> 과 x<sub>2</sub> 특성에서만 영향을 받는다고 하기보다는 어떤 신경망을 만들고 싶던지, 어떤 계산을 하고 싶던지 4개의 입력을 다 받을 것이다. <br>
* 신경망의 입력층과 이 중앙에 있는 Hidden Unit층은 긴밀하게 연결되어 있다. (__* 모든 입력 특성들은 중앙에 있는 Node 모두에 연결되어 있기 때문이다.__)
* 충분한 양의 X와 y를 Traning Data로 준다면 신경망은 X를 y로 연결하는 함수를 알아내는데 정말로 뛰어날 것이다.


<br>

# < Supervised Learning with a Neural Network >
## 일반적으로 Neural Network에서 일반적으로 사용되는 3가지 예제가 있다.
### [그림 6] 참고.
<center><img src="https://github.com/SungJaeShin/SungJaeShin.github.io/blob/master/imgs/deeplearning/fundamental/1-6.PNG?raw=true" width="80%" height="60%"></center>

<br>

# < Why is Deep Learning Taking off? >
## Scale drives deep learning progress

<center><img src="https://github.com/SungJaeShin/SungJaeShin.github.io/blob/master/imgs/deeplearning/fundamental/1-7.PNG?raw=true" width="70%" height="70%"></center>

1. Traditional learning algorithm
  * 데이터를 추가하는 동안 성능이 향상되지만 어느정도 지나면 성능이 정체기에이른다. (__* 방대한 data로 뭘 해야하는지 모르는 것처럼 보인다.__) <br>

2. Couple of Observation to perform high level performance
  * 많은 양의 데이터를 이용하기 위해 충분히 큰 신경망이 필요하다. (__* 큰 신경망 = 많은 Hidden Unit이 필요 = 많은 Connection & Parameter가 필요__)
  * Input Data가 아주 많이 필요하다. <br>

3. In small training set
  * 알고리즘의 상대적 순위가 잘 정의되어 있지 않다. (__* 특성을 다루는 실력이나 알고리즘의 작은 부분이 성능을 크게 좌우한다.__) <br>

4. In large traning set
  * 큰 신경망이 다른 방법을 압도하는 경향을 보이고 있다. <br>

5. Transformation of algorithm can improve computation
  * (예를 들면) Sigmoid Function -> ReLU Function 으로 바꾸면 Computation을 향상시킬 수 있다. (__* Gradient Descent를 사용하는 것이 더 삐를 것이다.__) <br>
