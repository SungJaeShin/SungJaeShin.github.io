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
     이 경우, Input Feature Vector X의 Dimension은 다음과 같이 표현한다!! &#8594; &#8756; __n = n<sub>x</sub> = 12288__ <br>


<br>
## The Goal of Binary Classification
- 입력된 사진을 나타내는 __특성벡터 X__ 를 가지고 이것에 대한 __Label Y__ 가 1 & 0 (= 고양이 사진인지(y=1) 아닌지(y=0)) 예측할 수 있는 __분류기를 학습__ 하는 것이다. <br>


<br>
## General Notation of Binary Classification
* 단 하나의 Training Sample을 한 쌍의 (X, y)로 표시할 때, X &#8712; R<sup>n<sub>x</sub></sup>, y &#8712; {0, 1}이다. <br>
* Training Set는 m개의 훈련 샘플을 포함할 때, {(x<sup>(1)</sup>, y<sup>(1)</sup>), (x<sup>(2)</sup>, y<sup>(2)</sup>), &#8230; ,(x<sup>(m)</sup>, y<sup>(m)</sup>)}으로 표현된 것이 m개의 Train Sample이다. <br>
* 입력된 Training Set들을 열들로된 (&#8658; m개의 훈련 샘플이 있을 때) 행렬 X는 [그림 4]와 같다.

<center><img src="https://github.com/SungJaeShin/SungJaeShin.github.io/blob/master/imgs/deeplearning/fundamental/2-4.PNG?raw=true" width="50%" height="50%"></center> <br>

* 결과 값의 행렬 y는 Row Matrix로 놓은 것이 편하다. 이는 [그림 5]와 같이 나타낼 수 있다.

<center><img src="https://github.com/SungJaeShin/SungJaeShin.github.io/blob/master/imgs/deeplearning/fundamental/2-5.PNG?raw=true" width="50%" height="50%"></center> <br>
