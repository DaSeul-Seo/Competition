### 도배 하자 질의 응답 처리 : 한솔데코 시즌2 AI 경진대회
[한솔데코 시즌2 AI 경진대회](https://dacon.io/competitions/official/236216/overview/description)

#### 도배 하자 질의 응답 AI 모델 개발
- 도배 하자 도메인에 대한 질의를 바탕으로 지능적인 응답을 생성하는 AI 모델 개발
- 주최 / 주관
    - 주최: 한솔데코
    - 주관: 데이콘

### 🛠 분석 환경
- OS
    - Windows10
- 언어 / Tool
    - Python / Colab
    
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