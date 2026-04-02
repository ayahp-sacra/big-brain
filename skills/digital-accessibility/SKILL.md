---
name: digital-accessibility
description: WCAG 2.2-compliant accessibility patterns for design, implementation, and testing — applied to every UI we produce
origin: ECC
---

# Digital Accessibility

Accessibility is not a post-launch audit. It is a design constraint applied at the earliest decision point — branding — and held through every layer until deployment.

**Standard:** WCAG 2.2, target conformance level AA minimum, AAA where feasible.
**Principles:** Perceivable · Operable · Understandable · Robust (POUR)

---

## When to Activate

This skill is always active. Specific trigger points:

- **Branding conversations** — any discussion of color palettes, typeface selection, visual hierarchy, or brand direction. This is the earliest and most important intervention point.
- **Design work** — wireframes, mockups, design system tokens, component specs
- **Frontend development** — new components, UI changes, design system updates
- **Code review** — any PR touching UI, styles, or interactive behavior
- **Visual-design or frontend-patterns skill invocations** — run this skill in parallel

Accessibility constraints must inform decisions at the source. Retrofitting is expensive and always incomplete.

---

## 1. Branding Phase Gate

Run this before any color palette or type system is locked.

### Color Palette
- Every proposed primary color must achieve **4.5:1** against both white (`#ffffff`) and a dark background (`#0f0f0f` or equivalent) — adjust lightness until it passes, then lock the token
- Document the contrast ratio for every color pairing in the brand spec (e.g., `--color-text` on `--color-bg`: 7.2:1 ✓)
- Brand palettes must include accessible light **and** dark variants — a color that only works on one background is not a complete brand color
- Never define a palette where the only accessible combination is the brand color on white — dark mode and component states must also pass

### Typography
- Confirm every typeface is legible at 16px — test by rendering a paragraph at that size before approving
- The chosen font family must include weight `400` (body) and `700` (emphasis) — decorative or display fonts cannot serve as the body typeface
- If using a variable font, confirm axes include weight range 400–700

### Hierarchy System
- Define heading levels H1–H4 with distinct size, weight, and spacing that are visually distinguishable **without color**
- Color alone must never be the sole differentiator between hierarchy levels
- Document the heading scale as part of the brand spec

### Motion
- If brand direction calls for animation, define the reduced-motion fallback strategy at this stage — not after implementation

---

## 2. Design-Layer Checklist

Apply during mockup and component design, before any code is written.

| Concern | Requirement |
|---------|-------------|
| Text contrast | 4.5:1 minimum (body), 3:1 for large text (≥18pt or ≥14pt bold) |
| UI component contrast | 3:1 — buttons, inputs, icons, borders — against adjacent background |
| Color as sole signal | Never — always pair color with icon, label, pattern, or shape |
| Touch targets | 44×44px minimum (WCAG 2.5.5), 48×48px recommended |
| Typography | 16px minimum body, line height ≥ 1.5, max line length 80ch, no justified text |
| Focus indicator | Visible ring on all interactive elements — 2px minimum, 3:1 contrast against adjacent color (WCAG 2.4.11) |
| Animation | All motion must have `prefers-reduced-motion` fallback defined; no content that flashes >3Hz |
| Spacing | Structure must be conveyed through heading hierarchy and semantic grouping — not whitespace alone |
| Error states | Error indicators must not rely on color alone (red border + error icon + message text) |

---

## 3. Semantic HTML Patterns

Use the right element for the right purpose. ARIA cannot fix the wrong element.

### Page Structure
```html
<body>
  <a href="#main" class="skip-link">Skip to main content</a>
  <header>...</header>
  <nav aria-label="Primary">...</nav>
  <main id="main">...</main>
  <aside aria-label="Related">...</aside>
  <footer>...</footer>
</body>
```
- One `<main>` per page
- Skip-to-main link must be the first focusable element; it can be visually hidden until focused

### Headings
```html
<h1>Page title</h1>          <!-- one per page -->
  <h2>Section</h2>
    <h3>Subsection</h3>
      <h4>Sub-subsection</h4>
```
- Never skip levels (no H1 → H3)
- Heading levels convey document structure, not visual size — use CSS for sizing

### Interactive Elements
```html
<!-- Actions → <button> -->
<button type="button">Save changes</button>

<!-- Navigation → <a> -->
<a href="/dashboard">Dashboard</a>

<!-- NEVER -->
<div onClick={handleClick}>Click me</div>  <!-- no keyboard access, no role, no focus -->
<span onClick={handleClick}>Submit</span>
```

