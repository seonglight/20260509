# 라이트맵 Lightmap — 디자인 기획 및 Stitch 프롬프트

## 브랜드 정의

| 항목 | 내용 |
|------|------|
| 브랜드명 | 라이트맵 / Lightmap |
| 대표 | 김성현 / Kim Seonghyeon |
| 업종 | 영상 제작 · 사진 촬영 |
| 핵심 메시지 | 빛으로 순간을 지도처럼 기록한다 |
| 타겟 | 브랜드 촬영 의뢰 기업, 웨딩·행사 고객, 콘텐츠 제작 협업사 |

---

## 디자인 방향

### 무드
- 다크 배경 기반, 미니멀하고 시네마틱한 분위기
- 텍스트보다 이미지·영상이 압도적으로 주인공
- 고급스럽고 조용한 긴장감 (과하지 않은 모션)

### 색상 방향
- 배경: 거의 검정 (`#0a0a0a` ~ `#111111`)
- 텍스트: 오프화이트 (`#f0f0f0`)
- 포인트: 따뜻한 골드 계열 (`#e8c97a`) — Stitch 결과 보고 최종 확정
- 보조: 중간 회색 (`#555555`) — 캡션, 날짜 등

### 타이포
- 한글 제목: Noto Serif KR 또는 Pretendard (세미볼드)
- 영문 서브타이틀: Inter 또는 DM Sans (라이트~레귤러)
- 본문: 14–16px, 행간 1.7

---

## 페이지 섹션 구성

```
Hero  →  Works  →  About  →  Contact
```

| 섹션 | 역할 | 핵심 요소 |
|------|------|-----------|
| Hero | 첫인상, 브랜드 각인 | 풀스크린 영상/이미지, 브랜드명, 슬로건, 스크롤 유도 |
| Works | 작업물 쇼케이스 | 영상·사진 필터 탭, 그리드, 라이트박스 |
| About | 신뢰 형성 | 대표 소개, 장비·스타일, 작업 철학 한 줄 |
| Contact | 전환 유도 | 이메일, SNS 링크, 간단 문의 폼 |

---

## Stitch HTML 코드 처리 정책 ⚠️

Stitch가 출력한 `code.html`은 **시각 참조용**으로만 사용한다. 코드를 그대로 가져오지 않는다.

- ❌ Tailwind CDN, Material Symbols, Google Fonts 다중 로딩 그대로 사용 금지
- ❌ Material You 컬러 토큰 풀세트(surface 6단계, primary 4종 등) 그대로 채택 금지
- ✅ 레이아웃·간격·컬러 톤·타이포 위계만 참고
- ✅ 3단계 개발에서 **순수 HTML/CSS/JS**로 새로 작성
- ✅ 폰트는 Google Fonts에서 필요한 것만 선택 로딩 (`preload`, `font-display: swap`)

---

## Stitch 프롬프트

> **사용법**: 아래 프롬프트를 Stitch에 그대로 붙여넣기.
> 섹션별로 개별 생성 후 병합하거나, 전체 프롬프트로 한 번에 생성.
> 결과물은 `01_기획/stitch-results/` 폴더에 저장.

---

### [전체 페이지] Full Landing Page Prompt

```
Design a dark, cinematic portfolio landing page for "Lightmap" (라이트맵), a Korean video production and photography studio run by Kim Seonghyeon.

Overall style:
- Dark background (#0a0a0a), off-white text (#f0f0f0), warm gold accent (#e8c97a)
- Minimal, high-end, editorial feel — let visuals breathe
- Desktop-first layout, single-column scroll
- Korean + English typographic pairing (Korean heading, English subtitle)

Sections (top to bottom):
1. Hero — fullscreen dark overlay on a cinematic video/photo placeholder. Brand name "Lightmap / 라이트맵" large centered, tagline "빛으로 순간을 기록합니다" below in smaller text. Subtle scroll indicator at bottom.
2. Works — section title "Works". Two filter tabs: "영상 Video" and "사진 Photo". Below tabs: a 3-column masonry or uniform grid of dark thumbnail cards. Each card has a thin gold border on hover with a play icon overlay for video.
3. About — two-column layout: left side a large portrait photo placeholder, right side short bio text. Name "Kim Seonghyeon / 김성현", role "Director · Photographer", 2–3 lines of philosophy text in Korean.
4. Contact — centered layout. Large heading "Contact", email link, Instagram icon link, and a minimal 3-field form (이름, 이메일, 메시지) with a gold submit button.
5. Footer — single line, "© 2026 Lightmap. All rights reserved."

Typography: use a serif for Korean headings, sans-serif for body and English text.
No gradients. No bright colors. Keep whitespace generous.
```

