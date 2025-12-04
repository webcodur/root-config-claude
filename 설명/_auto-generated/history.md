# history.jsonl

## 개요

전역 대화 기록을 저장하는 파일이다. JSON Lines 형식으로 한 줄에 하나의 JSON 객체가 저장된다.

## 위치

```
~/.claude/history.jsonl
```

## 내용

- 사용자 입력
- Claude 응답
- 도구 호출 기록
- 타임스탬프

## 형식

```jsonl
{"type":"user","content":"...","timestamp":"..."}
{"type":"assistant","content":"...","timestamp":"..."}
{"type":"tool_use","name":"...","input":{...},"timestamp":"..."}
```

## 주의

- 개인정보가 포함될 수 있다
- 용량이 빠르게 증가할 수 있다
- `.gitignore`에 포함되어 Git에 추적되지 않는다

## 삭제

```bash
rm ~/.claude/history.jsonl
```

삭제해도 Claude Code 동작에 영향 없다. 이전 대화 컨텍스트만 사라진다.
