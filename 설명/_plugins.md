# plugins/ 디렉토리

## 개요

`plugins/` 디렉토리는 Claude Code의 플러그인 및 외부 연동 설정을 저장한다.

## 디렉토리 구조

```
plugins/
├── config.json    # 플러그인 설정 파일
└── repos/         # 플러그인 저장소 (자동 생성)
```

---

## config.json

플러그인 저장소 및 설정을 관리하는 JSON 파일이다.

### 현재 설정

```json
{
  "repositories": {}
}
```

### 설정 옵션

| 키 | 타입 | 설명 |
|----|------|------|
| `repositories` | object | 외부 플러그인 저장소 URL 맵핑 |

### 저장소 추가 예시

```json
{
  "repositories": {
    "my-plugins": "https://github.com/user/claude-plugins",
    "company-tools": "https://internal.company.com/claude-plugins"
  }
}
```

---

## MCP 서버 연동

Claude Code는 MCP (Model Context Protocol) 서버와 연동할 수 있다. MCP 설정은 별도 파일에서 관리된다.

### MCP 설정 위치

- 전역: `~/.claude/mcp.json`
- 프로젝트: `.claude/mcp.json`

### MCP 설정 예시

```json
{
  "mcpServers": {
    "database": {
      "command": "npx",
      "args": ["-y", "@modelcontextprotocol/server-postgres"],
      "env": {
        "DATABASE_URL": "postgresql://..."
      }
    },
    "filesystem": {
      "command": "npx",
      "args": ["-y", "@modelcontextprotocol/server-filesystem", "/path/to/dir"]
    }
  }
}
```

---

## repos/ 디렉토리

플러그인 저장소에서 다운로드한 파일들이 저장되는 디렉토리이다. Claude Code가 자동으로 관리하므로 직접 수정할 필요 없다.

---

## 참고

플러그인 기능은 Claude Code 버전에 따라 다를 수 있다. 최신 기능은 공식 문서를 참고한다.