---

### [섹션 1] Hero

```
Design a fullscreen hero section for a dark portfolio website called "Lightmap".

- Background: near-black (#0a0a0a) with a cinematic photo or video placeholder (landscape, slightly blurred or darkened overlay at 40% opacity)
- Center-aligned content:
  - Brand name in two lines: "Lightmap" in large English sans-serif (light weight, letter-spacing 0.2em), below it "라이트맵" in medium Korean serif
  - Tagline below: "빛으로 순간을 기록합니다" in small, off-white, letter-spacing 0.05em
  - 40px vertical gap between brand name and tagline
- Bottom center: a thin vertical line (60px) with a small downward chevron — scroll indicator, subtle animation implied
- No buttons, no navigation in this section
- Overall mood: cinematic, silent, premium
```

---

### [섹션 2] Works / Gallery

```
Design a portfolio gallery section for a dark photography and video studio website.

- Section heading: "Works" left-aligned, large serif font, off-white color, with "작업물" as a smaller Korean subtitle beneath it
- Filter tabs just below heading: two pill-shaped tabs — "영상  Video" and "사진  Photo". Active tab: gold (#e8c97a) text with a thin gold underline. Inactive: gray.
- Grid: 3-column uniform grid of cards. Each card:
  - Dark gray background (#1a1a1a)
  - 16:9 aspect ratio thumbnail placeholder
  - On hover: thin gold border, slight scale-up (1.02), play icon centered for video cards
  - Below thumbnail: small caption — project title in Korean (white), category tag in gray
- Minimal gap between cards (16px)
- "더 보기  Load more" button centered below grid — outlined, gold border, transparent fill
- Background: #0a0a0a
```

---

### [섹션 3] About

```
Design an about section for a dark, editorial portfolio website.

- Two-column layout (50/50), large vertical padding
- Left column: portrait photo placeholder — tall rectangle (3:4 ratio), slight warm tone overlay, no border
- Right column (vertically centered):
  - Small label: "About" in gold uppercase letters, letter-spacing 0.2em
  - Name: "Kim Seonghyeon" large, English serif font, off-white
  - Korean name: "김성현" smaller, below
  - Role line: "Director · Photographer · Lightmap" in gray, italic
  - Paragraph: 3–4 lines of Korean text as philosophy/intro placeholder
  - Two icon links at bottom: email icon and Instagram icon, gold color
- Divider: thin horizontal gold line (80px wide) between label and name
- Background: slightly lighter than hero (#111111)
```

---

### [섹션 4] Contact

```
Design a contact section for a dark, minimal portfolio website.

- Centered layout, generous padding top and bottom
- Section heading: "Contact  문의하기" — English large serif, Korean small beneath, off-white
- Short subtext: "작업 의뢰 및 협업 문의를 환영합니다." in gray, centered
- Contact form below (full-width max 560px, centered):
  - Three fields stacked: 이름 (Name), 이메일 (Email), 메시지 (Message — textarea, 4 rows)
  - Field style: no box border, only a bottom border line in dark gray; on focus, line turns gold
  - Labels: small, gray, uppercase
  - Submit button: full-width, gold background (#e8c97a), black text "보내기  Send", no border-radius (sharp corners)
- Below form: direct email "hello@lightmap.kr" as a text link in gold, and Instagram handle "@lightmap" in gray
- Background: #0a0a0a
```

---

### [데스크탑 전용] Desktop Full Page (1440px) — Critical 보완용

> Stitch 1차 결과가 모바일 전용으로만 생성되어 추가 요청. 데스크탑 그리드 + About 50/50 two-column을 명시적으로 강제한다.

