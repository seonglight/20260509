---
name: Lightmap Cinematic System
colors:
  surface: '#121414'
  surface-dim: '#121414'
  surface-bright: '#38393a'
  surface-container-lowest: '#0c0f0f'
  surface-container-low: '#1a1c1c'
  surface-container: '#1e2020'
  surface-container-high: '#282a2b'
  surface-container-highest: '#333535'
  on-surface: '#e2e2e2'
  on-surface-variant: '#cfc5b4'
  inverse-surface: '#e2e2e2'
  inverse-on-surface: '#2f3131'
  outline: '#989080'
  outline-variant: '#4c4639'
  surface-tint: '#e2c375'
  primary: '#ffe6ab'
  on-primary: '#3d2e00'
  primary-container: '#e8c97a'
  on-primary-container: '#6a530f'
  inverse-primary: '#725c17'
  secondary: '#c9c6c5'
  on-secondary: '#313030'
  secondary-container: '#4a4949'
  on-secondary-container: '#bab8b7'
  tertiary: '#eae7e7'
  on-tertiary: '#313030'
  tertiary-container: '#cecbcb'
  on-tertiary-container: '#575655'
  error: '#ffb4ab'
  on-error: '#690005'
  error-container: '#93000a'
  on-error-container: '#ffdad6'
  primary-fixed: '#ffdf91'
  primary-fixed-dim: '#e2c375'
  on-primary-fixed: '#241a00'
  on-primary-fixed-variant: '#584400'
  secondary-fixed: '#e5e2e1'
  secondary-fixed-dim: '#c9c6c5'
  on-secondary-fixed: '#1c1b1b'
  on-secondary-fixed-variant: '#474646'
  tertiary-fixed: '#e5e2e1'
  tertiary-fixed-dim: '#c8c6c5'
  on-tertiary-fixed: '#1c1b1b'
  on-tertiary-fixed-variant: '#474646'
  background: '#121414'
  on-background: '#e2e2e2'
  surface-variant: '#333535'
typography:
  display-lg:
    fontFamily: notoSerif
    fontSize: 64px
    fontWeight: '400'
    lineHeight: '1.1'
    letterSpacing: -0.02em
  display-lg-mobile:
    fontFamily: notoSerif
    fontSize: 40px
    fontWeight: '400'
    lineHeight: '1.2'
  headline-md:
    fontFamily: notoSerif
    fontSize: 32px
    fontWeight: '400'
    lineHeight: '1.3'
  subheading-en:
    fontFamily: bebasNeue
    fontSize: 18px
    fontWeight: '400'
    lineHeight: '1.0'
    letterSpacing: 0.15em
  body-lg:
    fontFamily: hankenGrotesk
    fontSize: 18px
    fontWeight: '400'
    lineHeight: '1.6'
  body-md:
    fontFamily: hankenGrotesk
    fontSize: 16px
    fontWeight: '400'
    lineHeight: '1.6'
  label-sm:
    fontFamily: hankenGrotesk
    fontSize: 12px
    fontWeight: '500'
    lineHeight: '1.0'
    letterSpacing: 0.05em
spacing:
  unit: 4px
  container-max: 1440px
  gutter: 24px
  margin-desktop: 80px
  margin-mobile: 20px
  section-gap: 160px
---

## Brand & Style

This design system is built to reflect the prestige and technical precision of high-end video production and photography. The visual identity is rooted in **Cinematic Minimalism**, drawing inspiration from film credits, gallery exhibitions, and luxury editorial layouts.

The emotional response should be one of quiet confidence, sophistication, and focus. By utilizing deep blacks and subtle gold accents, the interface recedes to the background, allowing the studio’s visual portfolio to remain the primary focus. The aesthetic avoids all modern trends of softness or playfulness, opting instead for a structural, architectural rigor characterized by sharp corners, hairline strokes, and intentional whitespace.

## Colors

The palette is strictly limited to maintain a high-end, gallery-like atmosphere. 

