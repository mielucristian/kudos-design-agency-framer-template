# Kudos — Documentation

**Premium Framer Agency Template**
*"We design brands people remember."*

This document is both an overview and a working manual — everything you need to understand what's inside Kudos, how it's structured, and how to make it yours.

🔗 Live preview: [kudos.framer.media](https://kudos.framer.media/)
🛒 Marketplace: [framer.com/marketplace/templates/kudos](https://www.framer.com/marketplace/templates/kudos/)
✉️ Support: [@CristianMielu](https://twitter.com/CristianMielu) on X — usually a reply within 24h

---

## Table of Contents

1. [Overview](#1-overview)
2. [Getting Started](#2-getting-started)
3. [Page-by-Page Guide](#3-page-by-page-guide)
4. [Homepage, Section by Section](#4-homepage-section-by-section)
5. [The CMS, In Depth](#5-the-cms-in-depth)
6. [Customization Guide](#6-customization-guide)
7. [The Liquid Gradient Shader](#7-the-liquid-gradient-shader)
8. [License](#8-license)
9. [FAQ](#9-faq)
10. [Support](#10-support)

---

## 1. Overview

Kudos is a premium Framer template for design studios, creative agencies, startups, and professional services. It's built around three ideas:

- **Editorial confidence** — bold typography, a dark hero, and an oversized wordmark that makes a statement before a single word is read.
- **Real agency structure** — not a generic "business template," but pages and CMS collections modeled on how studios actually present their work: projects, case studies, team, jobs, articles.
- **Zero-friction customization** — every section is a standard Framer component or CMS-bound layer. Nothing is hardcoded, nothing requires code.

**At a glance:**

| | |
|---|---|
| Pages | 11 (8 static, 3 dynamic) |
| CMS Collections | 9 |
| Components | 60+ reusable components |
| Breakpoints | Desktop, Tablet, Phone |
| Hero background | Liquid Gradient shader (Framer native) |
| License | Professional Usage License (signed, included) |

---

## 2. Getting Started

1. **Remix or buy** the template from the [Framer Marketplace listing](https://www.framer.com/marketplace/templates/kudos/).
2. **Open the project** in Framer. The Home page (`/`) is the default focused page.
3. **Replace the placeholder content first**, in this order, for the fastest visible progress:
   - Hero headline and subheadline (Home page)
   - Your logo (`Big Logo` component, used across multiple sections)
   - Stat numbers in the "Who We Are" section
   - Your first 2–3 CMS items in **Projects** and **Team Members** (see [Section 5](#5-the-cms-in-depth))
4. **Update the Navbar and Footer** — both are shared components, so editing them once updates every page.
5. **Review the Legal page content** in the **Legal** CMS collection before publishing — the placeholder text is for layout reference only and is not legal advice.
6. **Publish.**

If you only have 30 minutes: swap the hero text, your logo, and your first 3 projects. That alone gets you 80% of the way to a site that feels like yours.

---

## 3. Page-by-Page Guide

| Page | Path | Type | What it pulls from the CMS |
|---|---|---|---|
| Home | `/` | Static | Projects (featured), Team Members (quote + studio link) |
| About | `/about` | Static | Team Members |
| Projects | `/projects` | Static, CMS list | Projects, Services Categories (for filtering) |
| Project detail | `/projects/:slug` | Dynamic | Projects, Clients, Team Members, Services Categories |
| Articles | `/articles` | Static, CMS list | Articles, Services Categories |
| Article detail | `/articles/:slug` | Dynamic | Articles, Team Members (Author) |
| Jobs | `/jobs` | Static, CMS list | Jobs, Job Type |
| Job detail | `/jobs/:slug` | Dynamic | Jobs, Job Type |
| Contact | `/contact` | Static | — (form only) |
| Legal | `/legal/:slug` | Dynamic | Legal |
| 404 | `/404` | Static | — |

Dynamic pages (`:slug`) automatically generate one page per CMS item — add a new Project, and a new `/projects/your-new-project` page is created for you. No manual page building required.

---

## 4. Homepage, Section by Section

The homepage is built as a continuous, scroll-driven story — each section earns the next one rather than just sitting next to it.

### Hero
A sticky, full-viewport section ("We design brands people remember") that stays pinned to the top while the next section rises over it. The background runs on Framer's **Liquid Gradient shader** instead of a static image or video file — see [Section 7](#7-the-liquid-gradient-shader) for how to adjust it. A social-proof cluster (avatars + rating, via the `Reviews` component) and a "Let's collaborate" button sit beside the headline. The oversized "KUDOS" wordmark anchors the bottom of the viewport via the `Big Logo` component — the same component reused (in a different color) further down the page.

### Who We Are
*"Aligned with your mission."* A founder quote (`Profile` component), a horizontally scrolling client logo ticker (`Ticker — Clients`), and four animated stat cards (`Statistics` component) — Brands, Launches, Users, Speed — that count up into view as you scroll. Each card has a "from" and "to" number plus a suffix (`%`, `M+`, etc.) — all editable as plain text properties, no code.

### Why Choose Us
*"Positioned for lasting success."* A scroll-triggered text reveal (`Text Reveal Content`) sits above a `Why Us Bentos` grid component — a bento-style layout that would normally be hand-built per-project, here it's a single drop-in component.

### Services
A dedicated section (`Services` component) that connects directly to the **Services Categories** CMS collection — add a category there, it appears here automatically.

### Process
*"Structure meets creative freedom."* Four `Process Stack` components in sequence (Discover → Design → Build → Launch), each with a number, title, description, and outcome line. Below that, a 3-column breakdown using the `Project Experience Card` component ("What to expect / What you get / What it takes").

### Featured Work
*"Created with clear purpose."* A sticky left column — founder quote + four `Statistic Card` components (Brands, Launches, Users, Speed) — stays pinned while a scrolling list of `Project Card` components (pulled live from the **Projects** collection) moves past it on the right.

### Testimonials
*"Trusted by great teams."* A `Client Quotes Stack` plus a horizontally scrolling `Ticker` of `Client Testimonial` components — all CMS-managed via the **Clients** collection.

### Team
Pulls directly from the **Team Members** collection via the `Team` component.

### Pricing
A standalone `Pricing` component for service-based offers — edit plans, prices, and feature lists directly.

### FAQ
An accordion-style `FAQ` component. Each question/answer pair is editable inline.

### Contact
A full `Contact Form` component, ready to wire up to your inbox or CRM.

### Insights
A live preview of your most recent **Articles**, via the `Insights` component.

---

## 5. The CMS, In Depth

Kudos ships with **9 connected CMS collections**. Understanding how they reference each other is the key to managing content without ever touching layout.

### Projects
Your case studies. The most connected collection in the project.

| Field | Type | Notes |
|---|---|---|
| Title, Subtitle, Meta Description | Text | |
| Thumbnail, Image 01–03 | Image | |
| Featured | Boolean | Controls homepage visibility |
| Client | Reference → **Clients** | One client per project |
| Team Members | Multi-reference → **Team Members** | Who worked on it |
| Categories | Multi-reference → **Services Categories** | Powers filtering on `/projects` |
| Year, Duration | Text | |
| Website, Website Link, Buy/Remix, Buy/Remix Button Text | Text/Link | Optional CTAs on the project page |
| Intro, Important, Approach, Vision and Innovation, Identifying Unique Challenges, Resolving Complex Problems, User-Centric Design, Meeting User Needs, Detailed Pages and Features, Accessibility and Optimization, Conclusions | Rich text | A full case-study narrative structure — use as many or as few as the project needs |

### Clients
Logos, the person quoted, and their stats — referenced by **Projects** and surfaced on the Testimonials section.

### Team Members
Each member has a Title, Role, Image, Quotes, X/LinkedIn links, and a **Skills** multi-reference to **Services Categories** — so a team member's expertise links back to the services they're associated with. Also referenced by **Articles** (as Author).

### Services Categories
The core of your offering. Each category has a Title, Number, Image, rich-text Content, and a **Services Tags** multi-reference.

### Services Tags
A lightweight supporting collection, referenced by **Services Categories** for filtering/labeling.

### Jobs
Career listings — Title, salary ranges for Full Time / Freelance / Intern, a **Job Type** multi-reference, and rich-text Short Description + Requirements.

### Job Type
Supporting reference collection for **Jobs** (e.g. Full-time, Freelance, Internship).

### Articles
Your blog/insights. Title, Meta Description, Date, read time, an **Author** reference → **Team Members**, Main Photo, Photo 1, a **Categories** multi-reference → **Services Categories**, and Intro + Content rich text.

### Legal
Privacy Policy, Terms, and any other legal page — Title, Effective Date, Intro, and Content. Fully editable from the CMS; no design changes needed to update legal copy.

**The pattern to remember:** Projects ↔ Clients, Projects ↔ Team Members, Projects ↔ Services Categories, Team Members ↔ Services Categories, Articles ↔ Team Members, Articles ↔ Services Categories, Jobs ↔ Job Type. Once you see the pattern, adding new content is just filling in a form.

---

## 6. Customization Guide

**Changing the hero headline** — open the Home page, select the text layer under `Hero → HeaderMainContent → HeaderContent → Header`, and type. The text style is `/Heading 1` — change it on the style itself to update it everywhere it's used.

**Changing colors** — Kudos uses project-wide Color Styles (`/Dark 2`, `/Turquoise 50`, `/Light 98`, etc.). Update a Color Style once and every layer using it updates automatically. Don't recolor layer-by-layer.

**Adding a new project** — go to the CMS panel → **Projects** → add a new item. Fill in at minimum a Title, Thumbnail, and Client. The `/projects/:slug` page is generated automatically.

**Filtering projects by category** — the `/projects` page uses the **Categories** multi-reference field on Projects together with a dropdown filter component reading from **Services Categories**. Add a category to a project, and it becomes filterable instantly — no new logic required.

**Editing the stat counters** — each `Statistic Card` instance has plain-text "from" and "to" number properties plus an optional suffix. Update the properties panel; the count-up animation adjusts automatically.

**Swapping the Navbar/Footer** — both are shared components (`Navbar`, `Footer`). Edit the component once (double-click to enter it) and the change applies across all 11 pages.

**Reordering homepage sections** — every section on the Home page (Hero, Who We Are, Why Choose Us, Services, Process, Featured Work, Testimonials, Team, Pricing, FAQ, Contact, Insights) is a top-level child of `Main` — drag to reorder in the Layers panel.

---

## 7. The Liquid Gradient Shader

The hero background uses Framer's native **Liquid Gradient** shader — a built-in effect, not a video file or custom code.

- Select the `Hero` frame and open the **Effects** panel.
- Adjust colors directly — the shader respects your project's Color Styles.
- Motion speed and scale are adjustable sliders, no keyframing required.
- Because it's a native shader (not a video), it loads faster, performs better on mobile, and never buffers.

If you prefer a static background, you can disable the shader effect and set a solid `backgroundColor` or `backgroundImage` on the same `Hero` frame instead.

---

## 8. License

Every purchase includes a signed **Professional Usage License**:

- Authorizes commercial use, including client projects and business initiatives
- One user/entity per license
- No redistribution or reselling of the template itself
- Modifications allowed

---

## 9. FAQ

**Do I need to know how to code?**
No. Every customization described in this document is done through Framer's visual editor — text, properties panel, CMS forms, and Color/Text Styles.

**Can I remove pages or sections I don't need?**
Yes. Every section on the homepage and every page in the Pages panel can be deleted or hidden without breaking the rest of the template.

**What happens if I add more than the existing CMS items?**
Nothing breaks — collections are unlimited. Add as many Projects, Team Members, or Articles as you need.

**Is the documentation only available before purchase?**
The full documentation lives inside the project (Design page → "Documentation") and is also available here for buyers and prospective buyers alike — what matters more than reading every section up front is knowing it's there when you need it.

---

## 10. Support

Questions before or after buying? Reach out via [@CristianMielu](https://twitter.com/CristianMielu) on X, or by email — usually a reply within 24h.

---

Built by [Cristian Mielu](https://uihub.design) — Framer Partner & Template Creator.
