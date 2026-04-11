# Content — [Client Name]

**Prepared by:** Ayah / Sacra
**Date:** [Date]
**Status:** [ ] Draft · [ ] Client approved

> **How to use this document**
> - `[Ayah]` — Ayah writes this section
> - `[Client]` — Client writes this section; Ayah reviews and refines before finalizing
> - `[Image: description]` — Image placement note; style defined in BRAND.md
> - Section names match Figma component names and DESIGN-CHECKLIST.md exactly

---

## Global Elements

These appear across all pages.

### Navigation
- Logo alt text: `[Client name] logo` `[Ayah]`
- Nav links: `[Ayah]`
  - [Link label] → `/[slug]`
  - [Link label] → `/[slug]`
  - [Link label with dropdown] → children:
    - [Child label] → `/[slug]`
    - [Child label] → `/[slug]`
- CTA button: `[Button label]` `[Ayah]`
- Phone number: `[Phone number]` `[Client]`

### Footer
- Tagline or short description: `[Client]`
- Address: `[Client]`
- Phone: `[Client]`
- Email: `[Client]`
- Column 1 heading + links: `[Ayah]`
- Column 2 heading + links: `[Ayah]`
- Copyright line: `© [Year] [Client name]. All rights reserved.` `[Ayah]`
- Privacy policy link label: `Privacy Policy` `[Ayah]`

### Persistent CTA
- CTA text: `[e.g. Call us: (555) 555-5555]` `[Client]`
- CTA button label: `[e.g. Get a Free Assessment]` `[Ayah]`

---

## Pages

<!-- For each page: list sections in the order they appear (matching DESIGN-CHECKLIST page assembly map).
     For each section: fill in every copy field. -->

---

### Home (`/`)

#### Hero — [section name from DESIGN-CHECKLIST]
`[Ayah]`
- Headline: `[e.g. Compassionate Care for Your Family, Right at Home]`
- Subheadline: `[e.g. Trusted by [X] families across [region]. Available 24/7.]`
- Primary CTA button: `[e.g. Get a Free Assessment]` → `/contact`
- Secondary CTA button: `[e.g. Learn About Our Services]` → `/services`
- `[Image: [describe — e.g. warm photo of caregiver with senior, natural light, home setting]]`

#### [Section name]
`[Ayah]` / `[Client]`
- Heading: `[copy]`
- [Field]: `[copy]`
- [Field]: `[copy]`

#### [Section name]
<!-- Repeat for each section on this page -->

---

### About (`/about`)

#### Page Hero
`[Ayah]`
- Heading: `[copy]`
- Subheading: `[copy]`
- `[Image: [describe]]`

#### [Section name]
`[Client]`
- Heading: `[copy]`
- Body: `[copy]`

#### [Section name]
<!-- Repeat for each section -->

---

### Contact (`/contact`)

#### Page Hero
`[Ayah]`
- Heading: `[copy]`
- Subheading: `[copy]`

#### Contact Form
`[Ayah]`
- Form heading: `[copy]`
- Form intro: `[copy]`
- Fields:
  - Full name (required)
  - Phone number (required)
  - Email address (required)
  - [Dropdown label]: options: [Option 1], [Option 2], [Option 3]
  - Message (optional)
- Submit button: `[e.g. Send Message]`
- Success message: `[copy — e.g. Thank you! We'll be in touch within 24 hours.]`
- Error message: `[copy — e.g. Something went wrong. Please try again or call us directly.]`

#### Direct contact sidebar
`[Client]`
- Phone: `[phone]`
- Email: `[email]`
- Hours: `[hours]`
- Address (if applicable): `[address]`

---

### [Page name] (`/[slug]`)

<!-- Copy the page block above and fill in for each page in the sitemap -->

---

## CMS Collections

<!-- For each CMS collection: define the field schema, then provide one fully filled example.
     Developer follows the same pattern for remaining entries. -->

---

### [Collection name — e.g. Services]

**Fields per item:**
| Field | Type | Notes |
|-------|------|-------|
| Name | Text | Used in nav, cards, page title |
| Slug | Text | URL slug e.g. `/services/companion-care` |
| Short description | Text | Used on cards and overview page (~20 words) |
| Full description | Rich text | Used on individual service page |
| What's included | Rich text | Bulleted list of what the service covers |
| Who it's for | Rich text | Who benefits from this service |
| CTA heading | Text | e.g. "Ready to get started?" |
| CTA subtext | Text | Supporting line under CTA heading |
| [Add fields] | | |

**Example entry — [Item name]:**
- Name: `[e.g. Companion Care]`
- Slug: `[e.g. companion-care]`
- Short description: `[e.g. Friendly, consistent companionship for seniors who want social connection and support at home.]`
- Full description: `[copy]`
- What's included:
  - `[e.g. Conversation and social engagement]`
  - `[e.g. Accompaniment to appointments and errands]`
  - `[e.g. Light activities and hobbies]`
- Who it's for: `[copy]`
- CTA heading: `[copy]`
- CTA subtext: `[copy]`

---

### [Collection name — e.g. Locations]

**Fields per item:**
| Field | Type | Notes |
|-------|------|-------|
| City name | Text | |
| Slug | Text | URL slug e.g. `/service-areas/naperville` |
| State / region | Text | |
| Intro paragraph | Rich text | ~50–80 words, unique per city |
| Services offered | Reference | Link to Services collection |
| Why families choose us here | Rich text | Local-specific differentiator |
| [Add fields] | | |

**Example entry — [City name]:**
- City name: `[e.g. Naperville]`
- Slug: `[e.g. naperville]`
- Intro paragraph: `[copy]`
- Why families choose us here: `[copy]`

---

### [Collection name — e.g. Testimonials]

**Fields per item:**
| Field | Type | Notes |
|-------|------|-------|
| Quote | Rich text | The testimonial text |
| Attribution name | Text | e.g. "Sarah M." |
| Attribution detail | Text | e.g. "Daughter of a client" |
| Source | Text | e.g. "Google Review", "SeniorAdvisor" |
| Featured | Switch | Whether to show on homepage snippet |

**Example entry:**
- Quote: `[copy]`
- Attribution name: `[e.g. Sarah M.]`
- Attribution detail: `[e.g. Daughter of a client]`
- Source: `[e.g. Google Review]`
- Featured: `[Yes / No]`

---

## SEO

### Meta title + description — static pages

| Page | Meta title | Meta description |
|------|-----------|-----------------|
| Home | `[Client name] — [Short value prop] · [Location]` | `[~155 char description]` |
| About | `About [Client name] — [Short differentiator]` | `[~155 char description]` |
| Contact | `Contact [Client name] — [Location]` | `[~155 char description]` |
| [Page] | `[title]` | `[description]` |

### Meta title + description — CMS page patterns

| Collection | Title pattern | Description pattern |
|------------|--------------|---------------------|
| [e.g. Services] | `[Service name] — [Client name]` | `[~155 char description referencing the service and location]` |
| [e.g. Locations] | `[Service type] in [City] — [Client name]` | `[~155 char description referencing services available in that city]` |

### OG image
- Default OG image: `[Image file name / description]` — used when no page-specific image is set
- Dimensions: 1200 × 630px