```
Design a DESKTOP version (1440px wide viewport) of the Lightmap portfolio landing page. Korean video production and photography studio. Director: Kim Seonghyeon (김성현).

Style system (use exactly these — do not invent variants):
- Background: #0a0a0a primary, #111111 elevated surfaces
- Text: #e2e2e2 primary, #989080 muted
- Accent: warm gold #e8c97a — SINGLE shade only, no light/dark variants
- Border: 1px hairline #2a2a2a
- All elements 0px border-radius (sharp corners only, no rounded anything)
- Typography: Noto Serif KR for Korean serif headings, Bebas Neue for English uppercase labels (letter-spacing 0.15em), Hanken Grotesk for body
- Container max-width 1440px with 80px side margins
- 12-column grid, 24px gutters
- Section vertical gap: 160px

Layout (top to bottom):

1. NAVIGATION (fixed top, 60px height, full width)
- Left: logo "LIGHTMAP" in Bebas Neue, off-white
- Right: three text links "WORKS", "ABOUT", "CONTACT" in gray, hover gold
- Active link: gold with 1px gold underline 4px below
- NO hamburger menu on desktop — show all three links inline
- Background: transparent on top, #0a0a0a 90% opacity when scrolled

2. HERO (full viewport, 100vh)
- Full-bleed cinematic landscape photo placeholder, 40% dark overlay
- Centered content: "Lightmap / 라이트맵" large display heading (64px Noto Serif KR), tagline "빛으로 순간을 기록합니다" below in Hanken Grotesk
- Bottom center: 60px vertical hairline + "SCROLL" label in Bebas Neue

3. WORKS (3-COLUMN DESKTOP GRID — important)
- Heading "Works / 작업물" with 2px gold left-border accent
- Filter tabs below: "영상 Video" (active, gold underline) and "사진 Photo" (gray) in Bebas Neue
- 3 columns × 2 rows = 6 cards, uniform 16:9 aspect, 24px gap
- Each card: image with bottom gradient overlay, gold category label (e.g. "COMMERCIAL", "DOCUMENTARY", "MUSIC VIDEO"), white serif project title
- Hover: 1px inset gold border, slight image desaturation
- "더 보기 / Load More" outlined gold button centered below grid

4. ABOUT (50/50 TWO-COLUMN SIDE-BY-SIDE — critical, do NOT stack vertically)
- LEFT column 50%: tall portrait photo placeholder, 3:4 aspect ratio, slight grayscale, no border
- RIGHT column 50%, vertically centered:
  - Small uppercase gold label "ABOUT" (Bebas Neue, letter-spacing 0.2em)
  - 80px gold horizontal divider line below label
  - Large Korean+English name: "김성현 Kim Seonghyeon" in Noto Serif KR
  - Role line: "Director · Photographer · Lightmap" in gray italic
  - 3-4 line philosophy paragraph in Hanken Grotesk body-md
  - Two icon links at bottom: email icon and Instagram icon, both in gold #e8c97a

5. CONTACT (centered, max-width 720px)
- Heading "Contact / 문의하기" with 2px gold left-border accent
- Subtext "작업 의뢰 및 협업 문의를 환영합니다." in gray, centered
- Form: 3 fields stacked (이름 NAME, 이메일 EMAIL, 메시지 MESSAGE textarea 5 rows)
- Field style: transparent, 1px bottom border #2a2a2a, focus turns gold #e8c97a
- Submit button: full-width, solid gold background, black text "보내기 SEND"
- Below form: direct email "hello@lightmap.kr" as gold text link, Instagram "@lightmap" in gray

6. FOOTER (single line, centered)
- "© 2026 LIGHTMAP. ALL RIGHTS RESERVED." in small gray Bebas Neue label-style text
- 80px top padding from previous section

Strict rules:
- Rectilinear shapes only, no shadows, no rounded corners anywhere
- Use ONLY one gold shade #e8c97a — do not introduce variants
- Limit color tokens to 6 total (bg, bg-elevated, text, text-muted, accent, border)
```

---

### [공통] Navigation Bar (선택 적용)

```
Design a minimal fixed navigation bar for a dark portfolio website called "Lightmap".

- Position: fixed top, full width
- Background: transparent (becomes #0a0a0a at 90% opacity on scroll)
- Left: logo — "Lightmap" in small caps, off-white, letter-spacing 0.15em
- Right: three text links — "Works", "About", "Contact" — in gray, hover turns off-white
- No hamburger menu on desktop. Mobile: hamburger icon that opens a fullscreen overlay menu
- Height: 60px
- Thin 1px bottom border in very dark gray (#222) when scrolled
```

---

## Stitch 결과물 관리

- 생성된 이미지/코드는 `01_기획/stitch-results/` 폴더에 저장
- 파일 이름 규칙: `{섹션명}_{버전}.png` (예: `hero_v1.png`, `works_v2.png`)
- 최종 채택 디자인에 표시: `{섹션명}_final.png`
- 채택 후 디자인 토큰(색상, 폰트, 간격)을 `02_설계/design-tokens.md`에 옮겨 정리
