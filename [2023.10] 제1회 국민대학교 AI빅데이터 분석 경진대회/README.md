### 제 1회 국민대학교 AI빅데이터 분석 경진대회 개요
[제1회 국민대학교 AI빅데이터 분석 경진대회](https://dacon.io/competitions/official/236170/overview/description)

#### 채용공고 추천 알고리즘 개발
- 구직자 입장
    - 자신의 이력과 경력에 맞춤화된 채용 공고를 추천받을 수 있다.
- 구인기업 입장
    - 공고에 적합한 인재를 미리 선별하는 도구로 활용 가능하다.
- 기대효과
    - 구직자 관련 데이터, 채용공고 관련 데이터, 지원 히스토리를 활용해 지원자의 적성에 맞는 채용공고에 지원하여 직무만족도를 높이고 구인기업은 직종에 맞는 핵심인재를 선발할 수 있다.
- 주최 / 주관
    - 주최 : 국민대학교 경영대학원, LINC+ 사업단
    - 주관 : 국민대학교 경영대학, 국민대학교 경영대학원 AI빅데이터전공/디지털마케팅전공
    - 운영 : 데이콘
    - 후원 : (주)스카우트

### 🗓️ 일정
#### 2023.10.16 ~ 2023.11.13

### 🛠 분석 환경
- OS
    - Windows10
- 언어 / Tool
    - Python / Colab

### 📚 방법
1. 각 데이터 삭제 및 새로운 컬럼 추가
2. Nevative Sampling 방식
3. 결과에서 데이터 빼기

</br>
<details>
<summary>📚 파일 설명</summary>

0. EDA
    - V0 ~ V3
        - 키 컬럼들을 기준으로 합치기
        - 결측치 치환, feature 생성, Scaling, Encoding
        - 공고 기준으로 구직자 데이터를 groupby -> 공고 feature
1. Analysis_V0
    - 원본 데이터 확인
    - 원본 데이터 결측치 처리만 진행
    - cosine_similarity를 통해 결과 도출 (Base Model 사용)

2. Analysis_V1
    - Negative Sampling
        - 데이터 셋을 이진분류가 가능하도록 변환
        - sklearn을 통해 train / test 데이터 셋 생성
    - 학습
        - LightGBM
        - roc_auc 지표 사용
    - 예측
        - 생성된 모델에 모든 구직자 X 모든 공고 조합을 input 하여 예측활률 구하기
        - 사전 지원 내역을하고 각 구직자 별 지원확률리 높은 공고 5개를 output

3. Analysis_V2 & Analysis_V3
     - Negative Sampling
        - 데이터 셋을 이진분류가 가능하도록 변환
        - sklearn을 통해 train / test 데이터 셋 생성
    - 학습
        - XGBoost
        - roc_auc 지표 사용
    - One-hot encoding 가능하도록 전처리
    - 모든 구직자 X 특정공고 조합을 사용하여 정확도 상승, 속도 개선

4. Analysis_V4
    - 지원 히스토리에서 무의미한 지원을 제거한 상태로 유사도를 계산하는 방법
    - 어떤 조건으로 히스토리를 삭제할 것인지 EDA
    - 데이터셋에서 아예 제거된 구직자 존재 => Random으로 복구

5. Analysis_V5
    - 최종 제출 파일
    - Analysis_V4에서 필터링 조건 탐색 및 적용
</details>
