# debug/

## 개요

Claude Code의 디버그 로그를 저장하는 디렉토리이다. 문제 진단 시 참고할 수 있다.

## 위치

```
~/.claude/debug/
```

## 내용

- 에러 로그
- 도구 실행 로그
- 성능 측정 데이터
- 내부 상태 정보

## 용도

- Claude Code 오류 발생 시 원인 분석
- Anthropic 지원팀에 로그 제출
- 성능 문제 진단

## 주의

- 민감한 정보가 포함될 수 있다
- `.gitignore`에 포함되어 Git에 추적되지 않는다

## 삭제

```bash
rm -rf ~/.claude/debug/
```

삭제해도 Claude Code 동작에 영향 없다.
