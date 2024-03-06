# 👋 Intro
```　
안녕하세요! 데이터 사이언티스트를 꿈꾸는 최무성 입니다.  
지금까지 배웠던 내용들을 정리하고 복기하고자 본 페이지를 만들었습니다.  
기본적으로 각 프로젝트들의 개요와 맡았던 역할, 결과 및 배웠던 점들을 기록하였습니다.  
```

<br />



# 📝Projects
> 데이터 관련 진행했던 프로젝트들을 정리해보았습니다.    
> 운영적인 측면에서는 팀원들과의 의사소통 및 역할 분배, 프로젝트 일정 관리를 맡아 프로젝트 전반적인 운영을 담당하였고,  
> 기술적인 측면에서는 대부분 모델링을 맡았으며 데이터 전처리 및 팀원들의 아이디어를 코드로 구현하는 역할을 수행하였습니다.

<br />

## 1. 💸 Lending Club 부도 예측 모델
### 부도 예측 모델 설계 _(서울대학교 빅데이터 핀테크 전문가 과정 6기, 6조 팀프로젝트)_
 - 핵심 역할 : 이진 분류 예측 모델링, 목적함수 코드 구현, 모델 성능 시각화

 ### 프로젝트 개요  
 - 목적 : 각 사용자 별 특징들을 기반으로 부도 예측 모델 개발
  
 - 데이터 : Lending Club Data
   - 데이터 형태 : 약 87만행 X 330열
   - 독립변수 : 각 사용자의 특성 (EX : 재산, 대출 금액, 신용 점수 등)
   - 종속변수 : 부도 여부
   - 이상치가 많았고, 부도 데이터가 16%로 불균형 데이터
  
 - 데이터 처리
   - 사후 변수 제거 : 대출 승인 여부에 대한 판단 시점에 사용가능한 변수와 불가능 변수를 구분
   - 다중공선성 확인 : 연속형 변수 간 다중공선성을 가진 변수 제거
   - 파생 변수 생성 : 범주형 변수의 속성 및 분포를 고려하여 그룹화
   - 변수 스케일링 : 이상치와 극단치를 고려하여 Robust Scaler 사용
   - 데이터 샘플링 : 불균형 데이터지만 데이터의 총량을 고려하여 Under Sampling
 
 - 사용한 모델
   - Decision Tree, Random Forest, Logistic Regression, XGBoost
   - 하이퍼 파라미터 최적화(필요한 경우) : 베이지안 최적화
  
   
### 프로젝트 결과 
| Model                | Accuracy | Precision | Recall | F1 score | 손실액     | 손실 감소 비율* |
|----------------------|----------|-----------|--------|----------|------------|---------------|
| Logistic Regression | 0.787 | 0.323 | 0.288 | 0.305 | 267569324 | 33% |
| Random Forest       | 0.769    | 0.308     | 0.342  | 0.324    | 277022671  | 30.6%         |
| Decision Tree       | 0.714    | 0.27      | 0.452  | 0.338    | 284704961  | 28.7%         |
| XG Boost            | 0.78     | 0.321     | 0.323  | 0.322    | 267977285  | 32.9%         |  
  
  
### 배운 점   
- 모든 변수들을 사용하는 것이 좋은 것이 아님, 모델 사용 시점과 더불어 도메인 지식에 대한 깊은 고민이 필요  
- 모델 자체의 성능뿐만 아니라 해당 모델이 사용될 영역에서 어떤 효과를 이끌어낼 수 있는가, 즉 **'목적함수'** 의 중요성
 
