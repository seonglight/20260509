# Stitch 결과물 갭 분석

> 비교 대상
> - **기획안**: `01_기획/design-planning.md`
> - **Stitch 산출물**: `01_기획/stitch-results/` (code.html, DESIGN.md, screen.png)

---

## 1. 종합 평가

| 항목 | 기획 의도 일치도 | 코멘트 |
|------|------------------|--------|
| 브랜드 톤·무드 | ★★★★★ | "Cinematic Minimalism" 콘셉트 정확히 반영 |
| 컬러 시스템 | ★★★☆☆ | 골드 컬러는 살아있으나 변종이 과다 |
| 타이포그래피 | ★★★★☆ | 의도와 다른 폰트 추가 — 전반적으로 적절 |
| 레이아웃 구조 | ★★☆☆☆ | **모바일 전용**으로만 출력됨, 데스크탑 그리드 없음 |
| 섹션 구성 | ★★★★☆ | Hero → Works → About → Contact 순서 일치 |
| 인터랙션 | ★★☆☆☆ | 필터 탭, 라이트박스 등 동적 요소 미구현 |
| 기술 스택 | ★★☆☆☆ | Tailwind CDN 사용 — 순수 HTML/CSS 정책과 불일치 |

---

## 2. 정렬된 항목 (Aligned)

기획 의도와 정확히 맞아떨어진 부분 — 그대로 채택 가능.

### 무드·디자인 철학
- 다크 시네마틱 미니멀리즘 (`#0a0a0a` 베이스)
- **0px border-radius** — "Rectilinear" 룰 일치
- 그림자 없이 1px hairline border로 깊이 표현
- 골드 포인트의 절제된 사용

### 섹션 구조
- Hero · Works · About · Contact 순서 그대로
- Hero의 풀스크린 + 슬로건 + scroll indicator 패턴 일치
- Form의 bottom-border-only 스타일, focus 시 골드 전환
- Primary 버튼: 솔리드 골드 배경 + 블랙 텍스트

### 슬로건·문구
- "빛으로 순간을 기록합니다" 그대로 반영
- "Director · Photographer" 역할 표기 일치

---

## 3. 격차 (Gaps)

### 🔴 Critical — 반드시 해결

#### G1. 데스크탑 레이아웃 부재
- **기획**: 데스크탑(1280px+) 우선, Works 3-column grid, About 50/50 two-column
- **현재**: 모바일(360px) 단일 컬럼만 출력됨
- **screen.png**: 약 360px 폭 모바일 화면만 존재
- **영향**: 가장 핵심적인 데스크탑 레이아웃 누락 — 포트폴리오 사이트의 메인 뷰
- **대응**: Stitch에 데스크탑 뷰 프롬프트 별도 요청 필요

#### G2. About 섹션 레이아웃 다름
- **기획**: 좌측 portrait(3:4) + 우측 bio (50/50 two-column)
- **현재**: portrait 위, bio 아래 (stacked single column)
- **대응**: 데스크탑 버전 재생성 시 two-column으로 명시

#### G3. Tailwind CDN 의존
- **기획**: 순수 HTML/CSS/JS, 번들러·CDN 최소화 (CLAUDE.md 명시)
- **현재**: `cdn.tailwindcss.com` + Material Symbols + Google Fonts CDN 다수
- **대응**: 코드를 그대로 가져오지 말고 **참조용**으로만 사용. CSS 변환 작업 필요.

---

### 🟡 Major — 결정 필요

#### G4. 컬러 토큰 과다
- **기획**: 5개 (`bg`, `text`, `accent`, `secondary-text`, `border`)
- **현재**: Material You 시스템 그대로 — surface 6단계, primary 4단계, secondary·tertiary·error 풀세트
- **골드 변종**: `#ffe6ab` (primary), `#e8c97a` (primary-container), `#e2c375` (primary-fixed-dim) — 3종
- **대응**: 5–6개 토큰으로 정리. 골드는 1종만 채택 추천 (`#e8c97a`).

#### G5. 폰트 추가 (Bebas Neue, Hanken Grotesk)
- **기획**: Noto Serif KR + Inter/DM Sans 1쌍
- **현재**: Noto Serif KR + Bebas Neue + Hanken Grotesk 3종
- **평가**: Bebas Neue는 시네마틱 무드와 잘 어울림 (영화 크레딧·포스터 톤). Hanken Grotesk는 본문용으로 가독성 양호.
- **대응**: 3종 모두 채택 추천. 단, 웹폰트 로딩 비용 점검 (Performance 90 목표 영향).

#### G6. 네비게이션 구조 다름
- **기획**: 고정 상단바, 우측 텍스트 3개 링크 (Works · About · Contact)
- **현재**: 좌측 햄버거 메뉴 + 중앙 LIGHTMAP 로고 + 우측 CONTACT 단일 링크
- **대응**: 모바일은 햄버거 OK. 데스크탑 버전에 텍스트 링크 3개 추가 필요.

