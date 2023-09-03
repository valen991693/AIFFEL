# AIFFEL Campus Online 5th Code Peer Review Templete
- 코더 : 김범준
- 리뷰어 : 어윤석

# PRT(PeerReviewTemplate) 
각 항목을 스스로 확인하고 토의하여 작성한 코드에 적용합니다.

- [X] 코드가 정상적으로 동작하고 주어진 문제를 해결했나요? 
  > 프로젝트1 - MSE : 2870.533631108969  
      코드가 정상적으로 동작하고 프로젝트에서 요구하는 상세기준에 맞는 결과를 얻었습니다.  
  > 프로젝트2 - RMSE : 158.32713046622834  
      RMSE 값 150 이하를 달성하지 못하여 해당 원인에 대해 함께 리뷰하였습니다.  
      학습 데이터의 컬럼 선택에서 'datetime'으로 부터 추출한 컬럼들이 포함되지 않은 부분을 원인으로 예상하였습니다.
  
- [ ] 주석을 보고 작성자의 코드가 이해되었나요?
  > 주석이 포함되어 있지 않아 코드에 대한 간단한 설명이 주석으로 추가되면 좋을 것 같습니다.

- [X] 코드가 에러를 유발할 가능성이 없나요?
  > 코드에서 에러가 발생할 가능성이 없어 보이지만 model함수 선언에 개선 사항에 대해 이야기하였습니다.

- [X] 코드 작성자가 코드를 제대로 이해하고 작성했나요?
  > 코드에 대해 잘 이해하고 작성하였습니다.  
      프로젝트2 의 (1)데이터 가져오기 부분에서 각 데이터 열의 조합에 대해 seaborn pairplot으로 스캐터 플롯을 그려보거나 컬럼별 max값을 확인하는 등  데이터 분석을 위한 코드가 추가되어 있었습니다.  
  
- [X] 코드가 간결한가요?
  > 불필요한 내용 없이 간결하게 코드가 작성되었습니다.

# 개선 사항
1. 프로젝트1 : model 함수 선언 시 일반화를 위해 for문의 range 설정을 인자로 받는 학습데이터 X에서 가져와 설정하도록 개선
```python
def model(X,W,b):
    predictions = 0    
    # for i in range(10):
    for i in range(X.shape[1]):
        predictions += X[:, i] * W[i]
    predictions += b
    return predictions
```
2. 프로젝트2 : 학습 데이터의 컬럼 설정 부분에 'datetime'으로 부터 추출한 년, 월, 일, 시, 분 등의 데이터 컬럼을 추가하도록 개선
```python
# features = ['season', 'holiday', 'workingday', 'weather', 'temp', 'atemp', 'humidity', 'windspeed']
features = ['season', 'holiday', 'workingday', 'weather', 'temp', 'atemp', 'humidity', 'windspeed',
            'year','month','day','hour','minute','second']
y = train['count']
train_X, test_X, train_Y, test_Y = train_test_split(train[features], y, test_size = 0.2)
```
