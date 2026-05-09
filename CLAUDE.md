# 라이트맵 Lightmap — 영상/사진 포트폴리오 랜딩페이지

## 프로젝트 개요

- **회사명**: 라이트맵 (Lightmap)
- **대표**: 김성현 (Kim Seonghyeon)

영상 제작물 및 사진 촬영본을 소개하는 **포트폴리오 쇼케이스 랜딩페이지**.
클라이언트·방문자에게 작업물의 퀄리티를 직관적으로 전달하는 것이 목표.

### 현재 상태 (Snapshot)

- **현재 단계**: 1단계 기획 — Stitch 1차 산출물 검증·갭 분석 완료, 데스크탑 뷰 재생성 대기
- **GitHub**: https://github.com/seonglight/20260509 (main 브랜치)
- **배포**: Vercel (vercel.json 구성 완료, GitHub 연동 시 자동 배포)
- **현재 노출 화면**: `index.html` = Stitch 1차 결과물(모바일 전용, Tailwind CDN 기반) — 시각 검증용
- **시작일**: 2026-05-09

## 작업 진행 단계

모든 작업은 아래 4단계를 순서대로 거친다. 단계를 건너뛰거나 역순으로 진행하지 않는다.

### 1단계 — 기획
- 목적·타겟 사용자·핵심 메시지 정의
- 섹션 구성 및 콘텐츠 목록 확정
- 참고 레퍼런스 수집
- **완료 기준**: 페이지 구성과 콘텐츠 범위가 텍스트로 확정됨

### 2단계 — 설계
- **Stitch**로 섹션별 UI 디자인 생성 (프롬프트는 `01_기획/design-planning.md` 참고)
- Stitch 결과물 기반으로 색상·타이포·간격 등 디자인 토큰 확정
- 디렉토리 구조 및 파일 명세 확정
- **완료 기준**: Stitch 결과물과 디자인 토큰이 문서로 정리됨

### 3단계 — 개발
- 기획·설계 문서를 기준으로 HTML → CSS → JS 순서로 구현
- 섹션 단위로 구현 후 브라우저에서 바로 확인
- 미완성 상태로 다음 섹션 넘어가지 않기
- **완료 기준**: 모든 섹션이 브라우저에서 정상 렌더링됨

### 4단계 — 테스트
- 반응형 확인: 모바일(360px) / 태블릿(768px) / 데스크탑(1280px+)
- Lighthouse 점수 확인 (Performance ≥ 90 목표)
- 링크·폼·영상 재생 동작 확인
- **완료 기준**: 주요 기기에서 결함 없이 동작 확인됨

---

## 기술 스택

- **언어**: HTML5, CSS3, Vanilla JavaScript (ES6+)
- **빌드 도구 없음**: 번들러·프레임워크 사용 안 함. 브라우저에서 바로 열 수 있어야 함.
- **폰트**: 시스템 폰트 우선 → 필요 시 Google Fonts (최대 1–2종)
- **아이콘**: SVG 인라인 또는 단일 sprite 파일

## 디렉토리 구조

```
/
├── index.html          # 진입점
├── style.css           # 전역 스타일
├── main.js             # 전역 스크립트
├── assets/
│   ├── images/         # 사진 원본·최적화본 (.jpg, .webp)
│   ├── videos/         # 영상 원본·썸네일 (.mp4, .jpg)
│   └── icons/          # SVG 아이콘
├── 01_기획/            # 기획 문서, Stitch 결과물 (배포 제외)
├── vercel.json         # Vercel 배포 설정
├── .vercelignore       # 배포 제외 파일 목록
├── .gitignore
└── CLAUDE.md
```

## 배포 (Vercel)

정적 사이트로 Vercel에 배포한다. 빌드 단계 없음.

### 최초 배포
```bash
# 옵션 A — Vercel CLI
npx vercel              # 로그인 후 프로젝트 연결
npx vercel --prod       # 프로덕션 배포

# 옵션 B — Git 연동 (권장)
# 1) git init && git remote add origin <repo>
# 2) git push
# 3) vercel.com 대시보드에서 Import Project
```

### 정책
- `.vercelignore`에 등록된 항목(기획 문서, zip 등)은 배포에서 제외
- `vercel.json`이 보안 헤더와 캐시 정책을 관리
- `assets/`, `*.css`, `*.js`, `*.woff2`는 1년 immutable 캐시
- `index.html`은 캐시 비활성 (must-revalidate)
- `cleanUrls: true` — `/about.html` → `/about`

