# .gitignore 설정

## 개요

`.gitignore` 파일은 Git 버전 관리에서 제외할 파일과 폴더를 정의한다. 민감 정보, 임시 파일, 대용량 캐시 등을 제외하여 저장소를 깔끔하게 유지한다.

---

## 현재 설정

```gitignore
# ===========================================
# Claude Code - .gitignore
# ===========================================

# 자격 증명 및 민감 정보
.credentials.json
*.key
*.pem
*.secret

# 세션/캐시 데이터
history.jsonl
statsig/

# IDE 락 파일
ide/*.lock

# 디버그 로그
debug/

# 임시 파일
shell-snapshots/
file-history/

# 프로젝트별 대화 기록 (용량이 크므로 제외 권장)
projects/

# TODO 상태 파일
todos/

# OS 생성 파일
.DS_Store
Thumbs.db

# 플랜 파일 (선택적 - 필요시 주석 해제)
# plans/
```

---

## 항목별 설명

### 민감 정보

| 패턴 | 설명 | 제외 이유 |
|------|------|----------|
| `.credentials.json` | API 키, 인증 토큰 | 보안 |
| `*.key` | 개인 키 파일 | 보안 |
| `*.pem` | 인증서 파일 | 보안 |
| `*.secret` | 비밀 정보 파일 | 보안 |

### 세션/캐시

| 패턴 | 설명 | 제외 이유 |
|------|------|----------|
| `history.jsonl` | 대화 기록 | 개인정보, 용량 |
| `statsig/` | 통계/분석 캐시 | 임시 데이터 |

### 임시 파일

| 패턴 | 설명 | 제외 이유 |
|------|------|----------|
| `debug/` | 디버그 로그 | 임시 데이터 |
| `shell-snapshots/` | 셸 상태 스냅샷 | 임시 데이터 |
| `file-history/` | 파일 변경 이력 | 임시 데이터 |
| `ide/*.lock` | IDE 락 파일 | 임시 데이터 |

### 대용량 데이터

| 패턴 | 설명 | 제외 이유 |
|------|------|----------|
| `projects/` | 프로젝트별 대화 기록 | 용량 |
| `todos/` | TODO 상태 파일 | 세션별 데이터 |

### OS 생성 파일

| 패턴 | 설명 | 제외 이유 |
|------|------|----------|
| `.DS_Store` | macOS 폴더 메타데이터 | 불필요 |
| `Thumbs.db` | Windows 썸네일 캐시 | 불필요 |

---

## 선택적 제외

### plans/ 폴더

```gitignore
# 플랜 파일 (선택적 - 필요시 주석 해제)
# plans/
```

플랜 파일은 기본적으로 Git에 포함된다. 플랜 내용을 공유하지 않으려면 주석을 해제한다.

### 설명/ 폴더

현재 `.gitignore`에 포함되어 있지 않다. 문서를 Git에 포함하려면 그대로 두고, 제외하려면 추가한다:

```gitignore
설명/
```

---

## 커스터마이징

### 추가 제외 예시

```gitignore
# 특정 에이전트 제외
agents/experimental.md

# 특정 명령어 제외
commands/internal-*.md

# 백업 파일
*.bak
*.backup
```

### 예외 처리 (제외에서 다시 포함)

```gitignore
# 모든 .json 제외
*.json

# 단, settings.json은 포함
!settings.json
```

---

## 주의사항

1. **`.credentials.json`은 절대 커밋하지 않는다** - API 키 유출 위험
2. **`history.jsonl`은 개인정보를 포함할 수 있다** - 대화 내용이 기록됨
3. **`projects/`는 용량이 빠르게 증가한다** - 정기적 정리 권장
