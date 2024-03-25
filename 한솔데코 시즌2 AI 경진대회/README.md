### 도배 하자 질의 응답 처리 : 한솔데코 시즌2 AI 경진대회
[한솔데코 시즌2 AI 경진대회](https://dacon.io/competitions/official/236216/overview/description)

- 주제
    - 도배 하자 질의 응답 AI 모델 개발
    - 도배 하자 도메인에 대한 질의를 바탕으로 지능적인 응답을 생성하는 AI 모델 개발
- 일정
    - 기간 : 2024년 01월 29일 10:00 ~ 2024년 03월 11일 10:00
    - 팀 병합 마감 : 2024년 03월 04일 23:59 -> 5명
    - 대회 종료 : 2024년 03월 11일 10:00
    - 코드 및 PPT 제출 : 2024년 03월 14일 23:59
        - private score 상위 10팀
    - 코드 검증 및 2차 평가 : 2024년 03월 15일 00:00 ~ 2024년 03월 24일 23:59
    - 최종 결과 발표 : 2024년 03월 25일 10:00
- 평가기준 : Cosine Similarity
- 1일 제출 3회
- API, 외부 데이터 및 사전 학습 모델
    - 사용에 법적 제약이 없으며, 누구나 변경, 재배포할 수 있는 공개된 외부 데이터 사용 가능
    - 사용에 법적 제약이 없으며, 오픈소스로 공개된 사전 학습 모델(Pre-trained Model) 사용 가능
        - 단, Hugging Face 내 sosoai가 제공하는 모든 'hansoldeco' 관련 모델 사용 불가능
    - API를 통한 외부데이터 수집, 데이터 전처리는 가능하나, API를 통한 추론은 불가능합니다. (Ex. ChatGPT API를 통한 추론 등 불가능)
        - 반드시 언어 모델 학습의 과정이 존재해야하며, 학습된 언어 모델을 바탕으로 추론이 이루어져야합니다.

### 🛠 분석 환경
- Local
- Google Colaboratory

### 📚 방법
1. Cosine Similarity
2. RAG 시스템 활용

</br>
<details>
<summary>📚 파일 설명</summary>

1. hyul_star
    - feature & target 분리
    - 정답과 예측값의 유사도 측정

2. DG_Analysis_V1 & DG_Analysis_V2
    - 트랜스포머에서 BitsandBytesConfig를 통해 양자화 매개변수 정의
    - 경량화 모델 로드
    - RAG 시스템 결합

</details>