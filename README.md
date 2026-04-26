# VOC 기반 Cartier 리스크 탐지 · 확산 모니터링 시스템 구축

## 프로젝트 개요
네이버 명품 커뮤니티 '시크먼트'의 까르띠에 관련 게시글을 분석하여
브랜드 리스크를 조기에 탐지하는 시스템을 구축했습니다.

- 분석 기간: 2025년 1월 ~ 8월
- 데이터: 시크먼트 게시글 11,969개

## 담당 역할

**팀 프로젝트**
- 프로젝트 기획 및 주제 선정 (리스크 분석 프레임워크, BERT 방법론 선정)
- 댓글 리스크 탐지 모델(KcBERT) 구축 및 성능 최적화
- Risk Score × Exposure Score 기반 9등급 매트릭스 설계
- Tableau 대시보드 제작
- 데이터 기반 인사이트 도출 및 대응 전략 제안 · 최종 발표

**단독 고도화** (팀 결과 한계 확인 후 진행)
- Active Learning 기반 BERT 브랜드 분류 모델 재학습
- 리스크 이진 분류 파이프라인 재설계 (Precision 8.6%p 향상)
- Rule-based + BERTopic 리스크 카테고리 분류
- Figma 기반 대시보드 레이아웃 설계 + Tableau 대시보드 고도화

## 주요 작업 내용

### 1. BERT 기반 브랜드 분류 고도화
- 600개 초기 라벨링 → Active Learning으로 228개 추가 학습
- Accuracy 0.95 / Macro F1 0.85 달성

### 2. 리스크 이진 분류
- 게시글/댓글 각각 BERT 모델로 분류
- Precision 향상을 목표로 Threshold 최적화
- 게시글 Precision +8.6%p 향상

### 3. 리스크 카테고리 분류
- Rule-based 대분류 (품질/운영/평판/정책)
- BERTopic 세부 분류 (응대불만, 웨이팅, 기스우려 등 8개 토픽)

### 4. 리스크 지표 설계 및 9등급 분류
- Risk Score = (0.5 × 리스크확률) + (0.3 × 감성강도) + (0.2 × 키워드점수)
- Exposure Score = 리스크댓글비율 + 좋아요수 + 조회수
- Risk Score × Exposure Score 기반 HH~LL 9등급 분류
- 전체 1,589개 중 집중 모니터링 대상 404개로 압축 → 운영 효율 4배 향상

### 5. 인사이트 및 대시보드
- Topic Evolution으로 가격 인상 전후 리스크 토픽 변화 분석
- Figma 기반 대시보드 레이아웃 설계 + Tableau 대시보드 2종 제작

## 사용 기술
Python / pandas / BERT (KcBERT) / BERTopic / Active Learning
/ Matplotlib / Seaborn / Tableau / Figma

## 파일 구조
```
├── 게시글_리스크_이진분류.ipynb   # KcBERT 파인튜닝, Active Learning, Threshold 최적화
├── 댓글_리스크_이진분류.ipynb     # KcBERT 파인튜닝, Threshold 최적화
├── 리스크_카테고리_분류.ipynb     # Rule-based 대분류 + BERTopic 세부 토픽 분류
└── topic_evolution.ipynb          # 월별 토픽 변화 시각화, 인사이트 도출
```

## 참고
- 원본 데이터는 보안상 미포함
- 브랜드 필터링(1차 까르띠에 게시글 추출) 및 Risk/Exposure Score 계산은
  팀 프로젝트 결과물 기반
- 게시글·댓글 리스크 이진분류 모델은 단독 고도화 작업
