---
name: nextjs-page
description: Next.js 페이지 생성 시 pages/views 분리 구조 적용. 페이지 생성, 라우팅 설정, 새 화면 추가 요청 시 자동 활성화.
allowed-tools: Read, Write, Edit, Glob, Grep
---

# Next.js Page 생성 Skill

## 개요

Next.js 페이지 생성 시 pages/views 분리 구조를 자동 적용한다.

## 디렉토리 구조

```
src/
├── pages/           # 라우팅만 담당
│   └── user/
│       └── [id].tsx
└── views/           # 실제 UI 구현
    └── user/
        └── UserDetailView.tsx
```

## 활성화 조건

다음 요청 시 자동 활성화:
- 페이지 생성/추가
- 라우팅 설정
- 새 화면 만들기
- Next.js 페이지 작업

## 규칙

### pages 파일

- 라우팅 + View 연결만 담당
- 비즈니스 로직 금지
- 최소한의 코드만 작성

```tsx
import { UserDetailView } from '@/views/user/UserDetailView';

export default function UserDetailPage() {
  return <UserDetailView />;
}
```

### views 파일

- 실제 UI 구현
- 컴포넌트 조합
- 상태 관리
- 데이터 페칭

```tsx
export const UserDetailView = () => {
  // 실제 구현
  return (
    <div>
      {/* UI 구현 */}
    </div>
  );
};
```

## 네이밍 규칙

| 위치 | 파일명 | 컴포넌트명 |
|------|--------|-----------|
| pages | `[id].tsx` | `UserDetailPage` |
| views | `UserDetailView.tsx` | `UserDetailView` |

## 작업 순서

1. pages 디렉토리에 라우팅 파일 생성
2. views 디렉토리에 동일 구조로 View 파일 생성
3. pages에서 View import하여 연결
4. View에서 실제 UI 구현
