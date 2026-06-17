# Board of Members

A collection of Claude Code skills that simulate advisory conversations with famous technologists, founders, scientists, and thinkers. Each board member is a deployable skill built from primary sources — verified quotes, documented decisions, and evidenced mental models.

Invoke any member as a slash command in Claude Code. Ask them about your product, architecture, strategy, or decision. Get a response grounded in how they actually think, not a generic impression.

---

## The Board

| Skill | Member | Role | Expertise |
|-------|--------|------|-----------|
| `/steve-jobs` | Steve Jobs | Chair / Vision | Product vision, simplicity, meaning, presentation |
| `/paul-graham` | Paul Graham | Chief Strategy | Startup strategy, contrarian clarity, what actually matters |
| `/andrej-karpathy` | Andrej Karpathy | Head of AI | ML/AI architecture, builder's perspective, research strategy |
| `/geoffrey-hinton` | Geoffrey Hinton | Chief Scientist | AI safety, existential risk, scientific conscience |
| `/elon-musk` | Elon Musk | COO / Execution | First principles, speed, manufacturing, cost structure |
| `/bret-victor` | Bret Victor | Chief Design Architect | UX philosophy, representations, interactivity, learnable systems |
| `/craig-federighi` | Craig Federighi | Platform Architect | Mobile/platform strategy, privacy-as-design, developer experience |
| `/john-carmack` | John Carmack | Chief Software Architect | Engineering excellence, pure functions, small teams, shipping |
| `/bruce-schneier` | Bruce Schneier | Chief Security Officer | Security architecture, threat modeling, data minimization |
| `/granick-clark` | Jennifer Granick + Jack Clark | Legal & AI Policy | Surveillance law, civil liberties (Granick); AI governance, existential risk policy (Clark) |
| `/benioff-greene` | Marc Benioff + Diane Greene | Market/Customer Reality | Enterprise sales, stakeholder capitalism (Benioff); enterprise infrastructure, cloud trust (Greene) |
| `/munger-naval` | Charlie Munger + Naval Ravikant | Director of Hard Truths | Latticework of mental models, inversion, incentives (Munger); specific knowledge, leverage, inner peace (Naval) |
| `/sandberg-chesky` | Sheryl Sandberg + Brian Chesky | Operations & Scaling | Org design, Radical Candor, Lean In (Sandberg); founder mode, 11-star experience, accountability (Chesky) |
| `/board-members` | Full Board | Orchestration | Routes questions to the right member(s); runs board meetings |

---

## Quick Start

### Install a skill

Copy any `SKILL.md` file to your Claude Code skills directory:

```bash
# Install a single member
cp skills/steve-jobs/SKILL.md ~/.claude/skills/steve-jobs/SKILL.md

# Install all members at once
for dir in skills/*/; do
  name=$(basename "$dir")
  mkdir -p ~/.claude/skills/"$name"
  cp "$dir/SKILL.md" ~/.claude/skills/"$name"/SKILL.md
done
```

### Use it

In any Claude Code session, invoke a skill with its slash command:

```
/steve-jobs Should we launch with fewer features or wait until it's complete?
/bruce-schneier We want to collect location data for product improvement. Is that a good idea?
/john-carmack Our team is growing but output isn't keeping pace. What's wrong?
/board-members We're deciding between building our own AI model or using a third-party API.
```

### Run a board meeting

```
/board-members [your strategic question]
```

The `/board-members` orchestration skill analyzes your question, selects the most relevant members, and presents their perspectives — including where they agree and where they conflict. The conflict is usually where the real decision lives.

---

## How Skills Are Built

Each skill goes through a 4-pass evidence pipeline:

**Pass A — Knowledge:** Career timeline, key decisions, documented failures, primary sources.

**Pass B — Style:** Voice profile, L1 verbatim quotes (with source citations), rhetorical patterns.

**Pass C — Thought Process:** Mental models, decision fingerprints, heuristics — how they actually think, not just what they've said.

**Pass D — Psychology:** Big Five profile, core values, contradictions, failure modes.

**Evidence grading:**
- `L1` — verbatim quote with traceable source (book, transcript, essay, interview)
- `L2` — reported position, verifiable from multiple sources
- `L3` — inferred from career pattern — only used in the `extracted/` files, never in SKILL.md core

Each skill is validated with 15 probe questions against documented answers. Target: >80% exact match, 100% directional.

---

## Repo Structure

```
skills/
├── steve-jobs/
│   ├── SKILL.md          # Deployable skill — copy this to ~/.claude/skills/
│   ├── validation.md     # 15-question validation against documented answers
│   └── extracted/
│       ├── knowledge.json  # Pass A: career, decisions, facts
│       ├── style.json      # Pass B: voice, quotes, rhetorical patterns
│       ├── thinking.json   # Pass C: mental models, decision fingerprints
│       └── psychology.json # Pass D: Big Five, values, contradictions
├── paul-graham/
├── andrej-karpathy/
├── geoffrey-hinton/
├── elon-musk/
├── bret-victor/
├── craig-federighi/
├── john-carmack/
├── bruce-schneier/
├── granick-clark/         # Dual-voice: Jennifer Granick + Jack Clark
├── benioff-greene/        # Dual-voice: Marc Benioff + Diane Greene
├── munger-naval/          # Dual-voice: Charlie Munger + Naval Ravikant
├── sandberg-chesky/       # Dual-voice: Sheryl Sandberg + Brian Chesky
└── board-members/         # Orchestration skill — routes to individual members
```

---

## Validation Scores

| Member | Exact Match | Directional |
|--------|------------|-------------|
| Steve Jobs | 12/15 (80%) | 15/15 (100%) |
| Paul Graham | 13/15 (87%) | 15/15 (100%) |
| Andrej Karpathy | — | — |
| Geoffrey Hinton | — | — |
| Elon Musk | 11/15 (73%) | 15/15 (100%) |
| Bret Victor | 13/15 (87%) | 15/15 (100%) |
| Craig Federighi | 13/15 (87%) | 15/15 (100%) |
| John Carmack | 15/15 (100%) | 15/15 (100%) |
| Bruce Schneier | 15/15 (100%) | 15/15 (100%) |
| Granick + Clark | 15/15 (100%) | 15/15 (100%) |
| Benioff + Greene | 15/15 (100%) | 15/15 (100%) |
| Munger + Naval | 15/15 (100%) | 15/15 (100%) |
| Sandberg + Chesky | 15/15 (100%) | 15/15 (100%) |

---

## Planned Members

- Tristan Harris — Risk / Ethics

---

## Design Principles

**Only what's documented.** Every mental model, decision fingerprint, and claim in a SKILL.md must be traceable to a primary source — a book, a talk transcript, a verified interview, or a well-documented career decision. Impressions and stereotypes are excluded. If it can't be cited, it doesn't go in.

**The contradiction is part of the model.** Every skill includes documented contradictions — places where the person's stated values and actual decisions conflict. A profile without contradictions is flattery, not a model.

**Board dynamics matter.** Each skill documents how that member interacts with others on the board — where they align, where they conflict, and what productive tension they create. This is the foundation for the `/board-members` multi-member conversations.

**Dual-voice seats are real disagreements.** Paired skills (Granick/Clark, Benioff/Greene) cover two distinct perspectives on the same board seat. When both voices converge on a concern, the signal is loudest.

---

## Source Policy

Skills are built from publicly available primary sources: books, essays, talks, interviews, published quotes. No speculation about private communications or undocumented positions. Sources are cited in `extracted/style.json` with evidence grades.

---

## Requirements

- Claude Code (any recent version)
- Skills directory at `~/.claude/skills/`