## 페이지 구성 (섹션 순서)

1. **Hero** — 대표 영상 또는 이미지 풀스크린, 타이틀·슬로건
2. **Works / Gallery** — 카테고리 필터(영상/사진) + 그리드 레이아웃
3. **About** — 작업자/팀 소개, 장비·스타일 한 줄 소개
4. **Contact** — 이메일·SNS 링크, 간단한 문의 폼(선택)

## 코딩 규칙

### HTML
- 시맨틱 태그 사용 (`<header>`, `<main>`, `<section>`, `<article>`, `<footer>`)
- 이미지: `loading="lazy"`, `alt` 필수, `<picture>` + WebP 소스 제공
- 영상: `<video>` 또는 YouTube/Vimeo iframe (`loading="lazy"`)

### CSS
- CSS 커스텀 프로퍼티(변수)로 색상·간격 관리
  ```css
  :root {
    --color-bg: #0a0a0a;
    --color-text: #f0f0f0;
    --color-accent: #e8c97a;   /* 포인트 컬러: 추후 확정 */
    --gap-section: clamp(4rem, 10vw, 8rem);
  }
  ```
- 모바일 퍼스트: `min-width` 미디어 쿼리
- 애니메이션: `prefers-reduced-motion` 미디어 쿼리 존중
- Grid / Flexbox 사용; float 금지

### JavaScript
- `document.querySelector` 기반, jQuery 사용 안 함
- `IntersectionObserver`로 스크롤 진입 애니메이션
- 영상 갤러리: 라이트박스 직접 구현 (외부 라이브러리 최소화)
- 폼 유효성 검사: 브라우저 기본 API 우선

## 디자인 방향

- **무드**: 다크 배경, 여백 넉넉, 미니멀
- **타이포**: 한글 제목 + 영문 서브타이틀 혼용
- **미디어 우선**: 텍스트보다 이미지·영상이 주인공
- **반응형**: 모바일(360px) / 태블릿(768px) / 데스크탑(1280px+) 모두 지원

## 미디어 처리 지침

- 이미지: 원본 jpg → WebP 변환본도 함께 제공 (`<picture>` 태그)
- 영상 소스: 로컬 mp4 · YouTube · Vimeo 모두 조건부 지원 (추후 결정)
- 썸네일: 영상 첫 프레임 또는 별도 jpg 파일
- 용량: 히어로 이미지 < 500KB, 갤러리 썸네일 < 100KB 목표

## 성능 목표

- Lighthouse Performance ≥ 90
- CLS < 0.1 (이미지·영상에 width/height 명시)
- LCP < 2.5s (히어로 이미지 preload 적용)

## 하지 말아야 할 것

- React, Vue, Angular 등 프레임워크 도입 금지
- npm 패키지·번들러 도입 금지 (CDN 링크도 최소화)
- 불필요한 주석, 빈 파일, 보일러플레이트 생성 금지
- 인라인 `style=""` 남용 금지 — CSS 파일에서 관리

---

## 프로젝트 진행 이력

> 향후 세션에서 컨텍스트를 빠르게 회복하기 위한 작업 로그.
> 새 작업이 끝날 때마다 항목을 추가한다.

### 2026-05-09 — 프로젝트 초기 셋업

**1단계 기획 작업**
- CLAUDE.md 초안 작성: 프로젝트 개요·기술 스택·페이지 구성·코딩 규칙
- 4단계 워크플로우 정립: 기획 → 설계 → 개발 → 테스트
- 브랜드 정보 확정: 라이트맵 (Lightmap), 대표 김성현 (Kim Seonghyeon)
- 디자인 도구로 **Stitch** 채택
- `01_기획/design-planning.md` 작성: 브랜드 정의, 디자인 방향, 섹션 구성, Stitch 프롬프트(Hero·Works·About·Contact·Navigation)

**Stitch 1차 산출물 갭 분석**
- 사용자가 Stitch에서 `stitch_lightmap_portfolio_landing_page.zip` 생성 → `01_기획/stitch-results/`에 압축 해제
- `01_기획/gap-analysis.md` 작성 — 기획 의도 vs Stitch 결과 비교
- **Critical 격차 3건**:
  - G1: 데스크탑 레이아웃 부재 (모바일 전용으로만 출력됨)
  - G2: About 섹션이 50/50 two-column이 아닌 단일 컬럼
  - G3: Tailwind CDN 의존 (순수 HTML/CSS 정책 위반)
