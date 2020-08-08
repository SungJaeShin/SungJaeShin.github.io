---
layout: post
title: Chapter 2 - Binary Classification
date: 2020-08-08 00:33:45
---

# < Binary Classification >
## <u>Logistic Regression</u> is an algorithm for binary classification
### (Example) Binary Classification Problem

* Assume : 이미지를 넣었을 때, 이 이미지가 고양이인지, 아닌지 판별하는 문제가 있다. <br>
* y = 1 : 이 이미지를 고양이로 판별을 했을 경우 <br>
* y = 0 : 이 이미지를 고양이가 아니라고 판별했을 경우 <br>

다음 [그림 1]과 같이 나타낼 문제를 정의할 수 있다.

<br>
<center><img src="https://github.com/SungJaeShin/SungJaeShin.github.io/blob/master/imgs/deeplearning/fundamental/2-1.PNG?raw=true"></center>

[그림 1]의 Input으로 넣었던 Cat Image에 대해서 Red, Green, Blue 채널들과 일치하는 3개의 행렬을 [그림 2]와 같이 따로 저장한다. 행렬에 쓰여진 값들을 **<u>"Pixel Intensity Value"</u>** 라고 부른다. <br>

* (참고) 만일, Input Image가 64 pixel X 64 pixel이라면, 3개의 64x64 행렬들이 사진의 Red, Green, Blue Pixel Intensity Value를 나타낸다!! <br>

<center><img src="https://github.com/SungJaeShin/SungJaeShin.github.io/blob/master/imgs/deeplearning/fundamental/2-2.PNG?raw=true"></center>


[그림 2]와 같은 pixel intensity value들을 특성 벡터로 바꾸려면, 모든 pixel 값을 입력될 __특성 벡터 X인 하나의 열__ 로 나타낼 것이다. 이는 [그림 3]과 같이 표현이 되고 위에서부터 차례대로 64 x 64 (=4096)개는 Red에 해당하는 intensity value이고 밑에는 Green, Blue 순서대로 표현된다. <br>

<center><img src="https://github.com/SungJaeShin/SungJaeShin.github.io/blob/master/imgs/deeplearning/fundamental/2-3.PNG?raw=true" width="30%" height="30%"></center>

* (참고) 만일, 64 x 64 Image인 경우, Vector X의 total dimension은 __"64 X 64 X 3 = 12288 차원"__ 이 된다. <br>
     이 경우, Input Feature Vector X의 Dimension은 다음과 같이 표현한다!! : &#8594; &#8756; __n = n<sub>x</sub> = 12288__ <br>


<br>
## The Goal of Binary Classification
- 입력된 사진을 나타내는 __특성벡터 X__ 를 가지고 이것에 대한 __Label Y__ 가 1 & 0 (= 고양이 사진인지(y=1) 아닌지(y=0)) 예측할 수 있는 __분류기를 학습__ 하는 것이다. <br>


<br>
## General Notation of Binary Classification
* 단 하나의 Training Sample을 한 쌍의 (X, y)로 표시할 때, &#8712;

<!--
* 참고 : Function들 중에서 다음과 같은 **<u>"ReLU(=Rectified Linear Unit)"</u>** 함수를 많이 볼 수 있다. <br>
  　　&nbsp; 여기서 __Rectified라는 의미는 0과 결과 값 중에서 큰 값을 취라하는 의미로 사용되었다.__ [그림 3]이 ReLU Function이다.


사실 집값을 예측하는데에 있어 여러 가지 특징(features)들이 존재한다. <br>
* Input X &nbsp; : size &nbsp; -> &nbsp; size, number of bedrooms, zip code(posted code), wealth <br>
* Output y : price <br>

<center><img src="https://github.com/SungJaeShin/SungJaeShin.github.io/blob/master/imgs/deeplearning/fundamental/1-4.PNG?raw=true" width="70%" height="70%"></center> <br>

[그림 4]에서 (Area 2)에 있는 Node들을 __<u>"Hidden Unit"</u>__ 이라고 부르고 이들은 ReLU가 될 수 있고 아니면 다른 비선형 함수가 될 수도 있다. <br>
family size, walkability, school quality와 같은 feature들은 Training Set인 Input X & Output y의 많은 Sample들을 주고 스스로 알아내게 된다. (Prediction!!) <br>
그 결과 최종 집의 가격을 예측하는 결과 y가 나오게 된다.

## In General 및 정리
<center><img src="https://github.com/SungJaeShin/SungJaeShin.github.io/blob/master/imgs/deeplearning/fundamental/1-5.PNG?raw=true" width="70%" height="70%"></center> <br>

* Node 1 은 x<sub>1</sub> 과 x<sub>2</sub> 특성에서만 영향을 받는다고 하기보다는 어떤 신경망을 만들고 싶던지, 어떤 계산을 하고 싶던지 4개의 입력을 다 받을 것이다. <br>
* 신경망의 입력층과 이 중앙에 있는 Hidden Unit층은 긴밀하게 연결되어 있다. (__* 모든 입력 특성들은 중앙에 있는 Node 모두에 연결되어 있기 때문이다.__)
* 충분한 양의 X와 y를 Traning Data로 준다면 신경망은 X를 y로 연결하는 함수를 알아내는데 정말로 뛰어날 것이다.


<br>

# < Supervised Learning with a Neural Network >
## 일반적으로 Neural Network에서 일반적으로 사용되는 3가지 예제가 있다.
<center><img src="https://github.com/SungJaeShin/SungJaeShin.github.io/blob/master/imgs/deeplearning/fundamental/1-6.PNG?raw=true" width="70%" height="50%"></center>

<br>

# < Why is Deep Learning Taking off? >
## Scale drives deep learning progress

<center><img src="https://github.com/SungJaeShin/SungJaeShin.github.io/blob/master/imgs/deeplearning/fundamental/1-7.PNG?raw=true" width="70%" height="70%"></center>

1. Traditional learning algorithm
  * 데이터를 추가하는 동안 성능이 향상되지만 어느정도 지나면 성능이 정체기에이른다. (__* 방대한 data로 뭘 해야하는지 모르는 것처럼 보인다.__)
2. Couple of Observation to perform high level performance
  * 많은 양의 데이터를 이용하기 위해 충분히 큰 신경망이 필요하다. (__* 큰 신경망 = 많은 Hidden Unit이 필요 = 많은 Connection & Parameter가 필요__)
  * Input Data가 아주 많이 필요하다.
3. In small training set
  * 알고리즘의 상대적 순위가 잘 정의되어 있지 않다. (__* 특성을 다루는 실력이나 알고리즘의 작은 부분이 성능을 크게 좌우한다.__)

4. In large traning set
  * 큰 신경망이 다른 방법을 압도하는 경향을 보이고 있다.
5. Transformation of algorithm can improve computation
  * (예를 들면) Sigmoid Function -> ReLU Function 으로 바꾸면 Computation을 향상시킬 수 있다. (__* Gradient Descent를 사용하는 것이 더 삐를 것이다.__)
 -->
