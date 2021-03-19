---
published : true # 건드리지 마세요
layout : posts # 건드리지 마세요
title: "[ML Research] Loss function" # [category 명]제목  <= 해당 양식에 맞춰주세요
date: 2020-02-24 # 날짜를 적어주세요
excerpt: "loss and loss function" # 요약을 적어주세요
comments: true # 건드리지 마세요
use_math: true # 건드리지 마세요
author : Jeongwon jo # 본인 프로필 이름을 입력해주세요
---

# Loss function

딥러닝 모델은 확률적 경사하강법과 최적화 알고리즘으로 학습합니다. 최적화 알고리즘으로 모델의 현 상태에 대한 오류를 추정하여 손실을 줄이는 방향으로 가중치를 업데이트 합니다. 모델의 오류를 추정하기 위해 사용하는 함수가 loss function입니다.

loss function은 회귀와 분류 두 가지 유형으로 구분할 수 있습니다. 회귀 손실은 연속적인 값을을 예측할 때 사용합니다. 분류 손실은 불연속적인 클래스를 분류하기 위해 사용하며 각 클래스에 확률값이 부여됩니다.

## Regression loss function

### MSE(Mean Squared Error)

> $$ MSE = {1 \over n}\sum_{i=1}^N(Y_i - \hat(Y)_i)$$

회귀 손실에 사용되는 기본적인 함수입니다. MSE는 실제값과 예측값 사이 오차 제곱의 평균으로 계산됩니다. 제곱을 했기 때문에 오차가 클 수록 더 큰 패널티가 부여됩니다. 이런 이유로 이상치에 큰 영향을 받습니다.

### RMSE(Root Mean Squared Error)
> $$RMSE(\hat(\theta)) = \sqrt(mse(\hat(\theta)))

RMSE는 MSE에 루트를 씌운 것입니다. 원래 타겟에 대해 더 나은 직관을 제공합니다.

### MAE(Mean Absolute Error)

> $$MAE = { \sum_ {i=1}^N(|y_i - x_i|)\over n} = {\sum_{i=1}^N|e_i|}$$

MAE는 실제값과 예측값 차이 절대값의 평균으로 계산됩니다. MAE는 이상치가 있는 문제에서 적절히 사용될 수 있습니다. 하지만 최적화에서 MAE를 사용하면 기울기가 계속해서 커지게 됩니다. 이것은 loss가 작을 때도 발생하므로 학습에 문제가 발생합니다. 또한 MAE는 미분이 어렵다는 점이 존재합니다.

### Huber loss
> $$Huber loss(t,p) = \begin{cases} {1 \over n}(t - p)^2, & \mbox{when}|t - p| \leqq δ \\ δ|t - p| - {δ^2 \over 2}, \mbox{otherwise} \end{cases}$$

Huber loss는 loss가 클 때는 MAE를 취해 이상치에 민감한 MSE의 단점을 극복하고 loss가 작을 때는 MSE를 취해 미분이 가능하게 합니다.

![image](https://user-images.githubusercontent.com/80579716/111460794-be57cc80-875f-11eb-9626-ccc3a721b751.png)

위 그림에서 작은 δ일 때는 기울기가 평평합니다. 이는 손실이 커질 때까지 꽤 시간이 걸립니다.
작은 δ는 이상치에 둔감해질 수 있지만 평균 오류가 작을 때는 좋지 않습니다.

δ가 클 수록 기울기가 증가합니다. 이 기울기는 최대로 수렴하는 경향이 있습니다.
작은 δ는 이상치에 민감하여 평균 오류가 작을 때는 괜찮지만 이상치가 있을 때는 문제가 발생합니다.

> Huber loss는 δ ~ 0일 때 MAE에 다가가고, δ ~ ∞ 일 때 MSE에 다가갑니다.

## Classification loss function

### Binary cross entropy

> $$ BCE(t,p) = -(t * log(p) + (1-t) * log(1-p))$$

신경망에서 가장 자주 사용되는 loss function이 binary cross entropy 입니다. 이진분류에 대한 손실함수이며 sigmoid와 같이 신경망의 출력값이 0과 1일 때 사용됩니다.
![image](https://user-images.githubusercontent.com/80579716/111457674-dc233280-875b-11eb-8be6-70661150c635.png)
위 그림에서 실제값이 1인 경우 왼쪽으로 갈 수록 loss가 증가하여 잘못된 예측을 처벌한다 할 수 있으며 잘못된 예측을 확신할 경우 loss가 빠르게 증가하여 더 큰 불이익을 받게 됩니다.

### Categoricla cross entropy

> $$ CCE(p,t) = -\sum_{c=1}^C(t_{o,c}log(p,c))$$

출력의 클래스가 2이상인 다중클래스 문제에 사용하는 손실함수입니다.

### Reference

https://machinelearningmastery.com/how-to-choose-loss-functions-when-training-deep-learning-neural-networks/
https://www.machinecurve.com/index.php/2019/10/04/about-loss-and-loss-functions/
