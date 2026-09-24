# H&M Customer Behavior Analysis
## Age-based Customer Segmentation & Active Senior Strategy

H&M 고객·상품·거래 데이터를 활용해 **연령대별 구매 행동, 채널 이용, 카테고리 및 색상 선호도**를 분석하고,  
고령화 시장에서 50대 이상 고객을 대상으로 한 상품·마케팅·서비스 전략을 제안한 팀 프로젝트입니다.

---

## Project Context

스파르타 내일배움캠프 데이터분석 10기 과정에서 진행한 **팀 기반 교육 프로젝트**입니다.

프로젝트는 H&M의 기존 핵심 고객층을 확인하는 동시에,  
고령화 시장에서 구매력을 가진 **50대 이상 고객의 행동 특성**을 분석해  
향후 고객 포트폴리오를 어떻게 확장할 수 있을지 탐색하는 것을 목표로 했습니다.

---

## Business Question

> H&M의 연령대별 고객은 **어떻게 구매하고, 어떤 채널·상품·색상을 선호하며**,  
> 50대 이상 고객을 확대하기 위해 어떤 전략을 제안할 수 있을까?

분석은 다음 네 가지 관점으로 구성했습니다.

1. 연령대별 구매 패턴
2. 연령대별 온·오프라인 채널 이용
3. 연령대별 카테고리·품목 선호
4. 연령대별 색상 선호

---

## My Contribution

이 저장소에서는 제가 수행한 **연령 기반 고객 행동 EDA와 시각화**를 중심으로 개인 기여를 확인할 수 있습니다.

### 1. Age-based Customer Segmentation

고객을 다음 연령 그룹으로 구분해 구매 행동을 비교했습니다.

- 10대
- 20대
- 30대
- 40대
- 50대 이상

연령대별로 다음 지표를 비교했습니다.

- 거래 건수
- 매출 합계
- 평균 구매 금액
- 선호 가격대

### 2. Customer Engagement Analysis

연령대별 패션 뉴스 구독 여부와 Active 여부를 분석해  
고객 참여 특성과 구매 행동을 비교했습니다.

### 3. Channel Analysis

연령대별 온라인·오프라인 매출 및 평균 구매 금액을 비교했습니다.

> 온라인 채널 데이터가 상대적으로 많이 포함되어 있어  
> 채널 비중 해석에는 **표본 편향 가능성**을 함께 고려했습니다.

### 4. Product & Preference Analysis

연령대별로 다음 항목을 비교했습니다.

- Product Group
- Garment Group
- 상위 구매 품목
- 월별 매출 추이
- 색상 선호

개인 분석 노트북은 `notebooks/jaehee_customer_analysis.ipynb`에서 확인할 수 있습니다.

---

## Data

프로젝트에서는 제공된 H&M 데이터를 사용했습니다.

### Customer Data
고객 속성 및 멤버십·패션 뉴스 관련 정보

### Article Data
상품 분류, 제품군, 색상, 카테고리 관련 정보

### Transaction Data
고객별 구매 일자, 상품, 가격, 판매 채널 정보

전처리 전 데이터 규모:

- Customers: **1,048,575 rows**
- Articles: **105,542 rows**
- Transactions: **1,048,575 rows**

고객·거래·상품 데이터를 결합한 분석 데이터는 약 **805K transaction records** 규모였습니다.

---

## Data Preprocessing

팀 전처리 과정에서는 다음 작업을 수행했습니다.

- 결측치 확인 및 보정
- 중복 행 제거
- 비정상 연령 범위 제거
- 구매일을 datetime 형식으로 변환
- 가격 로그 변환
- IQR 기반 이상치 탐지
- Z-score 기반 이상치 탐지
- IQR과 Z-score에서 동시에 이상치로 판단된 **1,698건 제거**
- 한 기준에서만 이상치로 판단된 값은 임계값으로 대체
- 상품 분류의 `Unknown` 값을 다른 상품 정보와 함께 검토해 보정
- 고객·거래·상품 데이터 병합

---

## Analysis Workflow

1. 문제 정의 및 Active Senior 타깃 설정
2. 고객·상품·거래 데이터 구조 확인
3. 결측치·중복·이상치 처리
4. 고객·거래·상품 데이터 병합
5. 연령대 파생변수 생성
6. 연령대별 구매 규모 및 가격대 분석
7. 패션 뉴스·Active 여부 분석
8. 온·오프라인 채널 비교
9. 카테고리·품목 선호 분석
10. 색상 선호 분석
11. 부서별 전략 제안