### Forms
```html
<!-- Explicit label (preferred) -->
<label for="email">Email address</label>
<input type="email" id="email" autocomplete="email" required>

<!-- Grouped fields -->
<fieldset>
  <legend>Shipping address</legend>
  <label for="street">Street</label>
  <input type="text" id="street">
</fieldset>

<!-- Error state -->
<label for="email">Email address</label>
<input type="email" id="email" aria-describedby="email-error" aria-invalid="true">
<span id="email-error" role="alert">Enter a valid email address</span>
```
- `placeholder` is supplemental context, never the only label
- `required` on the element, plus visible indicator in the label ("*" with a legend explaining it)
- `autocomplete` attributes reduce cognitive load and support assistive tech

### Lists and Tables
```html
<!-- Navigation list -->
<ul>
  <li><a href="/home">Home</a></li>
  <li><a href="/about">About</a></li>
</ul>

<!-- Data table -->
<table>
  <caption>Q1 2026 Revenue by Region</caption>
  <thead>
    <tr>
      <th scope="col">Region</th>
      <th scope="col">Revenue</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th scope="row">North America</th>
      <td>$4.2M</td>
    </tr>
  </tbody>
</table>
```

---

## 4. ARIA Patterns

**Rule:** Use semantic HTML first. Add ARIA only when HTML alone is insufficient.
**ARIA rule #1:** Never change a native element's role unless you fully reimplement its behavior.

### Labels
```html
<!-- aria-label: short string label -->
<button aria-label="Close dialog">✕</button>

<!-- aria-labelledby: reference another element -->
<h2 id="dialog-title">Confirm deletion</h2>
<div role="dialog" aria-labelledby="dialog-title" aria-modal="true">...</div>

<!-- aria-describedby: supplemental description -->
<input id="password" type="password" aria-describedby="password-hint">
<span id="password-hint">Must be 8+ characters with a number</span>
```

### Live Regions
```html
<!-- Polite: non-urgent async updates (search results, form success) -->
<div aria-live="polite" aria-atomic="true" id="status"></div>

<!-- Assertive: critical, time-sensitive errors only -->
<div role="alert">Session will expire in 2 minutes</div>
```
- `aria-live="assertive"` interrupts the user — reserve for genuine urgency
- `role="status"` is equivalent to `aria-live="polite"`
- `role="alert"` is equivalent to `aria-live="assertive"`

### Modal Dialog
```html
<div
  role="dialog"
  aria-modal="true"
  aria-labelledby="dialog-heading"
  aria-describedby="dialog-description"
>
  <h2 id="dialog-heading">Delete account</h2>
  <p id="dialog-description">This action cannot be undone.</p>
  <button>Cancel</button>
  <button>Delete</button>
</div>
```
- On open: move focus to first focusable element inside (or the dialog itself if no focusable child)
- Trap focus within the dialog while open
- On close: restore focus to the element that triggered the dialog
- Escape key dismisses

### Toast / Status Notification
```html
<div role="status" aria-live="polite" aria-atomic="true">
  <!-- Inject message text here dynamically -->
  Changes saved successfully
</div>
```

### Tab Group
```html
<div role="tablist" aria-label="Account settings">
  <button role="tab" aria-selected="true" aria-controls="panel-profile" id="tab-profile">Profile</button>
  <button role="tab" aria-selected="false" aria-controls="panel-security" id="tab-security" tabindex="-1">Security</button>
</div>
<div role="tabpanel" id="panel-profile" aria-labelledby="tab-profile">...</div>
<div role="tabpanel" id="panel-security" aria-labelledby="tab-security" hidden>...</div>
```
- Only the active tab is in tab order (`tabindex="0"`); others use `tabindex="-1"`
- Arrow keys move between tabs; Enter/Space activate

### State Attributes Reference
| Attribute | Use for |
|-----------|---------|
| `aria-expanded` | Toggles (accordion, dropdown, disclosure) |
| `aria-selected` | Selected item in a list, tab, or grid |
| `aria-checked` | Checkbox, radio, switch state |
| `aria-disabled` | Disabled but still perceivable (vs `disabled` which removes from AT) |
| `aria-hidden="true"` | Remove decorative elements from the accessibility tree |
| `aria-current="page"` | Active item in navigation |
| `aria-pressed` | Toggle buttons |

---

## 5. Keyboard Navigation

Every feature must be fully usable with keyboard only (no mouse, no touch).

### Tab Order
- Follows the visual/logical reading order — if visual order differs from DOM order, use CSS to adjust visual layout, not `tabindex` to reorder
- `tabindex="0"`: add non-interactive element to tab order (only when necessary)
- `tabindex="-1"`: remove from tab order but keep programmatically focusable
- Never use `tabindex` values > 0

