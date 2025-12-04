# statsig/

## 개요

Anthropic의 기능 관리 시스템(Statsig)과 연동되는 캐시 디렉토리이다.

## 위치

```
~/.claude/statsig/
```

## 내용

- 기능 플래그 (Feature flags) 캐시
- A/B 테스트 할당 정보
- 사용 통계 데이터

## 용도

- 새로운 기능의 점진적 롤아웃
- 사용자별 기능 활성화/비활성화
- 사용 패턴 분석

## 주의

- Anthropic 서버와 주기적으로 동기화된다
- `.gitignore`에 포함되어 Git에 추적되지 않는다

## 삭제

```bash
rm -rf ~/.claude/statsig/
```

삭제 시 다음 실행 때 Anthropic 서버에서 다시 가져온다. 일시적으로 기능 플래그가 기본값으로 리셋될 수 있다.
