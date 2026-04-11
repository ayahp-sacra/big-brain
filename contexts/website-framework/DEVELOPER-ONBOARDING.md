# Developer Onboarding — Sacra Projects

Hey! Welcome to a Sacra project. This doc walks you through how we work so you know exactly what to expect, what you'll receive, and what's expected of you at each stage.

Read this once before your first project. It'll make everything else make sense.

---

## How Sacra Projects Work

Sacra handles discovery, brand, design, and content. Your job is to build what gets handed to you — accurately and cleanly. You won't be making design decisions. You'll receive a Figma file with every section and component designed, a content doc with every word spelled out, and a checklist that tells you exactly which sections go on which page.

The goal is a clean handoff in both directions: you get everything you need to build without guessing, and Ayah gets a build that matches the spec.

---

## Your Role

**You are the builder, not the designer.**

- Ayah designs all sections and components in Figma
- You build them in Webflow to match the design exactly
- You do not make visual decisions — if something is unclear, ask before interpreting
- You do make technical decisions — CMS field schema, Webflow structure, performance optimizations

**You are also a collaborator, not just an executor.**

- You get looped in early, before design and content are done
- Your feedback on CMS structure and page architecture is genuinely wanted at that stage
- If you see a problem early, say so — it's much easier to fix before anything is built

---

## The Project Lifecycle

Here's where you fit into the full process:

```
Phase 1 — Discovery         (Ayah + Client)
Phase 2 — Early Dev Handoff ← YOU START HERE
Phase 3 — Brand             (Ayah)
Phase 4 — Design            (Ayah)
Phase 5 — Content           (Ayah + Client)
Phase 6 — Final Dev Handoff ← YOU BUILD HERE
Phase 7 — Review + Launch   ← YOU LAUNCH HERE
```

---

## Phase 2 — Early Dev Handoff

**What you receive:** `DEV-BRIEF.md`

This comes to you before brand, design, or content are finished. It gives you enough to set up the Webflow project structure so that work isn't blocked waiting for you.

**Your job at this stage:**
- Set up the Webflow project
- Create all page shells (one per page in the sitemap)
- Set up CMS collections (DEV-BRIEF lists the collections; you define the field schema)
- Set up style variables for colors, fonts, and spacing (values will be filled in once BRAND.md is approved)

**Please do:**
- Review the sitemap and CMS collections and flag any concerns
- Share feedback on page architecture or CMS structure before building anything
- Ask questions early — this is the cheapest time to solve problems

**Please don't:**
- Make visual decisions or style choices at this stage — brand isn't finalized yet
- Start building sections or UI — wait for the Figma file

---

## Phase 6 — Final Dev Handoff

**What you receive:**
- `BRAND.md` — full design system (colors, fonts, spacing, design patterns)
- Figma file link — every section and component designed, ready to build
- `DESIGN-CHECKLIST.md` — the page assembly map (which sections go on which page, in order)
- `CONTENT.md` — all copy, word for word; CMS content structured and ready to enter
- Assets folder — logos (SVG, PNG, favicon) and all imagery

**Your job at this stage:**
- Update Webflow style variables with the final brand values from BRAND.md
- Build each section/component in Webflow to match the Figma design
- Assemble pages using the page assembly map in DESIGN-CHECKLIST.md
- Enter CMS content from CONTENT.md into Webflow collections
- Apply all page copy from CONTENT.md exactly as written — do not rewrite or paraphrase

---

## How to Use the Figma File

- Every section and component is designed and named
- Section names in Figma match section names in DESIGN-CHECKLIST.md and CONTENT.md — use these names consistently
- If a section has variants (e.g. "Split — text left" and "Split — image left"), they are separate components in Figma
- Specs for buttons, forms, cards, icons, and typography are in DESIGN-CHECKLIST.md
- If anything in Figma is ambiguous, ask before interpreting it

---

## How to Use CONTENT.md

- Copy is organized as: **Page → Section → Field**
- Section names match Figma exactly
- Enter copy exactly as written — do not rewrite, trim, or paraphrase
- `[Image: description]` notes tell you where images go — use the supplied assets
- CMS content is structured with a field template + one filled example; enter the rest following the same pattern
- SEO meta titles and descriptions are at the bottom of the document — apply to every page

---

## Webflow Conventions

- **Style variables first** — set up all color, font, and spacing variables before building any sections; never hardcode values
- **Components for everything** — every section should be a Webflow component so changes propagate globally
- **CMS for dynamic content** — anything that repeats (services, locations, testimonials, team members) lives in a CMS collection, not hardcoded
- **Mobile-first** — build and check mobile at every step, not as a final pass
- **Clean class names** — use descriptive, consistent class names that match section names from the Figma file

---

## Phase 7 — Review + Launch

**Before sharing anything with Ayah, run the pre-launch checklist yourself:**

- [ ] All forms submitting correctly and sending email notifications
- [ ] Site fully mobile responsive (check at 375px, 768px, 1280px minimum)
- [ ] SEO meta title + description set on every page
- [ ] Favicon uploaded and displaying
- [ ] 404 page exists and is styled
- [ ] Analytics connected and tracking
- [ ] All internal links working (no broken links)
- [ ] All external links opening in a new tab
- [ ] Page load speed reasonable (Lighthouse 90+ target)

**Then share the staging link with Ayah.**

Ayah will review against the Figma designs and CONTENT.md. Expect up to 2 rounds of feedback from Ayah, then up to 2 rounds from the client. Address feedback specifically and completely each round.

**Launch checklist (once all reviews are done):**
- [ ] Webflow publish
- [ ] Custom domain connected
- [ ] SSL confirmed and active
- [ ] Post-launch: confirm everything is live and working correctly

---

## Communication Norms

- **Flag blockers early** — if you're waiting on something or something doesn't make sense, say so immediately rather than working around it
- **Ask before interpreting** — if the Figma or content doc has an ambiguity, ask Ayah rather than making a call yourself
- **Share staging proactively** — if you hit a milestone or want a gut-check, share a staging link; don't wait until everything is perfect
- **Be specific in questions** — include a screenshot or link to the specific element you're asking about

---

## Quality Bar

Every project ships to these standards:

| Area | Standard |
|------|----------|
| Accessibility | WCAG 2.1 AA — alt text, contrast ratios, form labels, keyboard nav |
| Mobile | Fully responsive from 375px; tested on real device or emulator |
| Performance | Lighthouse 90+ on all pages |
| SEO | Unique meta title + description on every page; OG tags; structured data where applicable |
| Copy accuracy | Every word on the site matches CONTENT.md exactly |
| Design accuracy | Every section matches the Figma design — spacing, color, typography, layout |

---

## Questions?

Reach out to Ayah at [email] for anything related to design, content, or scope.
If you find a technical issue or have an architecture suggestion, bring it up early and directly.

We're glad to have you on the project.
