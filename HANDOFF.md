# HANDOFF — Social Health Systems Website

> **You are Claude, continuing work on the Social Health Systems website. Read this whole document before acting.**

---

## ★ ORIGINAL GOAL (read first)

**Help socialhealthsystems.com rank higher in search by building brand-accurate SEO pages and on-site SEO improvements — and let the site owner (Fred) review every change before it goes live.**

Everything below serves that goal. The two hard rules that fall out of it:
1. **Brand accuracy beats volume.** A page that contradicts the live homepage hurts ranking and trust. Match the live brand exactly (see "Brand Source of Truth").
2. **Never publish directly.** Build on a branch, open a PR, and let Fred merge. He reviews before anything is live.

---

## 1. Project facts

- **Repo:** `samoanfro/Social-Health-Systems-3` (public)
- **Live URL:** https://socialhealthsystems.com
- **Hosting:** GitHub Pages, deploys automatically from the **`main`** branch.
- **Custom domain:** set via `CNAME` file (`socialhealthsystems.com`). `www` is a DNS CNAME → `samoanfro.github.io`.
- **`.nojekyll`** is present and must stay — it stops Jekyll from breaking inline assets.
- **Dev branch:** `claude/epic-albattani-KV7eo` (push here, open PRs into `main`).
- **Tech:** static HTML/CSS/JS. No build step, no framework. Each page is one self-contained `.html` file with inline `<style>` and inline SVG. Fonts load from Google Fonts (Inter Tight, Source Serif 4, JetBrains Mono).
- **Search Console:** domain property `socialhealthsystems.com` is **verified** (TXT record on `@`). `sitemap.xml` has been **submitted**.

### Environment constraints for you (Claude)
- **No outbound network.** You cannot fetch the live site (requests return `403 host_not_allowed`). To read what's actually deployed, use the **GitHub MCP tools** (`get_file_contents` on `refs/heads/main`) or read the local working tree.
- **Do not open a PR unless asked**, but Fred's standing workflow is review-via-PR, so for approved changes: branch → commit → push → open PR → tell him to merge.
- GitHub Pages deploy status is visible via the **Actions** workflow `pages build and deployment` (check `conclusion: success` for the merge commit).

---

## 2. Brand Source of Truth (CRITICAL — do not get this wrong)

The **live site is canonical.** An earlier "SEO content doc" was provided that **contradicted** the live brand; it was rejected. Use the live facts below. **Do NOT reintroduce the rejected terms.**

| Topic | ✅ USE (live brand) | ❌ DO NOT USE (rejected doc) |
|---|---|---|
| Framework | **Four Pillars** | "Five Foundations" |
| The pillars | Connection Before Concern · Connection Currency™ · Statements Before Questions · Relational Response to Mental Health™ | — |
| Accreditation | **SHa**, 3 tiers: White (Spark) · Purple (Root) · Black (Legacy) | 5-belt White→Black system |
| Founder | **David Kozlowski**, sole founder | extra co-founders (Fred Siaosi, Larry Tiejan, Kenneth Scott) |
| Tenure | **26 years** in mental health · **15 years** building the framework (since 2011) | "16 years" |
| Measurement | 60-second Social Health diagnostic (on homepage) | "SHA assessment", "Manual Factory" |

**Founder facts (for E-E-A-T / Person schema):** David Kozlowski — LMFT (California & Utah), M.S. Counseling Psychology (National University), 26 yrs mental health & crisis intervention. Host of **OG Therapy** podcast, TEDx speaker, author of *Youth of the Nation* (and *Corporations of the Nation*, forthcoming). Origin: Carlsbad CA, raised by Samoan/Hawaiian grandmother, Univ. of Utah football, 1995 suicide attempt → saved by therapy.

**Other brand vocabulary:** Social Connection Collapse · Connection Currency™ · Social Cardio · Connection Confidence™.

**Proof points:** Herriman High School — reported suicidal ideation dropped **155 → 5** after the **Level Up** curriculum; community lost 7 students to suicide in 2017; 91% of ideation traced to relationship breakdown.

**Non-profit:** Social Health Initiative (SHi), 501(c)(3), https://www.socialhealthinitiative.org — every donated dollar goes here.

**Tagline:** "Connection Is Infrastructure™".

---

## 3. Page template & conventions

When building a new page, **copy the structure of an existing subpage** (`what-is-social-health.html`, `framework.html`, `about.html`, or `healthcare.html`). They share one stylesheet block.

