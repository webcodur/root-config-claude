# Agents (커스텀 서브에이전트)

## 개요

`agents/` 디렉토리에 정의된 에이전트는 `Task` 도구에서 `subagent_type` 파라미터로 호출할 수 있다. 각 에이전트는 특정 역할에 특화된 지시문과 도구 권한을 가진다.

---

## 현재 파일 목록

```
agents/
├── backend.md      # 백엔드 개발자
├── frontend.md     # 프론트엔드 개발자
├── designer.md     # 디자이너
└── planner.md      # 기획자
```

---

## 파일 형식

```markdown
---
name: 에이전트 표시 이름
description: 에이전트 설명 (Task 도구 목록에 표시)
tools: [사용 가능한 도구 목록]
---

# 에이전트 지시문

(역할, 원칙, 작업 방식 등 상세 정의)
```

### 프론트매터 필드

| 필드 | 필수 | 설명 |
|------|------|------|
| `name` | O | 에이전트 이름 |
| `description` | O | 역할 설명 |
| `tools` | O | 사용 가능한 도구 배열 |

### 사용 가능한 도구

`Read`, `Write`, `Edit`, `Glob`, `Grep`, `Bash`, `WebFetch`, `WebSearch`, `NotebookEdit`, `Task`

---

## 새 에이전트 추가 방법

1. `agents/` 디렉토리에 `에이전트명.md` 파일 생성
2. 프론트매터에 `name`, `description`, `tools` 정의
3. 본문에 역할, 원칙, 작업 방식 상세 기술
4. Claude Code 재시작 후 Task 도구에서 사용 가능
