# todos/

## 개요

Claude Code의 TODO 상태 파일을 저장하는 디렉토리이다. `TodoWrite` 도구가 관리한다.

## 위치

```
~/.claude/todos/
```

## 구조

```
todos/
├── {session-id}-agent-{agent-id}.json
├── {session-id}-agent-{agent-id}.json
└── ...
```

## 내용

- 진행 중인 작업 목록
- 완료된 작업 기록
- 작업 상태 (pending, in_progress, completed)

## 파일 형식

```json
{
  "todos": [
    {
      "content": "작업 내용",
      "status": "completed",
      "activeForm": "작업 중 표시 텍스트"
    }
  ]
}
```

## 주의

- 세션/에이전트별로 파일이 생성된다
- 오래된 파일이 누적될 수 있다
- `.gitignore`에 포함되어 Git에 추적되지 않는다

## 삭제

```bash
rm -rf ~/.claude/todos/
```

삭제해도 Claude Code 동작에 영향 없다. 현재 세션의 TODO 목록만 초기화된다.
