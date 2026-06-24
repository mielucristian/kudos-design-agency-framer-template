# AGENTS.md — Kudos

Instructions for AI agents working inside this project — Framer's native canvas Agent, and external agents (Claude Code, Cursor, Codex, or any MCP client) connected via Framer's MCP server.

This file does not describe what Kudos is for buyers — see `Readme.md` for that. This file describes how an agent should behave when asked to edit, extend, or restyle this specific project.

---

## 1. Project Summary

- **Template:** Kudos — premium Framer agency template
- **Pages:** 11 (8 static, 3 dynamic via CMS slugs)
- **CMS Collections:** 9 — Projects, Clients, Team Members, Services Categories, Services Tags, Jobs, Job Type, Articles, Legal
- **Breakpoints:** Desktop (1200px), Tablet (810px), Phone (390px) — all three exist for every page, agents must update all three when changing layout, not just Desktop
- **Hero background:** Native Framer Liquid Gradient shader effect on the `Hero` frame — not an image, not a video, not custom code

---

## 2. Before Making Any Change

1. Call `getProjectXml` first to confirm current page/component IDs — node IDs in this file are illustrative and may drift as the project evolves. Never assume an ID from documentation is still valid; verify it.
2. Call `getNodeXml` on the specific page or component before editing it. Do not guess child structure from this file alone.
3. Identify whether the target content lives on the **canvas** (hardcoded layer) or in the **CMS** (collection item). If it's CMS-bound, edit the CMS item, not the canvas layer — editing the canvas layer for CMS-bound text will be overwritten on next CMS sync.

---

## 3. Safe to Edit

Agents may freely modify:

- Text content inside any `Text` node that is not a CMS-bound field
- CMS collection items (adding, editing, removing rows) in all 9 collections
- Color Styles (`/Dark 2`, `/Light 98`, `/Turquoise 50`, etc.) — editing the style updates every layer that references it, which is the intended workflow
- Text Styles (`/Heading 1`, `/Heading 2`, `/Subheadline Light`, `/Quotes Medium`, `/Span`, etc.)
- Component instance properties exposed in the properties panel (e.g. `Statistic Card` "from"/"to"/suffix props, `Button` label/link props, `Process Stack` number/title/description props)
- Section order on the Home page — all top-level sections (`Hero`, `Intro`, `WhyChooseUs`, `Services`, `Process`, `FeaturedWork`, `Testimonials`, `Team`, `Pricing`, `Faq`, `Contact`, `Insights`) are siblings under `Main` and can be reordered safely
- Adding new pages via `createPage` (type `"web"`) for additional static content

---

## 4. Edit With Care

- **Shared components** (`Navbar`, `Footer`, `Big Logo`, `Button`, `Reviews`) are used across multiple pages and sections. An edit to the component definition propagates everywhere it's instanced. Before editing a shared component, confirm with the user whether they want a global change or a one-off override (in which case, detach the instance first via `?detached=true` on the insert URL).
- **CMS reference fields** (e.g. Projects → Clients, Projects → Team Members, Projects → Services Categories, Team Members → Services Categories, Articles → Team Members, Articles → Services Categories, Jobs → Job Type) must point to an existing item in the target collection. Do not create a reference to an item that doesn't exist yet — create the referenced item first.
- **Dynamic page routes** (`/projects/:slug`, `/articles/:slug`, `/jobs/:slug`, `/legal/:slug`) are generated from their CMS collection. Do not manually create a static page at a path that collides with a dynamic route pattern.
- **Grid layout components** (`Content` frames using `layout="grid"` with `gridColumns="4"`) follow a consistent 4-column system throughout the project. When adding new content blocks, match the existing `gridColumnSpan` conventions rather than introducing a new column count.

---

## 5. Do Not Touch Without Explicit Instruction

- The **Liquid Gradient shader** effect settings on the `Hero` frame — these were deliberately tuned. If asked to "make the hero background better" without specifics, ask what outcome is wanted rather than replacing the effect.
- The **Professional Usage License** content/PDF — this is a legal document delivered outside the Framer project. Never generate or alter license text from inside the canvas.
- The **`/legal/:slug`** CMS items' legal copy — flag to the user that legal text changes should be reviewed by them (or counsel), not auto-rewritten.
- **SEO/meta fields** at the project or page level — these are tied to live marketplace and search positioning. Confirm before bulk-editing.

---

## 6. Style & Content Conventions

- Headline copy in this template follows a consistent voice: short, declarative, two-line maximum (e.g. "We design brands people remember," "Positioned for lasting success," "Structure meets creative freedom"). New sections should match this tone, not introduce long marketing paragraphs in headline slots.
- Section eyebrow labels (e.g. "WHO WE ARE," "WHY CHOOSE US?," "PROCESS," "FEATURED PROJECTS," "SOCIAL PROOF") use the `SpanTitle` component, all caps, 1–3 words.
- Body copy under headlines uses `/Subheadline Light` or `/Subheadline Small` text styles depending on column width — match the existing pattern rather than introducing a new text style for similar content.
- Numbers in stat components always include a "from" value (usually a smaller, rounder number) and animate up to the "to" value — don't set "from" equal to "to," it disables the count-up effect.

---

## 7. When Asked to Add New Sections

1. Check whether an existing component already covers the request (e.g. don't build a new bento grid from scratch if `WhyUsBentos` already exists and can be reused/duplicated).
2. New sections should be inserted as a sibling `Frame` under `Main`, following the existing `backgroundColor`, `Grids` decorative overlay, and `Divider` pattern used by every other section (see any section in `getNodeXml` on the Home page for the pattern: background → `Grids` decorative layer → `Content` grid → optional `Divider`).
3. Reuse existing CMS collections where the content type already exists. Only propose a new CMS collection if the content genuinely doesn't fit any of the 9 existing ones.

---

## 8. Reporting Back

After any multi-step change, summarize in plain language:
- What was changed (and on which breakpoints)
- Whether any CMS items were created, edited, or referenced
- Whether any shared component was modified (and therefore affects other pages)

This matches how the human collaborator on this project works — they review every AI-assisted change before publishing, per Framer's Agents + Branching workflow.