#### G7. Works 필터 인터랙션 미구현
- **기획**: "영상 Video" / "사진 Photo" 탭 클릭 시 그리드 필터링
- **현재**: 정적 마크업만 — JS 필터 로직 없음
- **대응**: 3단계 개발에서 IntersectionObserver와 함께 필터 JS 구현 항목 추가.

---

### 🟢 Minor — 보완 권장

#### G8. About 섹션 SNS 아이콘 누락
- **기획**: bio 하단에 이메일·Instagram 아이콘 링크
- **현재**: 텍스트만 있음
- **대응**: 데스크탑 재생성 시 아이콘 영역 명시

#### G9. Contact 직접 연락처 누락
- **기획**: 폼 + `hello@lightmap.kr` 텍스트 링크 + `@lightmap` Instagram
- **현재**: 폼만 있음
- **대응**: 폼 하단에 직접 연락처 영역 추가

#### G10. Footer 확장됨
- **기획**: `© 2026 Lightmap. All rights reserved.` 한 줄
- **현재**: WORKS / PROCESS / TEAM / LEGAL 4개 링크 + 카피라이트
- **대응**: PROCESS / TEAM / LEGAL은 계획에 없는 페이지. 두 가지 선택지:
  - (a) 푸터를 한 줄로 줄임 (계획대로)
  - (b) 사이트 범위를 확장 — 추가 페이지 콘텐츠 기획 필요

#### G11. Works 카드 레이아웃 패턴 차이
- **기획**: 썸네일 + 하단 별도 영역에 캡션·태그
- **현재**: 썸네일 위에 그라디언트 오버레이 + 카테고리·타이틀
- **평가**: Stitch 패턴이 더 시네마틱 — 채택 권장
- **대응**: 채택 시 기획 문서 업데이트

#### G12. 이미지 placeholder
- 모든 이미지가 Stitch의 `lh3.googleusercontent.com/aida-public/...` URL
- 실제 라이트맵 작업물로 교체 필요 (3단계 개발 전 자산 수집 단계 필요)

---

## 4. 채택 결정 매트릭스

| 항목 | 결정 | 이유 |
|------|------|------|
| 다크 시네마틱 무드 | ✅ 채택 | 기획과 완벽 일치 |
| 0px border-radius | ✅ 채택 | "Rectilinear" 콘셉트 강화 |
| Bebas Neue 추가 | ✅ 채택 추천 | 시네마틱 무드 강화, 영문 라벨에 적합 |
| Hanken Grotesk 추가 | ✅ 채택 추천 | 본문 가독성 양호 |
| Material 컬러 토큰 풀세트 | ❌ 단순화 | 5–6개로 정리 |
| 골드 3종 변종 | ❌ 단일화 | `#e8c97a` 1종으로 통일 |
| Works 그라디언트 오버레이 카드 | ✅ 채택 추천 | 더 시네마틱한 표현 |
| Tailwind CDN | ❌ 제거 | 순수 CSS로 변환 |
| Material Symbols 아이콘 | ❌ 제거 | SVG 인라인으로 교체 |
| Footer 4개 링크 | ⚠️ 결정 보류 | 사이트 범위 확정 후 결정 |
| 모바일 전용 출력 | ❌ 보완 | 데스크탑 뷰 재생성 필수 |

---

## 5. 다음 액션 (Action Items)

### A. Stitch 추가 작업
- [ ] **데스크탑 뷰 프롬프트** 작성 후 재생성
  - 1440px 기준, Works 3-column grid, About 50/50 two-column
  - 데스크탑 네비 텍스트 링크 3개 (Works · About · Contact)
- [ ] About 섹션에 이메일·Instagram 아이콘 명시
- [ ] Contact 섹션에 직접 연락처 영역 명시

### B. 디자인 토큰 정리 (2단계 설계로 이관)
- [ ] `02_설계/design-tokens.md` 생성
- [ ] 컬러 5–6개로 정제 (`bg`, `bg-elevated`, `text`, `text-muted`, `accent`, `border`)
- [ ] 골드 단일화: `#e8c97a`
- [ ] 폰트 3종 확정 + 웹폰트 로딩 전략 (preload, font-display: swap)

### C. 사이트 범위 확정
- [ ] PROCESS / TEAM / LEGAL 페이지 추가 여부 결정
  - 추가 시 → 기획 문서에 콘텐츠 항목 추가
  - 불필요 시 → 푸터를 한 줄로 축소

### D. 자산 수집 (개발 전 선행)
- [ ] Hero 영상/이미지 1점
- [ ] Works 썸네일 최소 6점 (영상 3 + 사진 3)
- [ ] About portrait 1점
- [ ] 카테고리 라벨 정의 (COMMERCIAL, DOCUMENTARY, MUSIC VIDEO 등)

### E. 기획 문서 업데이트
- [ ] `design-planning.md` 채택 결정 반영
  - Bebas Neue, Hanken Grotesk 추가
  - Works 카드를 그라디언트 오버레이 패턴으로 변경
  - 골드 단일화 명시