> [발표 자료 및 소스코드](https://github.com/choims12/LendingClub)

<br />

## 2. 🔥 김해시 화재 예측 모델
### 화재 예측 모델 설계 _(서울대학교 빅데이터 핀테크 전문가 과정 6기, 6조 팀프로젝트)_
 - 핵심 역할 : 이진 분류 예측 모델링, 파생 변수 생성 및 코드 구현, 모델 성능 시각화

 ### 프로젝트 개요  
 - 목적 : 경상남도의 소방 및 건물 관련 데이터를 활용하여 김해시 내 건축물의 화재 위험도 분석 및 예측 모델 개발

 - 데이터 : 김해시 화재발생 예측모델 개발 경진대회 데이터 (https://compas.lh.or.kr/subj/pas/info?subjNo=SBJ_1920_002#)
   - 데이터 형태 : 약 87만행 X 330열
   - 독립변수 : 소방 및 건물 관련 공공 정보
   - 종속변수 : 화재 발생 여부
   - 공공 데이터 중 결측치가 많았고, 화재가 발생한 비율이 18%로 불균형 데이터
  
 - 데이터 처리
   - 결측치 처리 : 변수의 성질과 결측인 비율을 고려하여 각기 다른 방식으로 대체 (EX : 결측치 비율이 3%이하며 연속형 변수 -> 동일 지역 평균값으로 대체)
   - 다중공선성 확인 : 동일한 의미를 가지는 변수들 제거 혹은 일원화
   - 파생 변수 생성 : 그룹화 및 변수들을 합쳐 새로운 변수 생성 (EX : 시간 관련 변수 -> 계절, 시간대 별 범주형 변수)
   - 데이터 샘플링 : 화재 발생 비율이 낮아 SMOTE를 활용하여 Over Sampling
    
- 사용한 모델
   - LGBM, XGBoost, Random Forest
   - 하이퍼 파라미터 최적화(필요한 경우) : 베이지안 최적화, Optuna
  
   
### 프로젝트 결과 
| Model          | Accuracy | Recall | Precision | F1 Score |
|----------------|----------|--------|-----------|----------|
| LGBM           | 0.83     | 0.38   | 0.58      | 0.46     |
| Random Forest  | 0.72     | 0.67   | 0.37      | 0.48     |
| XGBoost        | 0.78     | 0.58   | 0.44      | 0.50     |
  
  
### 배운 점   
- 각 변수들의 의미를 파악하고 새로운 변수를 만듦에 있어서 매우 깊은 고민이 필요
- 결측치를 처리하고 파생변수를 생성함에 있어 Train Set과 Test Set의 자료 차이를 고려해야 함 
 
> [발표 자료](https://github.com/kimphysicsman/MyLittelTrip_backend), [소스 코드](https://github.com/kimphysicsman/MyLittelTrip_backend)  

<br />

## 3. 📈 감성 지수를 활용한 주가 예측 모델
### 주가 예측 모델 설계 _(서울대학교 빅데이터 핀테크 전문가 과정 6기, 6조 팀프로젝트)_
 - 핵심 역할 : 뉴스 크롤링 및 감성 지수 계산, 모델링에 필요한 시계열 데이터 생성

 ### 프로젝트 개요  
 - 목적 : 경제 뉴스의 감성 지수와 거시 경제 지표들을 통해 주가 등락 예측 모델 개발

 - 데이터 : 뉴스 감성 지수 데이터 + 거시 경제 지표에 대한 시계열 자료 직접 생성
   - 데이터 형태 : 2020년 1월 ~ 2023년 3월 까지의 시계열 데이터
   - 사용변수 : 소비자물가지수, 금리, 환율, 감성 점수, 주가지수
  
 - 데이터 처리
   - 뉴스 크롤링 : Newspaper 라이브러리로 매일 경제의 해당 기간 모든 뉴스 중 ‘경제' 뉴스만 크롤링
   - 감성 분석 : 크롤링한 내용을 CLOVA Summary API를 통해 요약 후 CLOVA Sentiment API를 사용하여 감성 분석
   - 감성 지수화 : 해당 날짜의 감성 분석 값에 대해 (해당 일 기사 개수 / 전체 기사 개수)로 기사 개수에 대한 가중치와 긍정 +1, 중립 0, 부정 -1 가중치 부여하여 지수화
   - 거시 경제 변수 생성 : 주가 지수(KOSPI 200), 이자율(KORIBO), 금 값(1kg 기준), 유가(휘발유, 등유, 경유 평균가), 환율(KRX 데이터), CPI(소비자 물가지수 월 별 제공 -> 선형 보간법으로 일 별 데이터 생성)
   - 결측치 처리 : 뉴스, 주가, 이자율 등 휴일인 경우 관측되지 않기 때문에 해당 행 삭제
    
- 사용한 모델
   - Prophet, 1D CNN, Transformer
   - 각 모델 별 변수들을 다양하게 사용하며 결과 비교
  
   
### 프로젝트 결과 
- 시계열 자료 예측값의 오차 결과
  
| Model          | RMSE  | MAE   | Features                                    |
|-----------------|-------|-------|---------------------------------------------|
| Prophet         | 17.71 | 10.55 | Interest, Exchange rate, Sentiment score, KOSPI200 |
| 1D CNN          | 13.10 | 11.30 | CPI, Interest, Exchange rate, Sentiment score, KOSPI200 |
| Transformer     | 13.83 | 10.37 | Interest, Exchange rate, Sentiment score, KOSPI200 |  

- 등락을 0, 1로 마킹하였을 때 결과

| Model      | Accuracy | Precision | Recall | F1 Score |
|-------------|----------|-----------|--------|----------|
| Prophet (감성 지수 X)     | 0.47     | 0.48      | 0.49   | 0.49     |
| Prophet (감성 지수 O)     | 0.49     | 0.51      | 0.51   | 0.51     |
| 1D CNN (감성 지수 X)     | 0.46     | 0.49      | 0.37   | 0.42     |
| 1D CNN (감성 지수 O)      | 0.59     | 0.62      | 0.57   | 0.6      |
| Transformer (감성 지수 X) | 0.51     | 0.53      | 0.62   | 0.57     |  
| Transformer (감성 지수 O) | 0.67     | 0.69      | 0.68   | 0.69     |


- Transformer 모델의 경우 감성 지수를 추가하였을 경우 유의미한 성능 향상 및 변곡점을 더 잘 찾아냄을 볼 수 있음
<img width="321" alt="image" src="https://github.com/choims12/portfolio/assets/118867938/3e43a98e-d256-492b-a327-4598d29ad3dc">

  
  
### 배운 점   
- 직접 주제를 선정하고 데이터를 생성하는 과정에서 유의미한 데이터를 뽑아내기가 매우 어려움
- 목적에 맞는 데이터 선정 및 수집, 변수 생성, 모델 구축, 결과 도출 까지의 과정 모두가 매우 중요
 
> [발표 자료](https://github.com/kimphysicsman/MyLittelTrip_backend), [소스 코드](https://github.com/kimphysicsman/MyLittelTrip_backend)  

<br />



## 4. 👮‍♀️ 자금세탁·금융사기 의심거래 탐지 모델 개발
### 사기 계좌 탐지 모델 설계 _(서울대학교 빅데이터 핀테크 전문가 과정 6기, IBK 기업은행 캡스톤 프로젝트)_
 - 핵심 역할 : 데이터 분석 후 설명 변수 설정, 그래프 데이터로 변환, GNN 모델링

 ### 프로젝트 개요  
 - 목적 : 기존의 Rule 기반 자금세탁 및 금융사기 의심거래 탐지 방법의 한계 극복을 위해 사기계좌와 정상계좌의 관계적 특성과 패턴을 파악할 수 있는 네트워크 분석 기반 모형 개발

 - 데이터 : 암호화된 IBK 기업은행 내의 거래내역
   - 데이터 형태 : 각각 14000개, 16000개의 사기 신고 계좌, 정상 계좌를 기준으로 2번까지 거래 내역을 수집
   - Node Feature : 각 계좌로의 출/입금 횟수, 계좌 내 현금성 거래 여부, 활성화 기간
   - Edge Feature : 총 거래 금액, 총 거래 건수, 현금 거래 금액, 거래 지속 기간
   - Graph Label : 사기, 정상 여부 (0, 1)
  
 - 데이터 처리
   - 결측치 처리 : 거래 계좌 명 혹은 적요에 결측치들이 많았고, 간편결제의 경우 추적이 되지 않아 많은 양의 결측치 발생
   - 파생 변수 생성 : Raw Data 내에 많은 Feature들에 대해 이를 이해하고 의미 내포 여부 판단 및 파생 변수 생성에 오랜 기간 소요
   - 데이터 샘플링 : 정상 계좌들에 대한 데이터의 경우 사기 계좌와 비슷한 분포로 추출

 - 모델링
  - DGL Library를 통해 데이터를 그래프 데이터로 변형
  - 많은 GNN 모델 중 계좌 자체의 특성(Node Feature), 계좌 간 거래의 특성(Edge Feature) 모두 사용하는 모델 탐색
  - 다양한 정보들이 있기 때문에 특정 정보에 집중이 가능한 Attention 개념을 가진 GAT 모델 중 Edge에도 Attention을 적용하는 Edge GAT 최종 선정
    
![image](https://github.com/choims12/portfolio/assets/118867938/88626d42-24b9-4405-b56e-fd3ac50fc1dc)


   
- 사용한 모델
   - Edge GAT
   - 하이퍼 파라미터 최적화 : Optuna
  
   
### 프로젝트 결과 
| Model          | Accuracy | Recall | F1 Score |
|----------------|----------|--------|----------|
|Edge GAT           | 0.84     | 0.86   | 0.78      |

  
  
### 배운 점   
- Raw Data에서 Feature들을 선별함에 있어 명확한 기준이 필요함
- Model에 적용할 수 있도록 데이터를 변형하는 과정에서 정보 손실이 일어나지 않아야 함
- 정제된 Data가 아닌 현실에서 발생하는 Data는 매우 방대함, 어떤 목적인지 명확히 파악 후 해당 목적에 어떤 데이터가 필요할까, 어떻게 추출할까에 대한 고민이 매우 중요함
 
> [발표 자료](https://github.com/kimphysicsman/MyLittelTrip_backend), [소스 코드](https://github.com/kimphysicsman/MyLittelTrip_backend), [관련 자료](https://www.notion.so/87da1df105e14fb78e55da1e0e86d9f6?pvs=4)  

<br />

## 5. 📊 해외 및 국내 주식 상관관계 분석
### 해외 및 국내 주식 상관관계 분석을 통한 포트폴리오 구성 모델 설계 _(2023 NH 투자증권 빅데이터 경진대회 예선 및 본선)_
 - 핵심 역할 : 데이터 크롤링 및 변수 생성, 그래프 데이터화, GNN 모델링

 ### 프로젝트 개요  
 - 목적 : 해외 및 국내 주식 상관관계 분석을 통한 투자 아이디어 기획
 - ➡️ 수익률이 상위 25% 안에 드는지 여부로 그래프 라벨링을 통해 오를 확률이 높은 종목들로 포트폴리오를 구성하면 어떨까?

 - 데이터 : NH 투자증권 제공 데이터 및 블룸버그 데이터
   - 비밀 유지 서약으로 데이터에 대한 자세한 데이터 구조 설명 불가
  
 - 데이터 처리
   - 크롤링한 국내 주식 데이터와 제공 데이터를 기반으로 그래프 데이터 형성
   - 각 종목을 Node로, 종목 간 다양한 변수를 Edge로 사용
   - 제공받은 모든 데이터를 최대한 사용하고자 노력
   - Seed가 되는 종목의 데이터 종료일 기준 1주일 뒤 수익률이 상위 25%에 드는지 여부로 Graph Labeling
    
- 사용한 모델
   - Edge GAT
   - 하이퍼 파라미터 최적화 : Optuna
  
   
### 프로젝트 결과 
| Model          | Accuracy | Recall | F1 Score |
|----------------|----------|--------|----------|
|Edge GAT           | 0.56     | 0.52   | 0.37      |

  
  
### 배운 점   
- 모든 변수들을 사용하는 것이 좋은 것이 아님, 데이터를 선별함에 있어 도메인 지식이 매우 중요함
- Model을 위해 데이터를 구성하고 선별하는 것 보다, 해당 데이터를 분석하고 의미를 도출하는 과정에서 어떤 모델이 필요하겠다는 접근 방법이 올바름
  

<br />
<br />
<br />

# 감사합니다 🙇‍♂️
