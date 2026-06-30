# ERP Dashboard — Design System

**Version 1.0.1** · Extracted from a single product screenshot (light theme, dense data/ERP dashboard)

This document is the portable, text-based companion to `design-system.html`. It contains every design token, component specification, and behavioral pattern observed in the source interface, organized for quick reference during implementation. Hex values are best-estimate samples read visually from the screenshot — verify against brand source files if/when available.

---

## 1. Design principles

The interface follows four consistent rules worth preserving in any new screen:

1. **Flat, content-led surfaces.** White cards sit on a soft grey canvas. Depth comes from a 1px border first; shadow is reserved for floating elements (tooltips, dropdowns), not resting cards.
2. **One accent does the talking.** Raspberry-pink marks the single primary data series and the page's one primary call-to-action. Indigo, blue, and green are secondary — used for trend lines, secondary series, and status only.
3. **Numbers are the heroes.** Metrics are set large, bold, and tabular. Supporting labels stay small and grey so the number is always read first.
4. **Generous, consistent rounding.** Corners scale from 8px (small controls) up to 20px (primary cards) and full pill radius for badges/avatars/buttons — never mixed within a single component.

---

## 2. Design tokens

### 2.1 Color — Neutrals

| Token | Hex | Usage |
|---|---|---|
| `--bg-page` | `#EEEEF1` | App canvas background |
| `--bg-surface` | `#FFFFFF` | Cards, sidebar, top bar |
| `--bg-surface-2` | `#F6F6F8` | Hover fill for nav/list rows |
| `--bg-surface-3` | `#F0F0F3` | Active nav background, pill buttons, default icon-tile fallback |
| `--border-subtle` | `#E9E9ED` | Internal dividers (card footers, list rows) |
| `--border-default` | `#E2E2E7` | Card & input outlines |
| `--border-strong` | `#D2D2D9` | Checkbox borders, hovered outline buttons |
| `--black` | `#0A0A0C` | Primary buttons, logo mark, primary text |
| `--black-hover` | `#232328` | Primary button hover |

### 2.2 Color — Text

| Token | Hex | Usage |
|---|---|---|
| `--text-primary` | `#0B0B0E` | Headings, big metric numbers, body emphasis |
| `--text-secondary` | `#6E6E78` | Labels, nav item text, descriptions |
| `--text-tertiary` | `#9C9CA6` | Captions, placeholders, timestamps |
| `--text-inverse` | `#FFFFFF` | Text on black/filled buttons |

### 2.3 Color — Data accents

| Token | Hex | Usage |
|---|---|---|
| `--pink-500` (primary) | `#EE3D72` | Income series / primary chart bars, checked checkbox, "hero" CTA accent |
| `--pink-100` | `#FCE0EA` | Negative-trend badge background |
| `--indigo-500` | `#6366F1` | Trend line overlay, default icon-tile fill |
| `--indigo-100` | `#E1E1FC` | Focus ring tint |
| `--blue-500` | `#3B82F6` | Expense series |
| `--blue-100` | `#DCEAFE` | Expense badge background |
| `--green-500` | `#18B463` | Net profit series |
| `--green-100` | `#DAF8E6` | Positive-trend badge background |
| `--green-600` | `#129650` | Positive-trend badge text |

### 2.4 Typography

Font family: **Inter** (sans-serif), fallback `-apple-system, BlinkMacSystemFont, 'Segoe UI', sans-serif`. Base size **14px**, base line-height **1.5**.

| Role | Token | Size | Weight | Tracking | Example |
|---|---|---|---|---|---|
| Display | `--fs-5xl` | 34px | 700 | -0.02em | "Dashboard" page title |
| Metric (large) | `--fs-4xl` | 30px | 700, tabular | normal | "458", "240" stat-card numbers |
| Section heading | `--fs-2xl` | 22px | 700 | normal | "Shortcuts Analytics" |
| Card title | `--fs-lg` | 16px | 700 | normal | "Reports & Masters" |
| Body | `--fs-base` | 14px | 500 | normal | List row labels |
| Label | `--fs-sm` | 13px | 500, secondary color | normal | "One Year Statement" |
| Caption | `--fs-xs` | 12px | 600, tertiary color | uppercase optional | "This Year" |
| Micro | `--fs-2xs` | 11px | 600 | normal | Badge text, version tag |

### 2.5 Spacing (4px base unit)

