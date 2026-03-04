---
name: "Learning Content Generator"
description: "대학원/기업교육 수준의 학습 콘텐츠 자동 생성"
version: "1.0.0"
tags: [education, learning, quiz, curriculum]
author: "yohankoo"
---

# Learning Content Generator

CHA 대학원 강의 및 CMDS 워크숍을 위한 교육 콘텐츠를 자동 생성합니다.

## 대상 수준
- CHA 대학원 AI융합학과 대학원생
- CMDS 워크숍 참가자 (지식 노동자)
- 기업 교육 대상자 (중간관리자급)

## Workflow

### Step 1: 주제 선정
- **Input**: 사용자 지정 주제 또는 자동 선택
- **Action**: 자동 선택 시 최신 트렌드 기반 주제 결정
- **Output**: 확정 주제 + 키워드

### Step 2: 리서치
- **Input**: 확정 주제
- **Action**: WebSearch로 최신 자료, 논문, 도구 조사
- **Output**: 핵심 개념 5-7개, 사례 3-5개, 도구 3-5개
- **Validation**: 신뢰할 수 있는 소스 (학술지, 공식 문서)

### Step 3: 학습 목표 설계
- **Input**: 리서치 결과 + 난이도
- **Action**: Bloom's Taxonomy 기반 학습 목표 3-5개 작성
- **Output**: 측정 가능한 학습 목표 리스트

### Step 4: 콘텐츠 작성
- **Input**: 학습 목표 + 리서치
- **Action**: 핵심 개념 → 심화 학습 → 실습 과제 순서로 작성
- **Output**: 완성된 학습 자료
- **Validation**: 학습 목표와 콘텐츠 정합성 체크

### Step 5: 퀴즈 생성
- **Input**: 학습 콘텐츠
- **Action**: 객관식 10문제 + 참/거짓 5문제 + 주관식 3문제
- **Output**: 퀴즈 + 정답지 (해설 포함)
- **Validation**: 난이도 분포 (쉬움 30%, 보통 50%, 어려움 20%)

### Step 6: 저장
- **Input**: 완성된 콘텐츠
- **Action**: 저장 및 커밋
- **Output**: `output/learning/YYYY-MM-DD-{topic}.md`

## 콘텐츠 품질 기준
- [ ] Bloom's Taxonomy 기반 학습 목표
- [ ] 최소 5개 핵심 개념 (정의 + 예시)
- [ ] 실제 사례/케이스 스터디 포함
- [ ] 3개 이상 실습 과제 (단계별 난이도)
- [ ] 18문제 이상 퀴즈 (해설 포함)
- [ ] 한국어 작성 + 영어 전문용어 보존
- [ ] 실제 URL 참고자료 5개 이상
