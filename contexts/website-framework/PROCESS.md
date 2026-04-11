# Sacra Website Framework — Master Process

Every client website project follows this 7-phase process. Each phase has a defined output, owner, and approval checkpoint. Nothing moves forward without the previous phase being complete and (where required) approved.

---

## Phase Overview

| # | Phase | Output | Client approval? |
|---|-------|--------|-----------------|
| 1 | Discovery | `CLIENT-PROPOSAL.md` | Yes — sign-off + payment |
| 2 | Early Dev Handoff | `DEV-BRIEF.md` | No |
| 3 | Brand | `BRAND.md` | Yes |
| 4 | Design | Figma file + `DESIGN-CHECKLIST.md` | Yes |
| 5 | Content | `CONTENT.md` | Yes |
| 6 | Final Dev Handoff | Full package to developer | No |
| 7 | Review + Launch | Live site | Yes (staging) |

**Parallel work:** Phases 3–5 (Brand, Design, Content) happen while the developer is working from the Phase 2 DEV-BRIEF. Time is not wasted waiting.

---

## Phase 1 — Discovery

**Owner:** Ayah
**Output:** `CLIENT-PROPOSAL.md`
**Template:** `CLIENT-PROPOSAL-template.md`

### Steps
- [ ] Run discovery call with client
  - Goals + objectives for the new site
  - Current website pain points
  - Target audiences
  - Services/offerings
  - Existing brand assets (logo, colors, fonts)
  - Competitor sites + visual references they like/dislike
- [ ] Post-discovery: draft CLIENT-PROPOSAL.md
  - Synthesize discovery notes into a clean proposal
  - Build proposed sitemap
  - Define scope (what's in, what's explicitly out)
  - Set timeline and budget
- [ ] Send CLIENT-PROPOSAL.md to client for review
- [ ] **Client signs off and pays — do not proceed until both are complete**

### Notes
- Default exclusions (add to every proposal unless explicitly in scope): blog, e-commerce, login/member portal, multi-language, online booking/scheduling, payment processing
- The sitemap at this stage is a working draft — it will be finalized before the Final Dev Handoff

---

## Phase 2 — Early Dev Handoff

**Owner:** Ayah → Developer
**Output:** `DEV-BRIEF.md`
**Template:** `DEV-BRIEF-template.md`

### Steps
- [ ] Draft DEV-BRIEF.md from the approved CLIENT-PROPOSAL
  - Flag which pages are static vs. CMS-driven
  - List CMS collection names (developer handles field schema)
  - Note any integrations (forms, analytics, third-party tools)
- [ ] Send DEV-BRIEF.md to developer
- [ ] Developer begins Webflow setup
  - Page shells
  - CMS collections + field schema
  - Style variables (colors, fonts, spacing)
- [ ] **Get developer feedback on CMS structure and page architecture before proceeding**

### Notes
- The developer is a collaborator, not just an executor — loop them in early and ask for their input
- The developer does NOT make design decisions at this stage — visual work has not started yet
- Style variables set up by the developer will be populated with actual brand values after Phase 3

---

## Phase 3 — Brand

**Owner:** Ayah
**Output:** `BRAND.md`
**Template:** `BRAND-template.md`

### Steps
- [ ] Audit client's existing brand (logo, colors, fonts, current site)
- [ ] Identify what's working, what needs updating, what to drop
- [ ] Define updated brand direction: positioning, colors, typography, voice, imagery, design patterns
- [ ] If logo refresh is in scope: brief the logo work and confirm deliverable formats
- [ ] Draft BRAND.md
- [ ] **Client approves BRAND.md before Design begins**

### Notes
- Every client comes in with an existing brand — this is always a refresh, not a blank-slate build
- The Design Patterns section of BRAND.md feeds directly into Figma — complete it before opening the design file
- Developer updates Webflow style variables once BRAND.md is approved

---

## Phase 4 — Design

**Owner:** Ayah
**Output:** Figma file + `DESIGN-CHECKLIST.md`
**Template:** `DESIGN-CHECKLIST-template.md`