| Token | Value | Typical use |
|---|---|---|
| `--sp-1` | 4px | Icon-to-label micro gaps |
| `--sp-2` | 8px | Compact row gaps |
| `--sp-3` | 12px | Checkbox/label gap, sidebar item padding |
| `--sp-4` | 16px | Input padding, small card padding |
| `--sp-5` | 20px | Stat-card padding |
| `--sp-6` | 24px | **Primary card padding**, grid gutter |
| `--sp-8` | 32px | Hero stat row gap |
| `--sp-12` | 48px | Section-to-section vertical gap |

### 2.6 Radius

| Token | Value | Used for |
|---|---|---|
| `--r-sm` | 8px | Small/icon buttons |
| `--r-md` | 12px | Inputs, icon tiles, primary buttons |
| `--r-lg` | 16px | List cards |
| `--r-xl` | 20px | Primary cards, sidebar, chart card |
| `--r-full` | 999px | Pills, avatars, segmented controls, status dots |

### 2.7 Elevation

| Token | Value | Used for |
|---|---|---|
| `--shadow-xs` | `0 1px 2px rgba(15,15,20,.045)` | Resting card (rarely needed over border) |
| `--shadow-md` | `0 10px 28px rgba(15,15,20,.10)` | Hovered/dragged card |
| `--shadow-popover` | `0 14px 36px rgba(15,15,20,.14)` | Tooltips, dropdown menus |

### 2.8 Motion

| Token | Value | Used for |
|---|---|---|
| `--t-fast` | 120ms `cubic-bezier(.4,0,.2,1)` | Hover state transitions |
| `--t-base` | 180ms `cubic-bezier(.4,0,.2,1)` | Panel/dropdown open-close |

---

## 3. UI Kit

### 3.1 Buttons

| Variant | Height | Radius | Fill | Example |
|---|---|---|---|---|
| Primary | 40–46px | `--r-md` | `--black`, white text | "Explore Account" |
| Outline | 38–40px | `--r-md` / pill | white, 1px `--border-default` | "Import/Export", "Filters" |
| Ghost / pill | 34–40px | `--r-full` | `--bg-surface-3` | "12 New Task" |
| Icon button | 40×40px | `--r-md` or pill | `--bg-surface-3` | Bell, hamburger, theme toggle |

Rule: one primary (black) button per screen maximum. Outline and ghost cover everything else.

### 3.2 Form controls

- **Search field** — pill shape, `--bg-surface-3` fill, leading search icon, trailing `⌘F` shortcut chip, no visible border.
- **Text input** — 42px height, white fill, 1px `--border-default`, focus state adds a 3px `--indigo-100` ring + `--indigo-500` border.
- **Checkbox (series legend)** — 16px square, 4px radius; unchecked = `--border-strong` outline; checked = solid accent fill (pink/indigo/green depending on series) with a white check glyph.
- **Segmented toggle** (theme switch) — pill track in `--bg-surface-3`, active segment is a white pill with `--shadow-xs`.
- **Dropdown pill** ("Yearly") — pill outline button with trailing chevron-down icon.

### 3.3 Badges & chips

| Type | Style |
|---|---|
| Positive trend | `--green-100` bg, `--green-600` text, up-arrow icon, e.g. "+7%" |
| Negative trend | `--pink-100` bg, `--pink-600` text, down-arrow icon |
| Neutral | `--bg-surface-3` bg, secondary text |
| Count badge | `--bg-surface-3` bg, bold primary text, e.g. "12" |
| Notification dot | 9px circle, `--pink-500`, 2px white ring, top-right of bell icon |
| Status dot | 9px circle, `--green-500`, 2px white ring, bottom-right of avatar |

### 3.4 Avatars & icon tiles

- **Avatar**: 38px circle, gradient placeholder fill when no image provided.
- **Icon tile**: 42px (36px in compact stat cards) rounded-square (`--r-md`), solid accent fill, white stroke icon centered. Default accent for generic record types is indigo; use pink/blue/green only when the icon represents that specific data series.

---

## 4. Components

### 4.1 Sidebar navigation

Fixed 248px white panel. Structure: brand lockup → grouped nav sections (uppercase 11px tertiary-color label) → nav items → pinned account switcher footer.

Nav item states:
- **Default**: `--text-secondary`, transparent background
- **Hover**: `--bg-surface-2` background, `--text-primary`
- **Active**: `--bg-surface-3` background, `--text-primary`, font-weight 600