Required `<head>` for every page (SEO):
- `<title>` (keyword-led, ends with "| Social Health Systems")
- `<meta name="description">`
- `<link rel="canonical">` (page's own absolute URL)
- Open Graph: `og:type`, `og:url`, `og:title`, `og:description`, `og:site_name`, `og:locale`
- Twitter: `twitter:card=summary_large_image`, `twitter:title`, `twitter:description`
- JSON-LD `<script type="application/ld+json">` — `Article` for content pages, `FAQPage` if it has a FAQ, `AboutPage`+`Person` for About, `Service` for accreditation.

Layout components (CSS classes already defined): `.nav` (brand + "← Back to Home"), `.page-hero` (`.page-eyebrow`, `.page-title` with `<em>`, `.page-sub`), `.content` (`.tag`, `h2` with `<em>`, `p`, `blockquote`, `.section-divider`, `ul`), `.cta-band`, `.footer`.

**Design tokens** (CSS `:root`): green `#0a5c44`, gold `#b3853a`, ink `#0f1311`, bg `#ffffff`/`#f7f7f5`. Fonts via `--f-display` (Inter Tight), `--f-serif` (Source Serif 4), `--f-mono` (JetBrains Mono).

**File/URL convention:** flat `.html` files at repo root (e.g. `framework.html`). Link with the `.html` extension. No subdirectories.

**Internal linking:** every new page must (a) link to 2–3 related pages, and (b) be linked FROM somewhere (homepage footer and/or top nav) so it isn't orphaned. **Add new public pages to `sitemap.xml`.**

**Validation before committing:** confirm HTML parses, every JSON-LD block is valid JSON, `sitemap.xml` is valid XML, and all internal `href="*.html"` targets exist on disk.

---

## 4. Work completed so far

- **PR #1 (merged):** Contact page — form now submits via `mailto:` (no Formspree); "Book a Call" → Google Calendar scheduler `https://calendar.app.google/Qd5DaC5wspfv7H7n7`.
- **PR #2 (merged):** Open Graph/Twitter/canonical meta tags + missing descriptions across all subpages. Added **3 new pages** — `what-is-social-health.html` (Article+FAQPage), `framework.html` (Four Pillars, Article), `about.html` (AboutPage+Person). Added `sitemap.xml` + `robots.txt`. Wired new pages into homepage **footer**.
- **PR #3 (OPEN — awaiting Fred's merge):** Adds the new pages to the homepage **top nav** → `Framework · Social Health · How SHs Differs · About · Voices · Diagnostic · Media`. https://github.com/samoanfro/Social-Health-Systems-3/pull/3
- **Off-site:** Search Console domain verified; `sitemap.xml` submitted (showed "Couldn't fetch" right after submit — this is normal Google lag, not a defect; it self-resolves).

### Current pages (all live unless noted)
`index.html` (homepage) · `what-is-social-health.html` · `framework.html` · `about.html` · `accreditation.html` · `schools.html` · `enterprise.html` · `healthcare.html` · `community.html` · `contact.html` · `article-dei-to-shs.html` · `article-360b-problem.html` · `article-herriman.html` · plus `sitemap.xml`, `robots.txt`, `CNAME`, `.nojekyll`, `favicon.svg`.

---

## 5. Open items / next steps

1. **Merge PR #3** (Fred) → top-nav goes live.
2. **Confirm sitemap "Success"** in Search Console after ~1–2 days; optionally "Request Indexing" for the 3 new pages.
3. **Backlog (build brand-accurate, same template, then PR):**
   - SHa Accreditation deep-dive page (3-tier process, `Service`+`FAQPage` schema).
   - Enterprise/curriculum page consistent with the **Four Pillars** + **SHa tiers** (NOT a 5-belt system).
   - More articles (link from the homepage "Insights" section).
   - Add an `og:image` (1200×630) for richer social/link previews (homepage has placeholders commented out).
   - Periodically check **Search Console → Pages** that new URLs are indexed.

---

## ★ ORIGINAL GOAL (read last)

**Help socialhealthsystems.com rank higher in search by building brand-accurate SEO pages and on-site SEO improvements — and let Fred review every change before it goes live.**

If a request would force a choice, prefer: **brand accuracy > SEO completeness > speed.** Never ship copy that contradicts the live brand, and never merge to `main` yourself.
