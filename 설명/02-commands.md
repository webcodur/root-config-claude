# Commands (슬래시 명령어)

## 개요

`commands/` 디렉토리에 정의된 파일은 `/파일명` 형식의 슬래시 명령어로 사용할 수 있다. 자주 사용하는 작업을 명령어로 등록하여 빠르게 실행한다.

---

## 현재 파일 목록

```
commands/
├── fix.md         # /fix - 버그/이슈 수정
├── test.md        # /test - 테스트 코드 생성
├── explain.md     # /explain - 코드/개념 설명
├── doc.md         # /doc - 코드 문서화
├── refactor.md    # /refactor - 리팩토링 제안
└── review.md      # /review - 코드 리뷰
```

---

## 파일 형식

```markdown
---
description: 명령어 설명 (자동완성 목록에 표시)
allowed-tools: 사용 가능한 도구 (쉼표 구분)
argument-hint: "<인자 힌트>" (사용법 안내)
---

실행할 프롬프트 내용
$ARGUMENTS 변수로 사용자 입력 인자 참조
```

### 프론트매터 필드

| 필드 | 필수 | 설명 |
|------|------|------|
| `description` | O | 명령어 설명 |
| `allowed-tools` | X | 사용 가능한 도구 제한 |
| `argument-hint` | X | 인자 힌트 표시 |

### 변수

| 변수 | 설명 |
|------|------|
| `$ARGUMENTS` | 사용자가 명령어 뒤에 입력한 인자 전체 |

---

## 새 명령어 추가 방법

1. `commands/` 디렉토리에 `명령어명.md` 파일 생성
2. 프론트매터에 `description` 필수 작성
3. 필요시 `allowed-tools`, `argument-hint` 추가
4. 본문에 실행할 프롬프트 작성 (`$ARGUMENTS`로 인자 참조)
5. 저장 후 즉시 `/명령어명`으로 사용 가능