- **Critical 대응**:
  - `design-planning.md`에 [데스크탑 전용] 1440px 프롬프트 추가 (G1+G2 동시 해결용, 50/50 명시 강제)
  - Stitch HTML 코드 처리 정책 명시 — 시각 참조용으로만 사용, 3단계 개발에서 순수 CSS로 재작성

**Vercel 배포 구성**
- `vercel.json`: 보안 헤더 4종, 캐시 정책(assets 1년 immutable, index.html must-revalidate), cleanUrls
- `.gitignore`: `.DS_Store`, `*.zip`, `.env`, `.vercel`
- `.vercelignore`: `01_기획/`, `CLAUDE.md`, `*.zip` 등 배포 제외
- 초기 `index.html`은 Coming Soon 플레이스홀더 + 자체 `style.css`/`main.js`로 셋업
- 사용자 요청에 따라 `index.html`을 **Stitch 산출물(`code.html`)로 교체**, `style.css`/`main.js` 삭제 (Stitch HTML이 Tailwind CDN으로 자체 스타일 처리)
- vercel.json 1차 배포 오류 수정: 잘못된 path-to-regexp 패턴 `/(.*\.(css|js|woff2))` → 확장자별 3개 규칙으로 분리

**GitHub 연동**
- 저장소: https://github.com/seonglight/20260509
- `gh` CLI 직접 다운로드 설치 (Homebrew 미설치 환경) → `~/bin/gh` (v2.92.0), `.zshrc`에 PATH 추가
- `gh auth login` 인증 완료, `git push -u origin main` 성공
- 커밋 2개: 초기 커밋 + vercel.json 패턴 수정

### 핵심 결정 사항 (Decision Log)

| 결정 | 근거 | 영향 범위 |
|------|------|-----------|
| 순수 HTML/CSS/JS 스택 (프레임워크 X) | 가벼운 배포, 직접 통제 | 전체 |
| 디자인 도구로 Stitch 채택 | AI 기반 빠른 시안 | 2단계 설계 |
| Stitch HTML은 시각 참조용 — 코드 직접 사용 X | Tailwind CDN 의존 회피 | 3단계 개발 |
| 골드 컬러 단일화 `#e8c97a` | Stitch가 3종 변종 생성 — 단순화 필요 | 2단계 설계, 3단계 개발 |
| Bebas Neue + Hanken Grotesk 폰트 추가 채택 | 시네마틱 무드 강화 (기획안 1쌍 → 3종) | 2단계 설계 |
| Vercel 정적 배포 + GitHub 자동 연동 | 빌드 단계 없는 단순 워크플로우 | 운영 |

### 미해결 / 결정 보류 (Open Items)

- [ ] **데스크탑 Stitch 재생성** — `design-planning.md`의 [데스크탑 전용] 프롬프트로 1440px 뷰 만들기
- [ ] **Footer 범위 결정** — Stitch가 추가한 PROCESS / TEAM / LEGAL 링크 유지 여부 (해당 페이지 추가? 한 줄 푸터로 축소?)
- [ ] **이미지·영상 자산 수집** — 현재 모두 Stitch placeholder URL. Hero 1점, Works 6점(영상 3+사진 3), About portrait 1점 필요
- [ ] **카테고리 라벨 확정** — COMMERCIAL / DOCUMENTARY / MUSIC VIDEO 등
- [ ] **사용자 git identity 설정** — 현재 커밋이 hostname 기반으로 등록됨 (`gimseonghyeons-MacBook-Pro.local`). 필요 시 `git config --global user.email/user.name` 설정

### 다음 작업 후보

1. 데스크탑 Stitch 재생성 (Critical G1+G2 최종 해결)
2. Stitch 데스크탑 결과 → `02_설계/design-tokens.md`로 토큰 추출
3. Vercel 첫 배포 URL 확인 → 모바일 화면 실기기 검증
4. 자산 수집 시작 (사용자 작업물 정리)

---

## 작업 기록 규칙

새 작업을 끝낼 때마다 위 **프로젝트 진행 이력** 섹션 최상단(가장 최근 날짜)에 항목을 추가한다.

- 날짜는 `YYYY-MM-DD` 형식
- 항목은 **무엇을 했는가**보다 **왜 결정했는가**·**어떤 산출물이 생겼는가** 중심
- 결정이 변경되면 "Decision Log"에 새 행 추가 (기존 행 수정 X)
- 미해결 항목은 "Open Items"에 체크박스로 등록, 해결되면 체크 후 이력에 옮김