---

## Key Insights

### 1. Purchase Behavior by Age

- 현재 핵심 고객층은 **20~30대**
- 50대 이상 고객은 전체 매출 비중은 상대적으로 작지만 **평균 구매 금액이 높은 편**
- 연령대가 높아질수록 상대적으로 높은 가격대의 상품 구매 비중이 증가하는 경향을 확인

### 2. Fashion News

- 50대 이상 고객은 패션 뉴스 구독 비율이 상대적으로 높게 나타남
- 다만 50대 이상에서 패션 뉴스 구독 여부에 따른 구매 성과 차이는 크지 않음

### 3. Online vs Offline

- 20~30대는 온라인 채널 비중이 상대적으로 높고, 50대 이상은 오프라인 비중이 상대적으로 높게 나타남
- 모든 연령대에서 온라인 채널의 평균 구매 금액이 더 높게 나타남
- 단, 온라인 데이터 비중이 크기 때문에 채널 비교 결과는 표본 편향 가능성을 고려해 해석

### 4. Category Preference

- 모든 연령대에서 여성복 구매 비중이 높음
- 연령대가 높아질수록 **Ladieswear 비중이 증가**
- 50대 이상 고객은 다른 연령대보다 **Blouse 구매 비율이 상대적으로 높음**
- 전체적으로 상의·하의의 구매 비중이 높게 나타남

### 5. Color Preference

- 전반적으로 무채색과 파란색 계열 선호가 높음
- 연령대가 높아질수록 강한 원색보다 상대적으로 절제된 색상을 선호하는 경향이 나타남

---

## Strategy Recommendations

분석 결과를 바탕으로 50대 이상 고객 확대를 위한 세 가지 방향을 제안했습니다.

### MD

**시니어 선호 데이터를 활용한 상품 포트폴리오 강화**

- 50대 이상 고객의 상위 구매 품목을 반영한 상품 구성 확대
- 선호도가 높은 여성복·블라우스 중심 라인업 검토
- 높은 평균 구매 금액을 고려한 프리미엄 상품 구성 검토

### Marketing

**패션 고관여 Active Senior 유입을 위한 콘텐츠 개선**

- 시니어 고객을 위한 콘텐츠 구성
- 구독 개인화 등 신규 콘텐츠 가설 설계 및 검증

### Service / Product

**오프라인 경험을 유지하면서 온라인 유입을 촉진**

- 오프라인 시니어 추천 섹션 검토
- 온라인 이용 장벽을 낮추는 온보딩 가이드 제안

---

## Repository Files

### `notebooks/data_preprocessing.ipynb`

팀 프로젝트의 데이터 전처리 과정입니다.

주요 내용:

- 결측치 및 중복 처리
- 로그 변환
- IQR / Z-score 이상치 처리
- 데이터 병합
- 상품 분류값 보정

### `notebooks/jaehee_customer_analysis.ipynb`

제가 수행한 연령대 기반 고객 행동 EDA 및 시각화입니다.

주요 내용:

- 연령대별 매출·객단가·가격대 분석
- 패션 뉴스 / Active 분석
- 채널별 구매 행동 비교
- 상품·카테고리 선호 분석
- 월별 매출 추이
- 색상 선호 분석

### `notebooks/product_sales_analysis.ipynb`

팀 프로젝트에서 진행한 제품군 매출 및 월별 판매 패턴 분석 파일입니다.

### `report/hm_customer_analysis_presentation.pdf`

프로젝트의 문제 정의, 분석 결과 및 전략 제안을 정리한 최종 발표 자료입니다.

---

## Tools

### Data Analysis
- Python
- Pandas
- NumPy

### Preprocessing
- Scikit-learn
- Log Transformation
- IQR
- Z-score

### Visualization
- Matplotlib
- Seaborn

---

## Repository Structure

```text
hm-customer-behavior-analysis/
│
├── README.md
├── requirements.txt
│
├── notebooks/
│   ├── data_preprocessing.ipynb
│   ├── jaehee_customer_analysis.ipynb
│   └── product_sales_analysis.ipynb
│
└── report/
    └── hm_customer_analysis_presentation.pdf
```

---

## Project Type

- **Educational Team Project**
- Sparta Data Analysis Bootcamp
- Data Analysis 10th Cohort

> This repository contains team project files and highlights my age-segment customer behavior analysis.  
> Team-level preprocessing and strategy outputs are distinguished from the analysis work shown in my personal notebook.
