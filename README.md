# forecast_public_bike_demand_project
따릉이 수요량 예측 프로젝트

# 소개
서울시 공공자전거 서비스인 따릉이는 시민들의 교통·레저 수단으로 활발히 이용되고 있으며, 수요 예측을 통해 효율적인 자전거 재배치 전략 수립이 절실한 상황입니다.
본 프로젝트는 '통계적 기계학습' 수업의 프로젝트로 진행되었으며, 2022년 서울시 따릉이 데이터를 기반으로 시간대별·지역별 수요 예측 모델을 개발해 자전거의 부족/과잉 상태를 사전에 예측하고 재배치 전략 수립에 활용될 수 있도록 설계되었습니다.


# 요약
서울시 공공자전거 대여소 수요량 예측 프로젝트

### 1. 프로젝트 개요

- **프로젝트명**: 서울시 공공자전거 대여소 수요량 예측
- **진행 기간**: 2023.03 ~ 2023.05
- **역할**: 데이터 수집 및 전처리, 탐색적 데이터 분석(EDA), 모델링
- **목적**:
  - 서울시 공공자전거 '따릉이'의 대여소별 수요 예측을 통해 효율적인 자전거 재분배 및 운영 개선
  - 장소별, 시간대별 수요 패턴을 분석하여 자전거 거치율 최적화 및 이용자 만족도 향상

### 2. 데이터 수집 및 전처리

- **데이터 출처**:
  - [서울시 공공자전거 대여이력 정보 (2022년 1월~12월)](https://data.seoul.go.kr/dataList/OA-15182/F/1/datasetView.do)
  - [서울시 공공자전거 이용정보(시간대별)](https://data.seoul.go.kr/dataList/OA-15245/F/1/datasetView.do)
  - [서울특별시_시간별 (초)미세먼지](https://www.data.go.kr/data/15089266/fileData.do)
  - [따릉이 대여소 위치(폐쇄 포함)](https://github.com/vuski/SeoulBikeStationLocation/tree/main)
  - [서울시 공공자전거 대여소 정보](https://data.seoul.go.kr/dataList/OA-13252/F/1/datasetView.do)
  - 외부 데이터: [서울시 시간대별 날씨 정보는 외부 크롤링을 통해 추가 수집](https://freemeteo.co.uk/weather/seoul/history/daily-history/?gid=1835848&language=english&country=united-kingdom&date=2022-06-05)
 
    
- [**전처리 과정**:](https://github.com/na02string/forecast-public-bike-demand-project/blob/main/1_data_preparing.ipynb)
  - 날짜 및 시간 정보를 활용한 시간대별 데이터 정리
  - 날씨 및 미세먼지 데이터를 대여 이력 데이터와 병합
  - 날씨 데이터를 특정 기준에 따라 범주화(discomfort, windforce, 미세먼지, 초미세먼지 등)
  - 결측치 및 이상치 처리
  - datetime 변환 및 시간 관련 특성(hour, month, dayofweek 등) 추출
 ![image](https://github.com/user-attachments/assets/fe040f5e-3186-4a0c-9473-02e170492dae)



### [3. 탐색적 데이터 분석 (EDA)](https://github.com/na02string/forecast-public-bike-demand-project/blob/main/2_preprocessing_and_EDA.ipynb)

- **이용자 특성 분석**:
  - 성별 및 연령대별 이용 패턴 파악
  - ![image](https://github.com/user-attachments/assets/692420be-768a-4105-b6df-4f14c9ea0ce5)
    - 각 type 모두 남성(M)사용자가 가장 많음
  - 이용권 타입(일일권, 정기권, 단체권)별 사용량 분석

- **시간대별 이용 패턴**:
  - 계절별, 요일별, 시간대별 대여량 변화 추이 분석
  - 출퇴근 시간대 및 주말 이용량 패턴 식별

- **환경 요인과의 관계 분석**:
  - 기온, 강수량, 바람 세기, 불쾌지수 등 날씨 요인과 대여량의 상관관계 분석
  - 미세먼지 및 초미세먼지 농도에 따른 이용량 변화 분석

### 4. 모델 개발 및 평가

- **모델 선택**:
  - 시계열 데이터 예측에 적합한 Recurrent Neural Networks (RNN) 계열 모델인 LSTM 모델 활용

- **모델 평가**:
  - 예측 정확도 및 성능 지표를 활용한 모델 평가
  - 모델의 일반화 능력 및 과적합 여부 확인

### 5. 결론 및 기대효과
본 프로젝트를 통해 서울시 공공자전거 '따릉이'의 운영 효율성을 개선할 수 있는 가능성을 탐색하였습니다. 데이터 기반 분석을 통해 공공 서비스 운영의 질적 향상을 위한 인사이트를 도출하였습니다.
- 시간대별 및 대여소별 수요 예측 모델을 구축하여 자전거 재배치의 효율성을 높일 가능성을 확인
- 환경 요인과 이용 패턴 간의 상관관계를 분석하여 효과적인 운영 전략 수립에 활용할 수 있는 근거 제공

# 상세 내용
[블로그](https://itdatascience.tistory.com/61)
🔗 [강서구 기준 지도 시각화 결과 보기](https://na02string.github.io/forecast-public-bike-demand-project/seoulbike_station_usage.html)
  
# 아쉬운 점
- 시간이 부족하여 모든 대여소에 대한 예측을 진행하고 최적 루트를 정립하는 것까지 하지 못한 점이 아쉽다.
- 추가적으로 사용해볼 수 있는 변수에 대해 더 고민해보지 못한 점이 아쉽다.