### Steps
- [ ] Open Figma with approved BRAND.md as reference
- [ ] Create wireframes — rough layouts of each section type (structure only, no brand applied)
- [ ] Create high-fidelity designs — apply brand (colors, fonts, imagery direction)
- [ ] Finalize component/section library
- [ ] Draft DESIGN-CHECKLIST.md
  - List all sections designed
  - Build page assembly map (which sections go on which page, in order)
  - Document component specs (buttons, forms, cards, etc.)
- [ ] **Client approves Figma designs before Content begins**

### Notes
- Design reusable sections and components — not full pages. The dev assembles pages from sections.
- Section names in Figma must match section names in DESIGN-CHECKLIST.md and CONTENT.md
- The developer builds what is designed — they do not make visual decisions

---

## Phase 5 — Content

**Owner:** Ayah + Client (collaborative)
**Output:** `CONTENT.md`
**Template:** `CONTENT-template.md`

### Steps
- [ ] Resolve image sourcing: who is providing photos — Ayah sources or client provides?
  - If Ayah sources: license and collect before writing content
  - If client provides: set a deadline for delivery
- [ ] Send CONTENT-template.md to client with [Client]-tagged sections highlighted
- [ ] Client fills in their sections
- [ ] Ayah writes [Ayah]-tagged sections
- [ ] Ayah reviews and refines all copy for consistency and brand voice
- [ ] Finalize CONTENT.md
- [ ] **Client approves CONTENT.md before Final Dev Handoff**

### Notes
- Copy is written to fit the approved Figma layouts — design is locked before writing starts
- Section names must match Figma component names and DESIGN-CHECKLIST.md
- CMS-driven page types: write the field schema + one filled example; dev follows the same pattern for remaining entries

---

## Phase 6 — Final Dev Handoff

**Owner:** Ayah → Developer
**Output:** Complete handoff package

### Steps
- [ ] Confirm all client approvals are in place (BRAND, Figma, CONTENT)
- [ ] Confirm image sourcing is resolved — all assets in hand
- [ ] Package and send to developer:
  - [ ] `BRAND.md`
  - [ ] Figma file link
  - [ ] `DESIGN-CHECKLIST.md`
  - [ ] `CONTENT.md`
  - [ ] Assets folder: logos (SVG full, SVG white, PNG transparent, favicon) + all imagery
- [ ] Brief the developer on the handoff — walk through the page assembly map

### Developer's job from here
- Build each section/component in Webflow to Figma spec
- Assemble pages using the DESIGN-CHECKLIST page assembly map
- Enter CMS content from CONTENT.md into Webflow collections
- Apply all page copy from CONTENT.md

---

## Phase 7 — Review + Launch

**Owner:** Developer → Ayah → Client
**Revisions:** Up to 2 rounds from Ayah, up to 2 rounds from client

### Steps
- [ ] Developer runs pre-launch checklist before sharing anything
  - [ ] All forms submitting correctly
  - [ ] Site is fully mobile responsive
  - [ ] SEO meta titles + descriptions on every page
  - [ ] Favicon set
  - [ ] 404 page exists
  - [ ] Analytics connected
  - [ ] All internal + external links working
- [ ] Developer shares staging link
- [ ] Ayah reviews build against Figma + CONTENT.md
  - [ ] Sections match Figma designs
  - [ ] All copy matches CONTENT.md exactly
  - [ ] Images placed correctly
  - [ ] CMS entries complete and correct
- [ ] Developer fixes Ayah's feedback
- [ ] Repeat Ayah review if needed (max 2 rounds total)
- [ ] Client reviews staging — client always sees the most complete, ready version
- [ ] Developer fixes client feedback
- [ ] Repeat client review if needed (max 2 rounds total)
- [ ] **Launch**
  - [ ] Webflow publish
  - [ ] Custom domain connected
  - [ ] SSL confirmed
- [ ] Post-launch smoke check — confirm everything is live and working
- [ ] CMS handoff (if applicable) — walk client through Webflow CMS so they can manage their own content
