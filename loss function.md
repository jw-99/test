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

loss function은 regression 과 classification 두 가지 유형으로 구분할 수 있습니다. regression은 연속적인 값을을 예측할 때 사용합니다. classification은 불연속적인 클래스를 분류하기 위해 사용하며 각 클래스에 확률값이 부여됩니다.

## Regression loss function

### MSE(Mean Squeared Error)

회귀 손실에 사용되는 가장 기본적인 함수입니다. MSE는 실제값과 예측값 사이 오차 제곱의 평균으로 계산됩니다. 제곱을 했기 때문에 오차가 클 수록 더 큰 패널티가 부여됩니다. 이런 이유로 이상치에 큰 영향을 받습니다.



### MAE(Mean Absolute Error)

MAE는 실제값과 예측값 차이 절대값의 평균으로 계산됩니다. MAE는 이상치가 있는 문제에서 적절히 사용될 수 있습니다.


### hinge



## Classification loss function

cross entropy

다진분류


### Reference

https://machinelearningmastery.com/how-to-choose-loss-functions-when-training-deep-learning-neural-networks/
