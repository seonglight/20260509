# 라이트맵 Lightmap — 영상/사진 포트폴리오 랜딩페이지

## 프로젝트 개요

- **회사명**: 라이트맵 (Lightmap)
- **대표**: 김성현 (Kim Seonghyeon)

영상 제작물 및 사진 촬영본을 소개하는 **포트폴리오 쇼케이스 랜딩페이지**.
클라이언트·방문자에게 작업물의 퀄리티를 직관적으로 전달하는 것이 목표.

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
