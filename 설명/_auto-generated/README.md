# 자동 생성 파일/폴더

## 개요

Claude Code가 자동으로 생성하고 관리하는 파일 및 폴더들이다. 사용자가 직접 수정할 필요 없으며, `.gitignore`에서 제외된다.

## 목록

| 항목 | 설명 | 문서 |
|------|------|------|
| `.credentials.json` | 인증 정보 | [credentials.md](credentials.md) |
| `history.jsonl` | 전역 대화 기록 | [history.md](history.md) |
| `projects/` | 프로젝트별 대화 기록 | [projects.md](projects.md) |
| `todos/` | TODO 상태 파일 | [todos.md](todos.md) |
| `debug/` | 디버그 로그 | [debug.md](debug.md) |
| `ide/` | IDE 연동 데이터 | [ide.md](ide.md) |
| `statsig/` | 통계/분석 캐시 | [statsig.md](statsig.md) |
| `shell-snapshots/` | 셸 상태 스냅샷 | [shell-snapshots.md](shell-snapshots.md) |
| `file-history/` | 파일 변경 이력 | [file-history.md](file-history.md) |

## 정리 방법

디스크 공간 확보 또는 초기화가 필요한 경우:

```bash
# 대화 기록 삭제
rm ~/.claude/history.jsonl
rm -rf ~/.claude/projects/

# 캐시 삭제
rm -rf ~/.claude/statsig/
rm -rf ~/.claude/debug/

# 임시 파일 삭제
rm -rf ~/.claude/shell-snapshots/
rm -rf ~/.claude/file-history/
rm -rf ~/.claude/todos/
```

**주의:** `.credentials.json` 삭제 시 재인증 필요.
