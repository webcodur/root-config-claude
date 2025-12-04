# plans/ 디렉토리

## 개요

`plans/` 디렉토리는 Claude Code의 **플랜 모드**에서 생성된 구현 계획 파일을 저장한다.

---

## 플랜 모드란?

복잡한 작업을 수행하기 전, Claude가 먼저 계획을 수립하고 사용자 승인을 받는 모드이다.

### 활성화 조건

- 여러 파일을 수정하는 대규모 작업
- 아키텍처 결정이 필요한 작업
- 사용자가 명시적으로 계획 수립 요청

### 동작 방식

1. Claude가 작업 분석 및 계획 수립
2. `plans/` 디렉토리에 계획 파일 저장
3. 사용자에게 계획 검토 요청
4. 승인 후 구현 시작

---

## 파일 형식

### 파일명

자동 생성된 랜덤 이름을 사용한다:

```
glittery-humming-wigderson.md
dancing-purple-einstein.md
sleepy-crimson-turing.md
```

### 파일 구조

```markdown
# [작업 제목]

## 작업 개요
(전체 작업 요약)

## 상세 계획

### Phase 1: [단계명]
1. 세부 작업 1
2. 세부 작업 2

### Phase 2: [단계명]
...

## 수정 대상 파일

### 신규 생성
- `path/to/new-file.ts`
- ...

### 수정
- `path/to/existing-file.ts`
- ...

## 구현 순서
1. 첫 번째 단계
2. 두 번째 단계
...
```

---

## 현재 저장된 플랜

### glittery-humming-wigderson.md

**제목:** Feel&Note UI 통합 및 Stats 페이지 고도화 계획

**작업 개요:**
1. Archive UI 컴포넌트화 - Archive 페이지 UI를 재사용 가능한 컴포넌트로 분리
2. Stats 페이지 고도화 - 기획서 기반 상세 통계 및 인포그래픽 구현

**주요 내용:**
- `SectionHeader`, `ContentGrid` 공통 컴포넌트 생성
- Recharts 기반 차트 컴포넌트 8종 구현
- 반응형 Stats 페이지 레이아웃

**수정 대상 파일:** 16개 (신규 11개, 수정 5개)

---

## Git 관리

기본적으로 `plans/` 폴더는 Git에 포함된다. 제외하려면 `.gitignore`에 추가:

```gitignore
plans/
```

### 포함 권장 상황

- 팀 프로젝트에서 계획 공유 필요
- 작업 히스토리 추적 필요
- 코드 리뷰 시 계획 참조 필요

### 제외 권장 상황

- 개인 프로젝트
- 임시 계획만 사용
- 저장소 용량 절약 필요

---

## 정리 방법

오래된 플랜 파일 삭제:

```bash
# 특정 파일 삭제
rm ~/.claude/plans/glittery-humming-wigderson.md

# 전체 삭제
rm -rf ~/.claude/plans/*
```

---

## 참고

- 플랜 파일은 Claude가 자동 생성하며, 직접 생성할 필요 없다
- 플랜 승인 후에도 파일은 유지된다 (참조용)
- 동일 작업에 대해 새 플랜 생성 시 기존 파일은 덮어쓰지 않고 새 파일 생성
