# Claude Code 전역 설정

Claude Code CLI의 전역 설정 템플릿이다. 클론하여 `~/.claude` 디렉토리에 배치하면 모든 프로젝트에 적용된다.

## 설치 방법

```bash
# 기존 ~/.claude 백업 (있는 경우)
mv ~/.claude ~/.claude.backup

# 저장소 클론
git clone https://github.com/your-username/claude-config.git ~/.claude
```

## 디렉토리 구조

```
~/.claude/
├── .git/                  # Git 저장소 (버전 관리)
├── .gitignore             # Git 제외 목록
├── .credentials.json      # 인증 정보 (자동 생성, Git 제외)
│
├── CLAUDE.md              # 전역 시스템 지시문
├── settings.json          # 전역 설정 (언어, 권한)
├── README.md              # 이 파일
│
├── agents/                # 커스텀 서브에이전트 정의
│   ├── backend.md
│   ├── frontend.md
│   ├── designer.md
│   └── planner.md
│
├── commands/              # 슬래시 명령어 정의
│   ├── fix.md
│   ├── test.md
│   ├── explain.md
│   ├── doc.md
│   ├── refactor.md
│   └── review.md
│
├── skills/                # 자동 활성화 스킬 정의
│   └── nextjs-page/
│       └── SKILL.md
│
├── plans/                 # 플랜 모드 저장 파일
├── plugins/               # 플러그인 설정
│   ├── config.json
│   └── repos/
│
├── 설명/                   # 상세 문서
│   ├── 01-agents.md
│   ├── 02-commands.md
│   ├── 03-skills.md
│   ├── _settings.md
│   ├── _claude-md.md
│   ├── _plugins.md
│   ├── _plans.md
│   ├── _gitignore.md
│   ├── _git.md
│   └── _auto-generated/
│       ├── README.md
│       ├── credentials.md
│       ├── history.md
│       ├── projects.md
│       ├── todos.md
│       ├── debug.md
│       ├── ide.md
│       ├── statsig.md
│       ├── shell-snapshots.md
│       └── file-history.md
│
└── (자동 생성 - Git 제외)
    ├── history.jsonl      # 전역 대화 기록
    ├── projects/          # 프로젝트별 대화 기록
    ├── todos/             # TODO 상태 파일
    ├── debug/             # 디버그 로그
    ├── ide/               # IDE 연동 데이터
    ├── statsig/           # 통계/분석 캐시
    ├── shell-snapshots/   # 셸 상태 스냅샷
    └── file-history/      # 파일 변경 이력
```

## 포함된 설정

### 전역 지시문 (CLAUDE.md)

- 코드 작성 원칙: KISS, YAGNI, DRY
- 한국어 대화, 간결한 말투
- 주니어 개발자 대상 응답

### 권한 설정 (settings.json)

모든 도구 자동 허용 (권한 프롬프트 생략)

### 커스텀 에이전트 (agents/)

| 파일 | 역할 |
|------|------|
| `backend.md` | 백엔드 개발자 |
| `frontend.md` | 프론트엔드 개발자 |
| `designer.md` | 디자이너 |
| `planner.md` | 기획자 |

### 슬래시 명령어 (commands/)

| 명령어 | 용도 |
|--------|------|
| `/fix` | 버그/이슈 수정 |
| `/test` | 테스트 코드 생성 |
| `/explain` | 코드/개념 설명 |
| `/doc` | 코드 문서화 |
| `/refactor` | 리팩토링 제안 |
| `/review` | 코드 리뷰 |

### 스킬 (skills/)

| 스킬 | 용도 |
|------|------|
| `nextjs-page` | Next.js pages/views 분리 구조 자동 적용 |

## 상세 문서

`설명/` 디렉토리 참조:

**핵심 (번호순 - 사용자 정의 항목)**
| 파일 | 내용 |
|------|------|
| `01-agents.md` | 에이전트 정의 방법 |
| `02-commands.md` | 슬래시 명령어 정의 방법 |
| `03-skills.md` | 스킬 정의 방법 |

**부가 (설정 파일)**
| 파일 | 내용 |
|------|------|
| `_settings.md` | settings.json 옵션 |
| `_claude-md.md` | CLAUDE.md 작성 가이드 |
| `_gitignore.md` | .gitignore 설정 |
| `_git.md` | Git 저장소 관리 |

**부가 (폴더)**
| 파일 | 내용 |
|------|------|
| `_plugins.md` | plugins/ 및 MCP 연동 |
| `_plans.md` | plans/ 플랜 모드 |
| `_auto-generated/` | 자동 생성 폴더 (9개 문서) |

## 커스터마이징

1. 저장소 포크
2. 필요에 맞게 수정
   - `CLAUDE.md` - 코딩 원칙, 대화 스타일
   - `settings.json` - 권한, 언어 설정
   - `agents/` - 에이전트 추가/수정
   - `commands/` - 명령어 추가/수정
   - `skills/` - 스킬 추가/수정
3. 자신의 저장소에서 클론하여 사용

## 프로젝트별 설정

프로젝트 루트에 `.claude/` 생성 시 해당 프로젝트에만 적용된다. 전역 설정을 오버라이드한다.

## 주의사항

- `.credentials.json`은 Git에 포함되지 않음 (개인 인증 정보)
- `history.jsonl`, `projects/`, `todos/` 등 자동 생성 파일은 제외됨
- 설정 변경 후 Claude Code 재시작 필요
