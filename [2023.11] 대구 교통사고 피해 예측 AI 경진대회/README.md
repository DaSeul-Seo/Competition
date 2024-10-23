### 대구 교통사고 피해 예측 AI 경진대회
[대구 교통사고 피해 예측 AI 경진대회](https://dacon.io/competitions/official/236193/overview/description)

#### 시공간 정보로부터 사고위험도(ECLO) 예측 AI 모델 개발
- 교통사고의 원인을 규명하고 사고율을 낮추기 위해, 시공간 정보로부터 사고위험도(ECLO)를 예측하는 AI 알고리즘 개발
- 주최 / 주관 / 운영
    - 주최: 산업통상자원부, 대구광역시
    - 주관: 한국자동차연구원, 대구디지털혁신진흥원
    - 운영: 데이콘  
- 사용 가능한 외부데이터 채널
    - [대구 빅데이터활용센터](https://dipbigdata.kr/) (전체 데이터셋 활용을 위해서는 직접 대구 빅데이터활용센터 방문)
    - [한국자동차연구원 자동차데이터 포털](https://bigdata-car.kr/)
    - [공공데이터포털](https://www.data.go.kr/index.do) (2023.11.20 추가)
    - 단, 해당 출처 이외의 출처를 가지는 외부데이터는 사용 금지

### 🗓️ 일정
#### 2023.11.15 ~ 2023.12.11

### 🛠 분석 환경
- OS
    - Windows10
- 언어 / Tool
    - Python / Colab

### 📚 방법
1. 각 데이터 삭제 및 새로운 컬럼 추가
2. Voting을 통한 최종 결과값 선정
    - Soft Voting : 클래스 당 예측 확률(predict_proba의 리턴값)을 모든 모델로부터 받아와서, 해당 클래스 당 예측 확률 값을 평균 내어 가장 높은 확률을 갖는 클래스로 최종 예측을 하는 것

</br>
<details>
<summary>📚 파일 설명</summary>

0. DG_EDA
    - 주소 시, 군, 구 나누기
    - 각 컬럼 value_counts() 확인
    - 날짜, 시간정보 생성
    - 위치 정보 생성 (도시, 구, 군)
    - 도로형태 정보 추출
        > ex) '단일로 - 기타' </br>
        > 도로형태1 : 단일로 </br>
        > 도로형태2 : 기타 

1. DG_Analysis_V0
    - 원본 데이터
        - 결측치 처리
        - EDA 컬럼분류 사용
    - Model
        - Decision Tree Regressor
        - Decision Tree Classifier
    - 부스팅
        - XGBoost
        - Light GBM
        - Catboost
        - RandomForest
    - Encoder
        - Label Encoder

2. DG_Analysis_V1 & DG_Analysis_V2
    - DG_Analysis_V0에서 Voting 적용
    - 부스팅 Parameter 수정
    - kfold 확인

3. DG_Analysis_V3
    - 추가 정보 확인
        - '노면상태'와 '기상상태' 별 사고 발생 건수
        - '노면상태'와 '기상상태' 별 전체 사고 건수
        - 요일 사고 건수
        - 시간대 별 사고 건수
            - 0-6시, 6-12시, 12-18시, 18-24시
        - 주말/평일과 시간대에 따른 사고 발생 비율 계산
    - Encoder
        - OneHotEncoder
    - Model X
    - 부스팅 Parameter 수정
    - Voting

4. DG_Analysis_V4
    - 최종 제출 파일
        - ['기상상태', '사고유형', '연', '월', 'holiday', '동', '도로형태1', '도로형태2', '시간대']
        - Encoder
            - Label Encoder
        - 부스팅
            - XGBoost
            - Light GBM
            - Catboost

</details>
