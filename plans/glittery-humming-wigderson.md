# Feel&Note UI 통합 및 Stats 페이지 고도화 계획

## 작업 개요

1. **Archive UI 컴포넌트화** - Archive 페이지의 UI를 재사용 가능한 컴포넌트로 분리하여 Dashboard에서도 동일하게 사용
2. **Stats 페이지 고도화** - 기획서 기반 상세 통계 및 인포그래픽 구현

---

## 작업 1: Archive UI 컴포넌트화

### 생성할 컴포넌트

| 컴포넌트 | 경로 | 용도 |
|---------|------|------|
| `SectionHeader` | `src/components/ui/SectionHeader.tsx` | 제목 + 아이콘 + 링크 |
| `ContentGrid` | `src/components/ui/ContentGrid.tsx` | 그리드 레이아웃 래퍼 |

### SectionHeader Props
```typescript
interface SectionHeaderProps {
  title: string;
  icon?: React.ReactNode;
  linkText?: string;
  linkHref?: string;
}
```

### ContentGrid Props
```typescript
interface ContentGridProps {
  children: React.ReactNode;
  minWidth?: number;  // 기본 160px
  gap?: number;       // 기본 20px
}
```

### 수정할 파일

1. **`src/components/ui/SectionHeader.tsx`** - 신규 생성
2. **`src/components/ui/ContentGrid.tsx`** - 신규 생성
3. **`src/components/ui/index.ts`** - export 추가
4. **`src/components/features/dashboard/ContinueReading.tsx`** - 새 컴포넌트 적용
5. **`src/app/(main)/archive/page.tsx`** - 새 컴포넌트 적용

---

## 작업 2: Stats 페이지 고도화

### 설치할 패키지
```bash
pnpm add recharts
```

### Mock 데이터 확장 (`src/lib/mock-data.ts`)

```typescript
export const USER_DETAILED_STATS = {
  // 요약 정보
  summary: {
    totalContents: 152,
    totalReviews: 80,
    totalNotes: 45,
    totalCreations: 12,
    activityScore: 1530,
    achievementBonus: 350,
  },

  // 카테고리 분포 (도넛 차트)
  categoryDistribution: [
    { name: "도서", value: 45, color: "#7c4dff" },
    { name: "영화", value: 52, color: "#f59e0b" },
    { name: "드라마", value: 35, color: "#10b981" },
    { name: "게임", value: 20, color: "#ec4899" },
  ],

  // 영향력 정보
  influence: {
    friends: 24,
    followers: 156,
    totalInfluence: 2900,
    rank: "나무",
    nextRank: "숲",
    progress: 58,
  },

  // 월별 활동 히트맵 (365일)
  activityHeatmap: [...],

  // 칭호 현황
  titles: [
    { name: "첫 발자국", rarity: "일반", earned: true },
    { name: "독서광", rarity: "고급", earned: true },
    { name: "창작자", rarity: "영웅", earned: false, progress: 65 },
  ],

  // 장르 선호도 (레이더 차트)
  genrePreferences: [
    { genre: "SF", score: 85 },
    { genre: "판타지", score: 72 },
    ...
  ],

  // 월별 트렌드 (라인 차트)
  monthlyTrend: [
    { month: "1월", contents: 8, reviews: 5, notes: 3 },
    ...
  ],

  // 최근 활동
  recentActivities: [
    { type: "review", title: "인셉션", time: "2시간 전", points: 5 },
    ...
  ],
};
```

### 생성할 Stats 컴포넌트

| 컴포넌트 | 설명 | 차트 타입 |
|---------|------|----------|
| `StatsSummaryCards` | 6개 요약 카드 (2x3 그리드) | - |
| `CategoryDonutChart` | 카테고리별 콘텐츠 비율 | Recharts PieChart |
| `InfluenceGauge` | 영향력 등급 게이지 | Recharts RadialBarChart |
| `ActivityHeatmap` | GitHub 스타일 연간 활동 | CSS Grid (커스텀) |
| `TitleProgressCard` | 칭호 획득/진행 현황 | - |
| `GenreRadarChart` | 장르 선호도 | Recharts RadarChart |
| `MonthlyTrendChart` | 월별 활동 추이 | Recharts LineChart |
| `ActivityTimeline` | 최근 활동 목록 | - |

### Stats 페이지 레이아웃

```
┌─────────────────────────────────────────────────┐
│ 통계 (헤더)                                      │
├─────────────────────────────────────────────────┤
│ [요약카드][요약카드][요약카드]                      │
│ [요약카드][요약카드][요약카드]                      │
├───────────────────────┬─────────────────────────┤
│ 카테고리 분포 (도넛)    │ 영향력 & 등급 (게이지)    │
├───────────────────────┴─────────────────────────┤
│ 연간 활동 히트맵 (전체 너비)                       │
├───────────────────────┬─────────────────────────┤
│ 칭호 현황              │ 최근 활동                │
├───────────────────────┼─────────────────────────┤
│ 장르 선호도 (레이더)    │ 월별 트렌드 (라인)        │
└───────────────────────┴─────────────────────────┘
```

### 파일 구조

```
src/components/features/stats/
├── index.ts
├── StatsSummaryCards.tsx
├── CategoryDonutChart.tsx
├── InfluenceGauge.tsx
├── ActivityHeatmap.tsx
├── TitleProgressCard.tsx
├── GenreRadarChart.tsx
├── MonthlyTrendChart.tsx
└── ActivityTimeline.tsx
```

---

## 구현 순서

### Phase 1: UI 컴포넌트 통합
1. `SectionHeader.tsx` 생성
2. `ContentGrid.tsx` 생성
3. `ui/index.ts` 업데이트
4. `ContinueReading.tsx` 리팩토링
5. `archive/page.tsx` 리팩토링

### Phase 2: Stats 기반 작업
1. `pnpm add recharts` 설치
2. `mock-data.ts`에 `USER_DETAILED_STATS` 추가
3. `src/components/features/stats/` 폴더 생성

### Phase 3: Stats 컴포넌트 구현
1. `StatsSummaryCards.tsx`
2. `CategoryDonutChart.tsx`
3. `InfluenceGauge.tsx`
4. `ActivityHeatmap.tsx`
5. `TitleProgressCard.tsx`
6. `GenreRadarChart.tsx`
7. `MonthlyTrendChart.tsx`
8. `ActivityTimeline.tsx`

### Phase 4: Stats 페이지 통합
1. `stats/page.tsx` 전체 리팩토링
2. 반응형 레이아웃 적용

---

## 수정 대상 파일 목록

### 신규 생성
- `src/components/ui/SectionHeader.tsx`
- `src/components/ui/ContentGrid.tsx`
- `src/components/features/stats/index.ts`
- `src/components/features/stats/StatsSummaryCards.tsx`
- `src/components/features/stats/CategoryDonutChart.tsx`
- `src/components/features/stats/InfluenceGauge.tsx`
- `src/components/features/stats/ActivityHeatmap.tsx`
- `src/components/features/stats/TitleProgressCard.tsx`
- `src/components/features/stats/GenreRadarChart.tsx`
- `src/components/features/stats/MonthlyTrendChart.tsx`
- `src/components/features/stats/ActivityTimeline.tsx`

### 수정
- `src/components/ui/index.ts`
- `src/lib/mock-data.ts`
- `src/components/features/dashboard/ContinueReading.tsx`
- `src/app/(main)/archive/page.tsx`
- `src/app/(main)/stats/page.tsx`
