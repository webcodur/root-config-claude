# settings.json 설정

## 개요

`settings.json`은 Claude Code의 전역 동작을 설정하는 JSON 파일이다. 언어, 테마, 도구 권한, 환경변수 등을 정의한다.

## 전체 구조

```json
{
  "$schema": "https://json.schemastore.org/claude-code-settings.json",
  "preferences": {
    "language": "ko",
    "theme": "auto"
  },
  "permissions": {
    "allow": [],
    "deny": []
  },
  "env": {}
}
```

---

## preferences (환경 설정)

| 키 | 타입 | 설명 | 기본값 |
|----|------|------|--------|
| `language` | string | 인터페이스 언어 | `"en"` |
| `theme` | string | 테마 설정 | `"auto"` |

### language 옵션

- `"ko"` - 한국어
- `"en"` - 영어
- `"ja"` - 일본어
- 기타 언어 코드

### theme 옵션

- `"auto"` - 시스템 설정 따름
- `"dark"` - 다크 모드
- `"light"` - 라이트 모드

---

## permissions (도구 권한)

도구 사용 시 권한 확인 프롬프트를 제어한다.

### allow (자동 허용)

```json
"allow": [
  "Bash(*)",
  "Read(*)",
  "Write(*)"
]
```

### deny (차단)

```json
"deny": [
  "Bash(rm -rf *)",
  "Write(/etc/*)"
]
```

### 패턴 문법

| 패턴 | 설명 | 예시 |
|------|------|------|
| `Tool(*)` | 모든 사용 허용 | `Bash(*)` |
| `Tool(pattern)` | 특정 패턴만 | `Bash(git *)` |
| `Tool(path/*)` | 특정 경로만 | `Write(src/*)` |

### 사용 가능한 도구

| 도구 | 설명 |
|------|------|
| `Bash` | 셸 명령어 실행 |
| `Read` | 파일 읽기 |
| `Write` | 파일 생성/덮어쓰기 |
| `Edit` | 파일 수정 |
| `Glob` | 파일 패턴 검색 |
| `Grep` | 내용 검색 |
| `WebFetch` | URL 내용 가져오기 |
| `WebSearch` | 웹 검색 |
| `NotebookEdit` | Jupyter 노트북 편집 |
| `Task` | 서브에이전트 실행 |

### 현재 설정 (모든 권한 자동 허용)

```json
"permissions": {
  "allow": [
    "Bash(*)",
    "Read(*)",
    "Write(*)",
    "Edit(*)",
    "Glob(*)",
    "Grep(*)",
    "WebFetch(*)",
    "WebSearch(*)",
    "NotebookEdit(*)",
    "Task(*)"
  ],
  "deny": []
}
```

---

## env (환경 변수)

Claude Code 세션에 주입할 환경 변수를 정의한다.

```json
"env": {
  "NODE_ENV": "development",
  "API_BASE_URL": "https://api.example.com",
  "DEBUG": "true"
}
```

**주의:** 민감한 정보(API 키, 비밀번호 등)는 여기에 저장하지 않는다. `.credentials.json` 또는 시스템 환경 변수 사용 권장.

---

## 프로젝트별 설정

프로젝트 루트의 `.claude/settings.json`에서 전역 설정을 오버라이드할 수 있다.

```
my-project/.claude/settings.json
```

**우선순위:** 프로젝트 설정 > 전역 설정

프로젝트별로 다른 권한 정책이나 환경 변수를 적용할 때 유용하다.
