# Design Checklist — [Client Name]

**Prepared by:** Ayah / Sacra
**Date:** [Date]
**Figma file:** [Link to Figma file]
**Status:** [ ] In progress · [ ] Client approved

> This document is the bridge between the Figma file and the developer's build. Section names here must match exactly what's in Figma and in CONTENT.md.

---

## 1. Global Components

These appear on every page. Design and spec these first.

- [ ] Navigation (desktop + mobile)
- [ ] Footer
- [ ] Persistent CTA (e.g. sticky phone bar, floating button)
- [ ] Cookie banner (if applicable)

---

## 2. Section Library

All reusable sections to be designed before handoff. Check off each one as it's completed in Figma.

### Layout sections
- [ ] Hero — full width with heading, subheading, CTA, image
- [ ] Hero — centered text, no image
- [ ] [Add variants as needed]

### Content sections
- [ ] Feature grid — icon + heading + text (2–4 columns)
- [ ] Split section — text left, image right
- [ ] Split section — image left, text right
- [ ] Full-width text block
- [ ] Stats / numbers bar
- [ ] [Add as needed]

### Card sections
- [ ] Service cards grid
- [ ] Team cards grid
- [ ] Location cards grid
- [ ] Blog/article cards (if applicable)
- [ ] [Add as needed]

### Trust + social proof
- [ ] Testimonial block — single featured quote
- [ ] Testimonials grid
- [ ] Logo bar (client logos, certifications, awards)
- [ ] Trust bar (icon + short text, 3–5 items)

### CTA sections
- [ ] Full-width CTA banner (heading + button)
- [ ] Split CTA (text + form side by side)
- [ ] Inline CTA (embedded within content)

### Form sections
- [ ] Contact / inquiry form
- [ ] [Other form type — e.g. careers, referral]

### Utility sections
- [ ] Page hero (for interior pages — heading + breadcrumb)
- [ ] 404 page layout
- [ ] Privacy policy / plain text layout

---

## 3. Component Specs

Individual UI components. Document specs for each so the developer builds them consistently.

### Buttons
| Variant | Background | Text | Border | Hover state |
|---------|-----------|------|--------|-------------|
| Primary | [color] | [color] | none | [describe] |
| Secondary | [color] | [color] | none | [describe] |
| Ghost | transparent | [color] | [color] | [describe] |
| Destructive | [color] | [color] | none | [describe] |

**Border radius:** [value]
**Padding:** [e.g. 12px 24px]
**Font:** [weight, size]

### Forms
- Input fields: [height, border, border radius, focus state]
- Textarea: [min height, resize behavior]
- Dropdown/select: [style notes]
- Checkbox/radio: [style notes]
- Labels: [font size, weight, color]
- Error states: [color, icon, message placement]
- Submit button: [use Primary button style]

### Cards
- Background: [color]
- Border radius: [value]
- Shadow: [value]
- Padding: [value]
- Image treatment: [e.g. fixed ratio, object-fit cover]

### Icons
- Set: [e.g. Lucide Icons]
- Default size: [e.g. 24px]
- Color: [e.g. Primary brand color for info, accent for highlights]
- Always paired with a label

### Typography scale
| Level | Font | Size | Weight | Line height |
|-------|------|------|--------|-------------|
| Display / H1 | | | | |
| H2 | | | | |
| H3 | | | | |
| H4 | | | | |
| Body | | | | |
| Caption | | | | |
| Label | | | | |

---

## 4. Page Assembly Map

For each page: list the sections in order, top to bottom. Section names must match the Section Library above and CONTENT.md exactly.

<!-- Example format:
### Home (`/`)
1. Navigation (global)
2. Hero — full width with image
3. Trust bar
4. Service cards grid
5. Split section — text left, image right
6. Testimonials grid
7. Full-width CTA banner
8. Footer (global)
-->

### [Page name] (`/[slug]`)
1. Navigation (global)
2. [Section name]
3. [Section name]
4. [Section name]
5. Footer (global)

### [Page name] (`/[slug]`)
1. Navigation (global)
2. [Section name]
3. [Section name]
4. Footer (global)

### [CMS template page] (`/[collection-slug]/[item-slug]`)
<!-- This template applies to all items in the [Collection] collection -->
1. Navigation (global)
2. [Section name]
3. [Section name]
4. Footer (global)

<!-- Add a section for every page in the sitemap -->
