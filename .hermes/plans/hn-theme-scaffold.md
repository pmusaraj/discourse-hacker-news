# Hacker News-inspired Discourse theme scaffold plan

## Reference URL

- URL: https://news.ycombinator.com/
- Pages inspected: HN front page via browser and computed styles.
- Extracted styles:
  - Main page surface: `#f6f6ef` (`rgb(246,246,239)`).
  - Header/accent strip: `#ff6600`.
  - Primary story/link text: near-black `#000000`.
  - Metadata/domain text: gray `#828282`.
  - Font: `Verdana, Geneva, sans-serif`.
  - Body/story size: `13.333px`; metadata: `9.333px`; domain: `10.667px`.
  - Density: compact, flat, tabular, no shadows, no rounded card chrome.

## Visual extraction

- Primary: `#000000` for readable body text.
- Secondary/background: `#f6f6ef` for page and content surfaces.
- Accent/tertiary: `#ff6600` for header, primary buttons, selected states, focus outlines.
- Muted text: `#828282` via Discourse generated primary-medium/high tokens plus targeted metadata variables.
- Font: Verdana/Geneva/system sans; base size intentionally small to match HN.
- Radius scale: square/near-square (`0` to `2px`), matching HN’s flat table feel.
- Borders/shadows: no shadows; subtle orange/gray single-pixel separators only where helpful.
- Buttons/inputs/cards: rectangular, compact, low-chrome.

## Discourse mapping

- Color scheme in `about.json`:
  - `primary`: `000000`
  - `secondary`: `F6F6EF`
  - `tertiary`: `FF6600`
  - `quaternary`: `828282`
  - `header_background`: `FF6600`
  - `header_primary`: `000000`
  - `highlight` / `selected`: pale orange and warm cream.
- CSS custom properties:
  - `--font-family`, `--heading-font-family`
  - `--d-border-radius`, `--d-button-border-radius`, `--d-input-border-radius`
  - button, input, sidebar, table, topic-list, metadata, and header tokens.
- Target selectors/components:
  - `.d-header`, sidebar rows, topic lists/latest lists, category lists, buttons, inputs, composer surface, small metadata.
- Intentionally default:
  - Discourse layout, navigation structure, plugin UI behavior, mobile layout, icons, menus, user cards except safe child card content.

## Theme scaffold

- Repo/path: `/Users/pmusaraj/Projects/discourse-hacker-news`
- Files:
  - `about.json`
  - `common/common.scss`
  - `screenshots/light.png` after verification
- No JavaScript, connectors, icon components, or server-side modifiers needed.
- Internal examples checked: `pmusaraj/discourse-verso` and `pmusaraj/discourse-accent` for package structure, color scheme placement, screenshot metadata, and conservative SCSS organization.

## Testing plan

1. Copy/import the local theme directory into the Docker-backed Discourse instance.
2. Set it as the default theme for preview on `https://disco2021.musaraj.com` (Cloudflare tunnel exposed local instance).
3. Verify Rails theme state, generated `common_theme` stylesheet, and actual browser-rendered theme stylesheet.
4. Inspect `/latest`, `/categories`, a topic page, and composer/open controls where available.
5. Check console/theme banners and run CSS guardrail probes.
6. Capture a light screenshot and save it as `screenshots/light.png`, then re-import so metadata points to a real file.
