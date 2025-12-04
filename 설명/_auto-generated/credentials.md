# .credentials.json

## 개요

Claude Code의 인증 정보를 저장하는 파일이다.

## 위치

```
~/.claude/.credentials.json
```

## 내용

- API 키
- 인증 토큰
- 세션 정보
- 만료 시간

## 보안

- **절대 공유하지 않는다**
- **절대 Git에 커밋하지 않는다**
- `.gitignore`에 기본 포함되어 있다

## 삭제 시

파일 삭제 시 Claude Code 재시작 후 재인증이 필요하다.

```bash
rm ~/.claude/.credentials.json
```
