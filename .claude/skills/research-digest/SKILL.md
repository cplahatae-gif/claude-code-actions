---
name: "Research Digest Generator"
description: "AI/Education/KM 분야 일일 리서치 다이제스트 생성"
version: "1.0.0"
tags: [research, AI, education, knowledge-management]
author: "yohankoo"
---

# Research Digest Generator

AI, 교육, 지식경영 분야의 최신 연구/뉴스를 수집하여 구조화된 마크다운 다이제스트를 생성합니다.

## Workflow

### Step 1: 이전 다이제스트 확인
- **Input**: `output/research-digest/` 폴더
- **Action**: 최근 3일간 다이제스트 읽어 중복 방지
- **Output**: 제외할 URL/제목 리스트

### Step 2: 웹 리서치
- **Input**: 키워드 리스트 (AI education, KM, generative AI, HRD, PKM)
- **Action**: WebSearch로 각 키워드별 5-8개 결과 수집
- **Output**: 원시 검색 결과 (제목, URL, 스니펫)
- **Validation**: 최소 20개 결과 확보

### Step 3: 콘텐츠 상세 수집
- **Input**: 상위 10-15개 URL
- **Action**: fetch MCP로 각 페이지 본문 수집
- **Output**: 상세 콘텐츠 (제목, 본문 요약, 날짜, 저자)
- **Validation**: 7일 이내 콘텐츠만 유지

### Step 4: 분류 및 태깅
- **Input**: 수집된 콘텐츠
- **Action**: 카테고리 분류 (Research/Industry/Tools) + 태그 부여
- **Output**: 분류된 항목 리스트

### Step 5: 다이제스트 작성
- **Input**: 분류된 항목
- **Action**: 각 항목 2-3문장 한국어 요약 + Executive Summary 작성
- **Output**: 완성된 마크다운 다이제스트
- **Validation**: 최소 10개 항목, 모든 URL 유효

### Step 6: 저장 및 커밋
- **Input**: 완성된 다이제스트
- **Action**: `output/research-digest/YYYY-MM-DD.md`로 저장, git commit & push
- **Output**: 커밋된 파일
- **Validation**: git status clean

## Quality Standards
- [ ] 10개 이상 항목 포함
- [ ] 모든 URL 유효
- [ ] 7일 이내 콘텐츠만 포함
- [ ] 중복 없음 (이전 다이제스트 대비)
- [ ] 한국어 요약 + 영어 용어 보존
- [ ] Executive Summary 3-5개 bullet point
