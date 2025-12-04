# projects/

## 개요

프로젝트별 대화 기록을 저장하는 디렉토리이다. 각 프로젝트 경로를 해시하여 하위 폴더로 분리 저장한다.

## 위치

```
~/.claude/projects/
```

## 구조

```
projects/
├── {project-path-hash-1}/
│   ├── history.jsonl
│   └── ...
├── {project-path-hash-2}/
│   ├── history.jsonl
│   └── ...
└── ...
```

## 내용

- 프로젝트별 대화 기록
- 프로젝트별 컨텍스트 정보

## 주의

- 용량이 빠르게 증가한다
- 프로젝트가 많을수록 폴더 수 증가
- `.gitignore`에 포함되어 Git에 추적되지 않는다

## 삭제

```bash
# 전체 삭제
rm -rf ~/.claude/projects/

# 특정 프로젝트만 삭제 (해시값 확인 필요)
rm -rf ~/.claude/projects/{hash}/
```

삭제해도 Claude Code 동작에 영향 없다. 해당 프로젝트의 이전 대화 컨텍스트만 사라진다.
