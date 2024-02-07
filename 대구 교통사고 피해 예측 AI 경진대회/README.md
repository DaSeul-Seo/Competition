### 대구 교통사고 피해 예측 AI 경진대회
[대구 교통사고 피해 예측 AI 경진대회](https://dacon.io/competitions/official/236193/overview/description)

- 주제
    - 시공간 정보로부터 사고위험도(ECLO) 예측 AI 모델 개발
    - 사고 발생 시간, 공간 등의 정보를 활용하여 사고위험도(ECLO)를 예측하는 AI 알고리즘 개발
- 일정
    - 기간 : 2023년 11월 15일 ~ 2023년 12월 11일 10:00
    - 팀 병합 마감 : 2023년 12월 04일 23:59
        - 5명
    - 대회 종료 : 2023년 12월 11일 10:00
    - 코드 및 PPT 제출 : 2023년 12월 11일 10:00 ~ 2023년 12월 13일 23:59
        - private score 상위 10팀
    - 코드 검증 : 2023년 12월 14일 00:00 ~ 2023년 12월 18일 23:59
    - 최종 결과 발표 : 2023년 12월 19일 10:00
- 평가기준 : RMSLE(Root Mean Squared Logarithmic Error) of ECLO
    - ECLO: 인명피해 심각도(Equivalent Casualty Loss Only)
    - ECLO = 사망자수 * 10 + 중상자수 * 5 + 경상자수 * 3 + 부상자수 * 1
    - 다른 유형의 사고들을 부상자 기준으로 환산하여 사고의 심각 정도와 위험도를 표현하는 방법
    - 부상자: 교통사고로 인하여 5일 미만의 치료를 요하는 부상을 입은 경우
    
- 사용 가능한 외부데이터 채널
    - [대구 빅데이터활용센터](https://dipbigdata.kr/) (전체 데이터셋 활용을 위해서는 직접 대구 빅데이터활용센터 방문)
    - [한국자동차연구원 자동차데이터 포털](https://bigdata-car.kr/)
    - [공공데이터포털](https://www.data.go.kr/index.do) (2023.11.20 추가)
    - 단, 해당 출처 이외의 출처를 가지는 외부데이터는 사용 금지

### 🛠 분석 환경
- Google Colaboratory

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
