# VOC 기반 Cartier 리스크 분석 및 조기징후 탐색

## 프로젝트 개요
네이버 명품 커뮤니티 '시크먼트'의 까르띠에 관련 게시글을 분석하여
브랜드 리스크를 조기에 탐지하는 시스템을 구축했습니다.

- 분석 기간: 2025년 1월 ~ 8월
- 데이터: 시크먼트 게시글 11,969개

## 담당 역할
팀 프로젝트 이후 단독으로 고도화 진행

- 팀 프로젝트: 1차 까르띠에 게시글 필터링 (키워드/N-gram 기반)
- **본인 담당**: 이후 전 과정 단독 고도화

## 주요 작업 내용

### 1. BERT 기반 브랜드 분류 고도화
- 600개 초기 라벨링 → Active Learning으로 228개 추가 학습
- Accuracy 0.95 / Macro F1 0.85 달성

### 2. 리스크 이진 분류
- 게시글/댓글 각각 BERT 모델로 분류
- Precision 향상을 목표로 Threshold 최적화

### 3. 리스크 카테고리 분류
- Rule-based 대분류 (품질/운영/평판/정책)
- BERTopic 세부 분류 (응대불만, 웨이팅, 기스우려 등 8개 토픽)

### 4. 리스크 지표 설계
- Risk Score = (0.5 × 리스크확률) + (0.3 × 감성강도) + (0.2 × 키워드점수)
- Exposure Score = 리스크댓글비율 + 좋아요수 + 조회수

### 5. 9등급 리스크 매트릭스 및 대시보드
- Risk Score × Exposure Score 기반 HH~LL 9등급 분류
- 전체 1,589개 중 집중 모니터링 대상 404개로 압축 → 운영 효율 4배 향상

## 사용 기술
Python / pandas / BERT (klue/bert-base) / BERTopic / Active Learning
/ Matplotlib / Seaborn

## 파일 구조
├── 01_bert_brand_classification.ipynb   # BERT 브랜드 분류 고도화
├── 02_risk_binary_classification.ipynb  # 리스크 이진 분류
├── 03_risk_category_bertopic.ipynb      # 카테고리 분류
├── 04_risk_score_matrix.ipynb           # 리스크 지표 및 9등급 분류
└── README.md
