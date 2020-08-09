# Insurance_Fraud_Detection_Prj
고객 정보를 바탕으로 보험사기자를 예측하는 프로젝트
## 개요
- 고객정보인 CUST_DATA,CLAIM_DATA를 바탕으로 보험사기자 예측
- 결측치, 이상치 처리및 학습을 잘할수 있도록 column조정
- 파생변수 추가
- 머신러닝 및 모델 평가
## 데이터
- CUST_DATA : 고객의 기본정보와 보험사기자 여부를 포함
- CLAIM_DATA : 병원 입원일, 보험금 납입일등 기타 정보
- answer.csv : DIVIDED_SET==2 인 고객들의 사기자 여부
## 전처리 및 파생변수 추가
- 연관성이 높은 변수들은 원핫 인코딩
- 결측치와 이상치는 각 나이대별 직업군별 평균으로 치환
- 지역, 성별, 직업 등 숫자가 아닌 문자로 되어있는 칼럼 숫자로 변경
- 고객별 평균 입원일, 유의 병원 사고원인과 청구횟수 등 CLAIM_DATA중 상관관계가 높은 칼럼 추가
- 청구금액과 지급금액 차이, 보험금 납입시기와 지급시기의 차이에 대한 파생변수 추가
- 상관관계가 적은 칼럼 삭제
## 머신러닝 및 평가
- sklearn을 기반으로 진행
- 사기자여부의 데이터 불균형이 심하므로 Smote를 통해 Oversampling 하여 데이터 균형을 맞춰주기
- RandomForest, MLP, SVM, XGBOOST, LIGHTGBM 으로 예측후 validation_set으로 모델 평가
- 모델 평가 기준으로 상위 세개에 해당하는 RandomForest, XGBOOST, LIGHTGBM 모델을 이용하여 Voting_model 생성
- answer.csv 파일을 불러와 모델 평가 (F1_measure = 0.63)