- **Primary Background (#0a0a0a):** A deep, near-black that provides the canvas for cinematic content.
- **Secondary Background (#111111):** Used for subtle sectioning and container differentiation without breaking the dark immersion.
- **Accent Gold (#e8c97a):** A warm, desaturated gold used sparingly for calls to action, active states, and critical iconography. It represents the "light" in Lightmap.
- **Typography:** Primary text uses an off-white to reduce eye strain against the black background, while secondary text uses a muted gray to establish clear information hierarchy.
- **Lines/Borders:** Hairline strokes should use a dark gray (#2a2a2a) to define structure without being intrusive.

## Typography

This design system employs a sophisticated typographic pairing to balance tradition and modernity.

- **Headings (Serif):** Uses **Noto Serif** for its elegant, authoritative presence, especially for Korean characters. It mimics the look of high-end editorial mastheads.
- **Sub-titles & Tags (Sans-serif Display):** Uses **Bebas Neue** for English tags and categories. Its tall, condensed form factor evokes cinematic "lower thirds" and film posters.
- **Body Copy (Sans-serif):** Uses **Hanken Grotesk** for its exceptional readability and clean, contemporary geometry.

**Rules:**
1. Headlines should never use bold weights; the serif letterforms provide enough character.
2. Maintain generous line height for body text to ensure a luxurious reading experience.
3. Use all-caps with increased letter spacing for Bebas Neue labels to maximize the "tag" aesthetic.

## Layout & Spacing

The layout philosophy follows a **Fixed Grid** approach for content containers to maintain a disciplined, editorial structure. 

- **Grid:** Use a 12-column grid for desktop with 24px gutters. Elements should align strictly to these columns.
- **Whitespace:** Emphasize vertical "breathing room." Section gaps should be substantial (120px-160px) to give each project or service its own stage.
- **Alignment:** Use asymmetrical layouts where necessary to create visual interest, but always anchor elements to the grid lines.
- **Mobile:** Reflow to a single-column layout with 20px side margins. Typography scales down specifically for the Display role to prevent awkward wrapping.

## Elevation & Depth

This design system rejects the use of shadows and blurs to maintain a "flat but deep" aesthetic. 

- **Tonal Layering:** Depth is achieved solely through color. The base layer is #0a0a0a. Cards or secondary sections sit on #111111.
- **Thin Lines:** Use 1px solid borders (#2a2a2a) to define edges. This mimics the technical drawings of camera lenses and equipment.
- **Interactive Depth:** When an element is hovered, the depth change is indicated by a color shift of the border to the Accent Gold or a slight opacity change in the content, rather than a shadow "lift."

## Shapes

The shape language is strictly **Rectilinear**. 

- **Corners:** All buttons, input fields, images, and containers must have **0px border-radius**. Sharp corners communicate precision, technical skill, and a modern edge.
- **Accents:** Horizontal lines (1px height) in Accent Gold should be used as dividers or to underline active navigation items, reinforcing the "map" or "timeline" aspect of the brand name.

## Components

### Buttons
- **Primary:** Sharp-edged, solid Gold background with Black text. No hover shadow; instead, use a slight darkening of the gold on hover.
- **Secondary:** Ghost style. 1px Gold border with Gold text. On hover, fills with Gold and changes text to Black.

### Input Fields
- Transparent background with a 1px bottom-border only (#2a2a2a). On focus, the bottom border changes to Gold. Labels should use the **label-sm** style sitting above the line.

### Cards
- Use #111111 background. No padding between the image and the card edge; the image should be flush with the top and sides. Content below the image should have generous padding (24px+).

### Video/Photo Thumbnails
- Always sharp corners. On hover, a 1px Gold border appears inside the frame (inset), and the image should slightly desaturate to emphasize the UI overlay.

### Navigation
- Minimalist top bar. Use **subheading-en** for nav items. The active state is indicated by a 1px Gold line 4px below the text.