### 4.2 Top bar

Left-to-right: sidebar-collapse icon → breadcrumb (`Dashboard / Home`, last crumb bold) ... search field, task-count pill, theme segmented toggle, notification bell with dot — right aligned.

### 4.3 Stat card

Anatomy (top to bottom): label + icon tile row → large tabular number → 1px divider → footer row (trend badge + period label + "Show More" text link).

Spec: `--r-xl` radius, `--sp-5` (20px) padding, 36px icon tile, `--fs-4xl` number, divider before footer.

### 4.4 Chart card ("Shortcuts Analytics")

Anatomy: eyebrow label + title (left) / range-dropdown + filter button (right) → three-up micro-stat row (figure + trend badge + sparkline per series) → checkbox series legend → combo chart (neutral bars + highlighted-range pink bars + dashed indigo trend line + floating value tooltip) → month axis labels.

### 4.5 List card ("Reports & Masters")

`--r-xl` card, bold title + overflow (`···`) button header with a divider, followed by evenly divided rows (label left, small external-link icon button right), each row separated by a `--border-subtle` divider.

---

## 5. Patterns (behavior)

| # | Pattern | Behavior |
|---|---|---|
| 1 | **Series toggling** | Checkboxes act as a visibility legend, not a filter form. Checking adds a series in its accent color; unchecking fades it to neutral. At least one series must remain checked. |
| 2 | **Range highlight + tooltip** | A selected span of months brightens to full-opacity pink while the rest of the chart recedes to neutral fill; a floating tooltip anchors above the midpoint showing the aggregate value and date range. |
| 3 | **Stat card → drill-down** | Cards end in a quiet "Show More" text link rather than making the whole card clickable, so the number stays selectable and accidental navigation is avoided. |
| 4 | **Carousel overview** | Horizontally-paginated card rows use a pair of round prev/next buttons docked at the section header, not on the cards themselves. |
| 5 | **Responsive sidebar collapse** | The rail-icon toggle collapses the sidebar to icon-only; active-state background and icon persist without labels. |
| 6 | **Notification & presence dots** | One dot vocabulary, two meanings by position/color: top-right of bell (pink) = unread; bottom-right of avatar (green) = online. Never combined on one element. |

---

## 6. Documentation & guidelines

### 6.1 Component usage

| Component | Use for | Avoid |
|---|---|---|
| Primary button (black) | One decisive action per view | More than one per screen |
| Pink accent | The single primary data series, checked states, hero CTA | Decorative use; applying to more than one series |
| Stat card | A single countable metric with a YoY trend | Multi-metric comparisons (use the chart card) |
| List card | Grouping 2–6 navigational links per record type | Long lists past ~6 items — paginate instead |
| Tooltip | Contextual chart values on hover/selection | Persistent help text — use inline captions |

### 6.2 Do & don't

**Do**
- Pair every icon tile with a plain-text label, never icon alone.
- Keep one pink call-to-action visible per screen.
- Set numeric values in tabular figures so columns align.
- Use a 1px border before reaching for shadow.

**Don't**
- Mix more than one corner radius within a single card.
- Use red/pink for anything other than the primary series or a negative trend.
- Stack two outline buttons of equal visual weight as the main actions.
- Drop the divider between a card's metric and its footer actions.

### 6.3 Content & voice

Labels name what the person controls, in plain sentence case — "Show More," "Filters," "New Task" — never system jargon. Section eyebrows (e.g. "One Year Statement") set context before the headline so the number that follows is never ambiguous. Trend badges always pair the percentage with a directional icon so meaning never depends on color alone.

### 6.4 Accessibility

| Area | Guideline |
|---|---|
| Contrast | Body text (`#6E6E78`) on white passes AA at 14px; tertiary gray (`#9C9CA6`) is for non-essential captions only |
| Hit targets | All icon buttons are 40×40px minimum, even when the glyph itself is 15–18px |
| Focus state | Inputs and buttons get a 3px indigo ring at ~12% opacity on keyboard focus |
| Color independence | Trend badges and series legends always pair an icon or label with color |

---

## 7. File reference

- `design-system.html` — the live, interactive version of this system: rendered tokens, full UI kit, assembled components, and pattern demos in one page.
- `design.md` — this file, a portable text reference for the same tokens and specs.
