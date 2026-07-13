# The Atlantean Chronicle

> *"Where the signal rises above the noise."*

The weekly newspaper-style intelligence brief published by **Atlantis ITS** at
**[news.atlantisits.info](https://news.atlantisits.info)**. Each issue is a single,
self-contained HTML file — a print-newspaper layout covering International, National,
Local (Metro Atlanta / Hall County), Travel, Tech & AI, prediction markets, and an
Atlantis operations section.

- **Publisher:** Atlantis Intelligence Technology Solutions · Metro Atlanta, GA
- **Cadence:** Weekly — Weekend Edition (Fri–Sun)
- **Volume/Issue:** Vol. I · No. *N* (increments each week)
- **Current issue:** **No. 12** — Weekend Edition, July 10–12, 2026
- **Hosting:** Static site on Vercel (no build step — plain HTML/CSS, Google Fonts + local images)

---

## Repository layout

```
atlantis-news/
├── index.html                          # LIVE current issue — a mirror of the latest No. N
├── atlantean-chronicle-vol1-no12.html  # Canonical file for the current issue
├── atlantean-chronicle-vol1-no8..11.html   # Recent issues (kept in root)
├── CHRONICLE_PROJECT_SYSTEM_PROMPT.md  # ★ Canonical build spec — read before every build
├── README.md                           # This file
├── pics/                               # Shared image assets (see Images below)
└── archive/
    ├── atlantean-chronicle-vol1-no1..7.html   # Older issues
    ├── Chronicle-No8-Briefing.md              # Build/briefing notes
    └── mobile-news.html                       # Legacy mobile experiment
```

**The `index.html` convention:** `index.html` is what Vercel serves at the site root, and it is
always a copy of the **latest** issue. Building a new issue means producing
`atlantean-chronicle-vol1-no[N].html` **and** copying it over `index.html`.

---

## Building a new issue

The full spec lives in **[`CHRONICLE_PROJECT_SYSTEM_PROMPT.md`](CHRONICLE_PROJECT_SYSTEM_PROMPT.md)** —
section order, locked CSS design system, editorial standards, privacy rules, and the pre-flight
checklist. **Read it before every build.** Do not duplicate or drift from it.

At a glance, each issue must have:

1. **Seven sections, in locked order** — International → National + Markets → Local →
   Travel → Tech & AI → Oracle's Corner → Atlantis Ops.
2. A **6-item wire bar** (mix: 2 international, 1 national, 1 local, 1 tech, 1 wildcard).
3. **Real, current news** pulled fresh each week (web research — never fabricated or copied
   from last week).
4. A permanent **Travel "Atlantis Travels" promo** banner.
5. A permanent **Tech & AI "Developing · Watch Next Week" teaser** at the foot of the Tech
   section (added in system-prompt v1.1) — flag an unresolved AI/tech story and carry the
   thread into the next issue.
6. Footer: `news.atlantisits.info · Weekend Edition [dates] · © 2026 Atlantis ITS`.

The locked template base is **No. 6**; the most recent issue is the practical starting point.
CSS variables and typography must not be modified.

### Publish steps

1. Build `atlantean-chronicle-vol1-no[N].html` from the current template + fresh research.
2. Drop any new images into `pics/` — filenames must match the `src` refs **exactly** (see below).
3. Copy the new issue over `index.html`.
4. (Optional) Move issues that have aged out of the root into `archive/`.
5. Commit and push — Vercel auto-deploys to `news.atlantisits.info`.
6. Ship line: **"No. [N] ready — push to Vercel at news.atlantisits.info."**

---

## Images & assets

Images live in **`pics/`** and are referenced with relative paths, e.g. `src="pics/Spain-wildfire.jpg"`.

> ⚠️ **Filenames are case-sensitive on deploy.** Local Windows is case-insensitive, so a
> mismatch like `pics/spain-wildfire.jpg` → `pics/Spain-wildfire.jpg` *looks* fine locally but
> **404s on Vercel (Linux)**. Match the `src` attribute to the actual filename character-for-character.

Images often fail to render in a local preview but load fine once deployed. Sections without a
photo use their own visual anchor (Tech dark hero banner, Markets boxes, styled callouts) — no
placeholder needed.

---

## Section order & accent colors (quick reference)

| # | Section | Accent |
|---|---------|--------|
| 1 | International · World Affairs | navy `#2c3e50` |
| 2 | National · US Affairs + Markets | forest green `#1a4a2e` |
| 3 | Local · Gainesville / North Georgia | terracotta `#8b4513` |
| 4 | Travel & Mobility · Advisory | ocean blue `#1a5496` |
| 5 | Technology · AI Industry | navy/red `#1a1a2e` / `#e94560` |
| 6 | Oracle's Corner · Predictions | deep purple `#4a0e8f` |
| 7 | Atlantis ITS · Operations Intel | teal `#0e6e4f` |

---

## Issue index

| Issue | Weekend Edition | Location |
|-------|-----------------|----------|
| **No. 12** | July 10–12, 2026 *(current — mirrored to `index.html`)* | root |
| No. 11 | June 26–28, 2026 | root |
| No. 10 | June 19–21, 2026 | root |
| No. 9  | June 2026 | root |
| No. 8  | June 2026 | root |
| No. 1–7 | earlier 2026 | `archive/` |

---

## Conventions & guardrails

- **Self-references use `.info`** — the paper's own domain is `news.atlantisits.info`. (The
  permanent Travel promo intentionally links `travel.atlantisits.co`; that's the one sanctioned
  `.co`.)
- **Public-safe only.** No personal contact info, no client/lead data, and **no internal ports,
  hostnames, IPs, or credentials** in any published issue — including the Atlantis Ops section.
  Public contact is limited to `atlantisits.co` / `shane@atlantisits.co`.
- **All story content is new each week.** Ongoing stories may be followed forward, but never
  copied verbatim from the prior issue.
- **Design system is locked.** Keep the CSS variables and typography exactly as in the template.

---

## Related / canonical references

- **[`CHRONICLE_PROJECT_SYSTEM_PROMPT.md`](CHRONICLE_PROJECT_SYSTEM_PROMPT.md)** — the build spec (this repo).
- **`SOP-007 · Chronicle Build`** — Thursday prep + build runbook. Lives in `atlantis-docs`
  (Forgejo), *not* in this repo.
- **`ATLANTIS_AI_MEMORY-v29.md`** (and successors) — squad/ops context that feeds the Atlantis
  section. Kept in `atlantis-memory` (Forgejo); the current compile is loaded per build.

---

*Built by the Atlantis ITS AI squad. 🗞️🔱*