### Composite Widget Keyboard Conventions
| Widget | Keys |
|--------|------|
| Menu / Listbox | Arrow Up/Down to move, Enter to select, Escape to close |
| Radio group | Arrow keys to move between options |
| Tabs | Arrow Left/Right to move between tabs |
| Tree | Arrow Up/Down to move, Arrow Right to expand, Arrow Left to collapse |
| Date picker | Arrow keys to navigate grid, Enter to select, Escape to close |

### Focus Trap (Modal / Drawer)
```javascript
// On modal open:
// 1. Save reference to previously focused element
const previousFocus = document.activeElement;
// 2. Move focus into modal
modal.querySelector('[autofocus], button, [href], input, select, textarea, [tabindex]:not([tabindex="-1"])').focus();
// 3. Intercept Tab/Shift+Tab — wrap at boundaries

// On modal close:
// 4. Restore focus
previousFocus.focus();
```

### Skip Navigation
```html
<a href="#main" class="skip-link">Skip to main content</a>
```
```css
.skip-link {
  position: absolute;
  transform: translateY(-100%);
  transition: transform 0.2s;
}
.skip-link:focus {
  transform: translateY(0);
}
```

---

## 6. Images and Media

### Alt Text
```html
<!-- Informative: describe what the image communicates, not what it depicts -->
<img src="chart.png" alt="Revenue grew 40% YoY in Q1 2026, driven by enterprise contracts">

<!-- Decorative: suppress from accessibility tree -->
<img src="divider.png" alt="">

<!-- Functional (icon button): describe the action -->
<button>
  <img src="search.svg" alt="Search">
</button>

<!-- Complex (chart/diagram): brief alt + detailed description nearby -->
<img src="architecture.png" alt="System architecture diagram" aria-describedby="arch-desc">
<p id="arch-desc">Three-tier architecture: client layer (React), API layer (Node.js), data layer (PostgreSQL)...</p>
```

### Video and Audio
- All videos must have synchronized captions (not auto-generated without review)
- Videos with meaningful visual content (diagrams, demonstrations) must have audio descriptions
- No autoplay with audio — provide a visible, keyboard-accessible control
- Transcripts for audio-only content

---

## 7. Motion and Animation

```css
/* Define animation normally */
@keyframes slide-in {
  from { transform: translateX(-100%); }
  to { transform: translateX(0); }
}

.panel {
  animation: slide-in 300ms ease-out;
}

/* Suppress for users who prefer reduced motion */
@media (prefers-reduced-motion: reduce) {
  .panel {
    animation: none;
    /* Use an instant state change instead */
    transform: translateX(0);
  }
}
```

- No content that flashes more than 3 times per second (WCAG 2.3.1)
- Carousels and auto-advancing content: provide pause controls
- Parallax, large-scale motion, and scroll-triggered animations: disable under `prefers-reduced-motion`

---

## 8. Testing

Automated tools catch ~30–40% of accessibility issues. Manual testing is required.

### Automated (run on every PR)
- **axe-core** — zero violations is the bar; `aria-*`, contrast, label, role issues
- **Lighthouse** accessibility audit — score 90+ minimum
- **eslint-plugin-jsx-a11y** — catches common JSX accessibility errors at author time

### Manual Testing Protocol
1. **Keyboard-only pass** — unplug the mouse, tab through every page and interactive element
   - Can you reach and operate every control?
   - Is focus always visible?
   - Does tab order match visual reading order?

2. **Screen reader spot check**
   - Windows: NVDA + Chrome
   - macOS/iOS: VoiceOver + Safari
   - Test: page structure (landmarks, headings), form interaction, dynamic content updates, modal dialogs

3. **Zoom test** — set browser zoom to 200% and then 400%
   - No content loss or truncation
   - No horizontal scrolling (exception: data tables)
   - Layout remains usable

4. **Contrast verification** — use browser DevTools color picker or Colour Contrast Analyser on final rendered screens (not design files — rendering affects perceived contrast)

5. **Reduced motion** — in DevTools, emulate `prefers-reduced-motion: reduce`
   - All animations suppress or reduce to instant state changes

---

## 9. Pre-Commit Checklist

Before any UI-touching PR is merged:

- [ ] All images have appropriate `alt` text (informative, decorative, or functional)
- [ ] Color contrast passes: 4.5:1 for text, 3:1 for UI components and large text
- [ ] No information conveyed by color alone
- [ ] All interactive elements are keyboard accessible and focusable
- [ ] Focus indicators are visible on all interactive elements
- [ ] Heading hierarchy is sequential and semantically meaningful
- [ ] All form inputs have explicit `<label>` associations
- [ ] ARIA attributes are present where needed and used correctly
- [ ] `prefers-reduced-motion` handled for all animations
- [ ] Dynamic content updates announced via live regions where appropriate
- [ ] axe-core reports zero violations
- [ ] Keyboard-only pass completed for new flows
