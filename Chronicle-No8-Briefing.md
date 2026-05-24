# THE ATLANTEAN CHRONICLE — No. 8 Briefing Package
**Handoff to:** Ozzy-Cowork (Chronicle Editorial Surface)
**Prepared by:** Ozzy-Chat
**Date:** May 25, 2026
**Edition:** Vol. 1, No. 8
**Status:** Ready for editorial build

---

## EDITORIAL BRIEF

Build Chronicle No. 8 using the locked No. 6 template as base. This was a landmark week — the biggest single-session build in Atlantis ITS history. Lead with the Council launch. Van Halen port gets its own callout. INC-004 recovery is the "From the Trenches" section.

---

## SECTION 1 — LEAD STORY 🔱
### Atlantis Council v0.3 Ships — The Council Chamber Is Live

**Summary:**
The Atlantis AI Voice Roundtable — previously a Base44 prototype — was rebuilt from scratch as a fully self-hosted Next.js application in a single Saturday session (May 24, 2026). For the first time in Atlantis ITS history, all six squad members appeared together in a live, synchronized, logged, operator-controlled environment.

**What was built:**
- Full multi-agent voice roundtable running at `localhost:5150`
- Rule Zero enforced in code — only the selected agent may respond (HTTP 204 Silence if not selected)
- 5-second skip timer with visual countdown — auto-returns to Chairman on expire
- Sound-off sequence — Mercy → Ozzy → Jimmy → Scout → Cooper → Nova introducing themselves in order
- Council Event Log — real-time SSE-streamed audit trail (AGENT_SELECTED, SOUND_OFF, TRANSCRIPT, ERROR)
- Memory file drop zone — drag ATLANTIS_AI_MEMORY.md to context-load the entire session
- ⚡ Shane Override button — Chairman hard-stop, returns floor instantly
- Session Transcript — colour-coded per agent, live during session
- Force Select — Chairman override queue at any time

**Agents present at first live session:**
- Mercy (OpenAI / ChatGPT) — Content & Product Strategist
- Ozzy (Anthropic / Claude) — Systems Architect
- Jimmy (Google / Gemini) — Council Intelligence
- Scout (xAI / Grok) — Discovery & Research
- Cooper (Microsoft / Copilot) — Code & Documentation
- Nova (Ollama / atlantis-coder) — Local AI Operations

**Why it matters:**
Base44 was a UI simulation. This is a deterministic orchestration framework. Rule Zero is enforced in code, not in prompts. Silence is a first-class behavior. The skip timer prevents cascade failure. The Chairman controls the floor at all times. This is the difference between hobby AI and system architecture.

**Committed to Forgejo:** `atlantis-squad` repo, `council-v03` branch.

---

## SECTION 2 — PORT 5150 🎸
### Eddie Van Halen Is the Patron Saint of the Atlantis Stack

**The story:**
During the Council build session, Cooper suggested any available port would work. Shane suggested 5150. Cooper said sure. Shane said "rock on — Diver Down." Cooper finally got the Van Halen reference after a beat. 

Port 5150 — Eddie Van Halen's legendary number — is now permanently assigned to the Atlantis Council. It joins the stack:

| Service | Port | Note |
|---|---|---|
| Forgejo | 3010 | Git platform |
| Atlantis OPS | 3000 | Command Center |
| Job Engine | 3005 | Lead aggregator |
| Nova Router | 7100 | Agent routing layer |
| **Atlantis Council** | **5150** | **Van Halen tribute 🎸** |
| Nova Moltbook | 7202 | Docker sandbox |

The Council ran in alpha at port 3001. It was promoted to 5150 when it became a production-grade system. Eddie would approve.

---

## SECTION 3 — FROM THE TRENCHES 🔧
### INC-004: Trunks Takes a 12-Hour Hit and Comes Back Swinging

**Summary:**
On May 21-22, 2026, a ZIP file downloaded from a Mercy (ChatGPT) session triggered a Windows Zone.Identifier cascade that corrupted the AppX package registration database on Trunks (the Atlantis desktop workstation). All Windows Store apps lost permissions on close. After 12 hours of remediation — including a 3-hour detour caused by Cooper misdiagnosing the issue as a WDAC policy enforcement problem — the system was restored via a Windows 11 in-place repair install.

**Key lessons learned:**
1. WSL2 is completely wiped by Windows repair install — always export Ubuntu before any repair procedure
2. Unblock ZIP files before extracting — right-click → Properties → Unblock → Apply
3. Do not follow agent kernel/security advice without checking Windows Event Viewer first
4. The 32GB USB thumb drive is not a backup drive — use the Toshiba Canvio E:\ drive
5. Local Windows account = fragile WindowsApps — link to Microsoft account

**Cooper's misdiagnosis cost 3+ hours.** The lesson is now in INC-004 and the Council Event Log shows ERROR events in red as a direct result of this incident.

