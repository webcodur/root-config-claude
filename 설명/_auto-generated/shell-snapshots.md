# shell-snapshots/

## 개요

셸 상태 스냅샷을 저장하는 디렉토리이다. `Bash` 도구의 백그라운드 실행 기능과 관련된다.

## 위치

```
~/.claude/shell-snapshots/
```

## 내용

- 백그라운드 셸 상태
- 실행 중인 프로세스 정보
- 출력 버퍼

## 용도

- `run_in_background` 옵션으로 실행된 명령 관리
- 백그라운드 프로세스 출력 조회 (`BashOutput` 도구)
- 프로세스 종료 (`KillShell` 도구)

## 주의

- 세션 종료 후에도 파일이 남을 수 있다
- `.gitignore`에 포함되어 Git에 추적되지 않는다

## 삭제

```bash
rm -rf ~/.claude/shell-snapshots/
```

삭제해도 Claude Code 동작에 영향 없다. 단, 실행 중인 백그라운드 프로세스 정보는 사라진다.
