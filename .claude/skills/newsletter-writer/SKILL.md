---
name: "Newsletter Writer (더배러)"
description: "더배러 뉴스레터 스타일로 초안 작성"
version: "1.0.0"
tags: [newsletter, writing, thebetter]
author: "yohankoo"
---

# Newsletter Writer - 더배러 (The Better)

구요한의 '더배러' 뉴스레터 스타일로 콘텐츠를 작성합니다.

## 톤 가이드

### 기본 원칙
- 독자에게 말을 거는 듯한 친근한 어투
- 구어체와 문어체를 적절히 섞어 사용
- 복잡한 개념을 쉽게 풀어서 설명
- 개인적 경험과 관찰을 녹여내기
- "~입니다" 대신 "~이에요", "~거든요" 등 자연스러운 어미

### 톤별 가이드
- **insight**: 핵심 인사이트를 짚어주되, 왜 이것이 중요한지 독자가 바로 와닿게
- **humor**: 위트 있는 비유, 일상적 예시로 무거운 주제도 가볍게
- **serious**: 데이터와 사례 중심, 깊이 있는 분석과 논리적 전개

## Workflow

### Step 1: 리서치
- **Input**: 주제 + 참고 URL (선택)
- **Action**: 참고 URL 수집 + WebSearch로 추가 자료 확보
- **Output**: 핵심 데이터, 통계, 인용구 정리
- **Validation**: 최소 5개 소스 확보

### Step 2: 아웃라인 작성
- **Input**: 리서치 결과
- **Action**: 뉴스레터 구조 설계
- **Output**: 섹션별 아웃라인 (오프닝, 본문 3-4개, 테이크어웨이)

### Step 3: 초안 작성
- **Input**: 아웃라인 + 리서치
- **Action**: 더배러 톤으로 1,500-2,500자 초안 작성
- **Output**: 완성된 마크다운 초안
- **Validation**: 분량 체크, 톤 일관성 확인

### Step 4: 저장
- **Input**: 초안
- **Action**: `output/newsletter/YYYY-MM-DD-draft.md`로 저장, 커밋
- **Output**: 커밋된 파일

## 뉴스레터 구조 템플릿
```markdown
# [제목]

> 🎯 [한줄 요약]

## 📌 오프닝
[독자 관심 끌기 - 질문이나 에피소드로 시작]

## 💡 [소제목 1]
[본문 - 데이터/사례 포함]

## 💡 [소제목 2]
[본문]

## 💡 [소제목 3]
[본문]

## 🔑 핵심 테이크어웨이
- Point 1
- Point 2
- Point 3

## ✍️ 에디터 노트
[개인적 의견/경험]

---
📚 **참고 자료**
- [Source 1](url)
- [Source 2](url)
```
