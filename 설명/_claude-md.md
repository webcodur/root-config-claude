# CLAUDE.md 작성 가이드

## 개요

`CLAUDE.md`는 Claude Code가 모든 대화에서 따라야 할 시스템 지시문을 정의하는 마크다운 파일이다. 전역(`~/.claude/CLAUDE.md`) 또는 프로젝트별(`.claude/CLAUDE.md`)로 설정할 수 있다.

## 위치 및 우선순위

| 위치 | 적용 범위 |
|------|----------|
| `~/.claude/CLAUDE.md` | 모든 프로젝트에 적용 |
| `프로젝트/.claude/CLAUDE.md` | 해당 프로젝트에만 적용 |

**우선순위:** 프로젝트 > 전역 (프로젝트 설정이 전역 설정을 오버라이드)

---

## 현재 전역 설정

```markdown
# 전역 설정

## 코드 작성 원칙

- **KISS** - Keep It Simple Stupid!
- **YAGNI** - You Ain't Gonna Need It
- **DRY** - Do not Repeat Yourself

## 대화

- 한국어로 대화
- 간결하고 권위적인 말투 사용 (있다, 이다, 하다, 했다, 한다 등)
- 사용자를 주니어 개발자로 가정하고 응답
```

---

## 작성 가능한 항목

### 1. 대화 스타일

```markdown
## 대화
- 한국어로 대화
- 간결한 말투
- 불필요한 인사말 생략
```

### 2. 코딩 원칙

```markdown
## 코딩 원칙
- KISS, YAGNI, DRY 준수
- 함수는 20줄 이하
- 클래스보다 함수 선호
```

### 3. 기술 스택 지정

```markdown
## 기술 스택
- React + TypeScript
- Tailwind CSS
- Zustand (상태관리)
- 절대 jQuery 사용 금지
```

### 4. 코드 스타일

```markdown
## 코드 스타일
- 세미콜론 사용
- 작은따옴표 사용
- 들여쓰기 2칸
- trailing comma 사용
```

### 5. 금지 사항

```markdown
## 금지
- console.log 남기지 않기
- any 타입 사용 금지
- 주석 없는 복잡한 로직 금지
```

### 6. 선호 패턴

```markdown
## 선호 패턴
- early return
- 삼항 연산자 > if/else
- 객체 맵핑 > switch
- async/await > .then()
```

### 7. 파일 구조

```markdown
## 파일 구조
- 컴포넌트: src/components/
- 훅: src/hooks/
- 유틸: src/utils/
- 타입: src/types/
```

### 8. 커밋 규칙

```markdown
## 커밋 메시지
- feat: 새 기능
- fix: 버그 수정
- refactor: 리팩토링
- docs: 문서
- 한국어로 작성
```

---

## 팁

### 명확하고 구체적으로

```markdown
# 나쁜 예
- 깔끔하게 코드 작성

# 좋은 예
- 함수는 단일 책임 원칙 준수
- 함수명은 동사로 시작 (get, set, create, update, delete)
- 변수명은 의미 있게 (i, j 대신 index, count)
```

### 우선순위 표시

```markdown
## 필수 (반드시 지켜야 함)
- TypeScript strict 모드
- ESLint 에러 0개

## 권장 (가능하면 지킴)
- 함수 20줄 이하
- 파일 200줄 이하
```

### 예외 상황 명시

```markdown
## 원칙
- console.log 사용 금지

## 예외
- 디버깅 목적으로 임시 사용 가능 (커밋 전 삭제 필수)
```

---

## 프로젝트별 CLAUDE.md 예시

```markdown
# 프로젝트: E-commerce Admin

## 기술 스택
- Next.js 14 (App Router)
- TypeScript
- Prisma + PostgreSQL
- NextAuth.js

## 디렉토리 구조
- app/: 라우팅
- components/: UI 컴포넌트
- lib/: 유틸리티
- prisma/: DB 스키마

## API 규칙
- /api/v1/ prefix 사용
- 모든 응답은 { success, data, message } 형식

## 특이사항
- 레거시 jQuery 코드 있음 (점진적 마이그레이션 중)
- IE11 지원 불필요
```