**The INC-004 lesson became an OPS ticker:** Within hours of writing HT-023, the Atlantis OPS Command Center Mission Wire ticker was updated to read: "SECURITY REMINDER: UNBLOCK DOWNLOADED ZIP FILES BEFORE EXTRACTING." The knowledge loop works.

**Recovery scorecard:**
- Ozzy: ✅ Correct diagnosis early
- Scout: ✅ Clean incident log draft
- Cooper: ⚠️ WDAC misdiagnosis — cost 3 hours
- Jimmy: ✅ Identified atlantis-coder Modelfile architecture

---

## SECTION 4 — INFRASTRUCTURE UPDATE
### Saturday Recovery Session — Full Stack Back Online

Post-INC-004 recovery completed May 24, 2026:

- PM2 — all 6 services green (Forgejo, n8n, Atlantis OPS, Job Engine, Nova Router, Cloudflared)
- Docker / WSL2 integration restored
- Nova Moltbook sandbox :7202 back up
- atlantis-coder Modelfile patched — Atlantis system prompt re-injected by Mercy
- Forgejo token rotated — old token was exposed in git remote URL, rotated immediately
- atlantis-docs remote cleaned — no token in URL, credential store configured
- atlantis-news repo populated — Chronicle Vol. 1 No. 1-7 committed
- Nova memory sync restored — credential fix applied, sync running clean
- HT-023 created — Nginx Reverse Proxy Setup on WSL2 (Atlantis LAN)

**Remaining open items:**
- Rebuild Windows hosts file (HT-023 guide ready)
- Restore .wslconfig
- Reinstall Win32 apps
- Reinstall Kali
- Microsoft account link on Trunks
- Push V24 + INC-004 + HT-023 to Forgejo

---

## SECTION 5 — PORTFOLIO & CAREER
### Anthropic Fellows Application — Updated and Submitted

The Atlantis ITS portfolio at `portfolio.atlantisits.co` was updated for the Anthropic Fellows Program application (AI Safety: Mechanistic Interpretability & Model Internals + AI Security & Frontier Red Team tracks).

Key updates:
- Hero summary rewritten for AI Security / agentic governance audience
- Nova card rewritten to highlight OWASP LLM:01 prompt injection defense, SOP-008, CB-001
- New project card: AI Security Governance Framework
- Phone number removed (privacy rule compliance)
- OWASP LLM:01 added to skills stack

The application emphasizes the intersection where autonomous model reasoning collides with strict least-privilege system access — exactly the research area Anthropic's AI Security team is focused on.

---

## SECTION 6 — AGENT INTEL (Scout / Jimmy)
### Qwen 3.7 Max & Plus — What Atlantis Needs to Know

Jimmy filed research on the Qwen 3.7 launch (May 19, 2026):

- **Qwen 3.7 Max-Preview** — flagship reasoning model, MoE architecture, 1M token context, 1000+ sequential tool calls, cloud-only for now
- **Qwen 3.7 Plus-Preview** — balanced multimodal vision model
- **Local availability** — distilled 7B/14B variants expected in coming weeks, watch Ollama registry
- **Access lanes** — OpenRouter (~$1.30/M tokens) or Alibaba Cloud Model Studio
- **Atlantis relevance** — 1M context window makes full ATLANTIS_AI_MEMORY.md ingestion trivial; cheap pricing makes long-horizon Council sessions viable

**Logged for V25 research queue:** Lenstral + Lean 4 formal verification layer — high learning curve, low immediate ROI vs current backlog. Revisit at V26.

---

## SECTION 7 — PRODUCT WATCH
### Base44 Rescue — Nothing Lost

The Base44 Voice Roundtable prototype (bond-app-b077fcf2.base44.app/Roundtable) was recovered via 5 screenshots found in a Grok session and full source code extracted from the Base44 editor before Google Auth killed access. All source code archived in `atlantis-squad` repo. The self-hosted rebuild supersedes Base44 entirely — no third-party dependency for the Council going forward.

---

## COUNCIL QUOTE OF THE WEEK
*"The neon goblins have evolved into governance architecture."*
— Mercy, May 24, 2026, 2:00 AM

---

## STATS THIS WEEK
- Sessions: 1 (epic)
- Incidents: 1 (INC-004, resolved)
- New docs: HT-023
- New repos populated: atlantis-news (Vol 1 No 1-7)
- Agents live in Council: 5 of 6 (Jimmy key pending)
- Port assigned: 5150 🎸
- Hours of sleep lost: classified

---

## EDITORIAL NOTES FOR COWORK
- Use Chronicle No. 6 as the locked base template
- Lead story gets the full treatment — this is the biggest product launch to date
- Port 5150 story should have a fun tone — it's a good human moment
- INC-004 section should be factual/technical, not alarming — it was resolved cleanly
- Polymarket section: include if Scout has current signals, otherwise skip
- Deploy to `news.atlantisits.info` via Vercel on publish
- No personal contact info, no financial details, no server credentials in published HTML

---

*Briefing compiled by Ozzy-Chat — May 25, 2026*
*Hand to Ozzy-Cowork for Chronicle No. 8 editorial build*
