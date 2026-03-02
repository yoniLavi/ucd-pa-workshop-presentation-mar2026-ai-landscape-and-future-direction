# Current Landscape & Future Paths: AI Beyond the Chat Window

**10-min SME Perspective — Planning Workshop Briefing**

---

## Narrative Arc

**Opening:** There are only two *fundamental* limitations left — and everything else is tractable engineering progressing at breakneck speed.

**Middle:** Here's what that engineering looks like right now (Claude Code ecosystem, agent swarms, Cowork, Claws) — and a key insight about where non-coding work is heading.

**Close:** Here's where it's plausibly heading by 2027, and some implications worth discussing as a group.

---

## 1. The Two Real Limitations (~1.5 min)

Open with the big picture: the AI models themselves are remarkably capable. ARC-AGI2 is essentially saturated — Gemini 3 Deep Think hits 84.6% at $13.62, around average human capability. METR shows Claude Opus 4.6 reliably completing tasks that would take a skilled human 14.5 hours, with the 50% time horizon doubling every ~123 days (up from 4 minutes in early 2024). Reasoning and reliability are improving rapidly and predictably — they're not a fundamental barrier.

What's actually holding us back are exactly **two fundamental limitations**:

### Limitation 1: Long-term Context Management

Current models have finite context windows. They can't truly *remember* across long sessions or across sessions at all without engineering workarounds (compaction, memory files, RAG, etc.). When agents hit the context boundary, there's a discontinuity — a jarring loss of thread — that limits how long and complex a task can be.

### Limitation 2: Online Learning

Models don't update their weights from experience at inference time. They can't learn a new concept, skill, or preference in a lasting way during use. Every session is a blank slate at the parameter level.

### The key insight:

These two limitations may ultimately be solved by the **same breakthrough** — and there are promising research directions (more on this at the end).

### Everything else is tractable engineering:

Tool access? MCP. Knowledge and workflow encoding? Skills. Working memory management? Compaction and memory hooks. Safety? Permission systems and hooks. Parallelism? Agent teams. Persistence? Claws. All of this is moving at extraordinary speed — not because the engineering is easy, but because it doesn't require fundamental research breakthroughs.

---

## 2. The Claude Code Ecosystem: What Rapid Engineering Looks Like (~2.5 min)

Claude Code established the pattern now reshaping everything: give an AI agent real tools and let it *do work*, not just talk about work.

### The building blocks:

- **MCP (Model Context Protocol)** — open standard connecting AI to external tools/data. Now adopted across the ecosystem (ChatGPT, VS Code, Goose, etc.). MCP Apps (Jan 2026) return interactive UI components right inside conversations. Next spec release (~June 2026) targets stateless protocol with stateful app support.

- **Skills** — the agent's "playbook." Follow the open Agent Skills standard (cross-tool). Hot-reload as of v2.1 (Jan 2026). Public Skills repository. Complementary to MCP: skills = *what to do*, MCP = *how to connect*.

- **Context management & compacting** — the quiet revolution. PreCompact hooks (Jan 2026) cut critical info loss by ~30%. Context editing enables selective clearing. Philosophy shift: *quality over quantity* in context utilization. Auto-memory persists patterns and preferences across sessions. The discontinuity at the context boundary is shrinking rapidly.

- **Permissions & hooks** — expanded from 7 to 14 lifecycle events (Feb 2026). Three handler types: bash commands, LLM-based prompt evaluation, full agentic verifiers. This is the safety scaffolding enabling longer-running, more autonomous work.

### Parallel agents & teams:

Single-agent work hit a ceiling. Claude Code now supports up to 5 simultaneous sub-agents on a shared codebase — specializing, coordinating via shared task lists, claiming and reporting work autonomously. Anthropic's own team built a C compiler this way.

This is where the "copilot" metaphor breaks down — we're talking about *delegation and orchestration*, not autocomplete.

---

## 3. The Expanding Ecosystem (~2 min)

### Claude Cowork (Jan 2026)

The key insight: **the same patterns that transformed coding apply to all knowledge work.**

Cowork is built on Claude Code's foundations but for non-developers: scoped folder access, autonomous file management, parallel task queuing, external system connections via MCP/skills. Available on Pro, Team, and Enterprise plans.

The interaction model shifts from "chatbot" to "coworker" — you assign work and review results.

### Gas Town & Agent Swarms (Steve Yegge, Jan 2026)

Yegge's Gas Town takes multi-agent to the extreme: **20-30 parallel Claude Code instances** organized into hierarchical "colonies." Work is expressed as "Beads" (atomic units) organized into "Molecules" (workflow graphs), all persisted in Git.

The developer role transforms from individual coder to "factory operator managing agent swarms." Yegge's framing: 2024 was the year of the Chatbot, 2025 the year of the Agent, 2026 is the year of **Orchestration**.

### Devin: The "AI Employee" Model

Devin (Cognition) represents a different paradigm — not a tool *you* orchestrate but an autonomous agent you *assign work to*. 18 months in: 67% of PRs now merged (vs 34% a year ago), 4x faster at problem-solving, deployed at Goldman Sachs, Santander, Nubank. Excels at clear-requirement tasks a junior engineer would take 4-8 hours on.

### Claws: The Personal AI Layer (Karpathy, Feb 2026)

Karpathy's layering model:

> **LLMs → LLM Agents → Claws**

> "Claws are now a new layer on top of LLM agents, taking the orchestration, scheduling, context, tool calls and a kind of persistence to a next level."

A Claw is a locally-hosted AI assistant wired to your tools — calendar, email, browser, messaging (WhatsApp, Telegram, Slack, Signal, iMessage). Not a chat window but a persistent *orchestrator*. The 🦞 emoji is the symbol.

Key projects: **OpenClaw** (~400K lines, broad integrations, moving to open-source foundation) vs **NanoClaw** (~4K lines, "fits in my head and that of AI agents" — Karpathy).

---

## 4. Where This Is Going by 2027 (~2.5 min)

### Addressing the two fundamental limitations:

**The context discontinuity is shrinking fast**, via multiple converging paths:
- **Letta/MemGPT approach** — virtual context management; the LLM manages its own memory like an OS manages RAM/disk. Letta's Context Repositories (Feb 2026) use git-based versioning for agent memory. Their Skill Learning feature lets agents improve from experience in token space.
- **Architectural research** — non-transformer or hybrid architectures may bypass the context window constraint entirely.
- **Increasingly effective engineering** — compaction, memory hooks, persistent file/database memory (catalyzed by the Claws movement) are functionally mitigating the problem before it's formally solved. For practitioners, "true infinite context" vs "functionally indistinguishable from it" is a distinction without a difference.

At the current trajectory, the context discontinuity may cease to be a practical problem well before it's theoretically solved.

**Online learning** is moving from theory toward practice:
- **E2E-TTT (End-to-End Test-Time Training)** — published Dec 2025. Reframes language modeling as *continual learning*: the model compresses context into its weights at inference time. For 3B models, it scales with context length like full-attention Transformers with constant inference latency (2.7x faster at 128K). Scaling to frontier model sizes is still unproven, but the research direction is credible and active.

### AI will turn non-coding work into coding work

A key observation: the reason AI agents work so well for coding is that code is *structured and verifiable* — there are tests, compilers, type checkers. Non-coding knowledge work (emails, documents, planning) lacks this.

But AI itself will close this gap. Using its own SWE capabilities, AI will accelerate the digital transformation processes already underway — structuring previously unstructured work, making it API-addressable and testable. This is putting on steroids a trend that's been running for decades.

In the medium term, most "knowledge work" will be handled by API and agent-to-agent communication. The question of whether AI handles "fuzzy" work well becomes less relevant as less and less work remains fuzzy. And for genuine edge cases, AI systems will be able to escalate — including spawning human contractors (e.g. via platforms like Upwork) to handle what they can't.

### The productivity vision: AI workers, not AI assistants

The Claws trajectory raises a fundamental security question. Karpathy is right to be cautious about giving an AI persistent access to your personal email, calendar, and credentials — that's an inherently exposed surface that's hard to secure.

A more natural evolution: **long-lived AI workers with their own accounts** — their own email addresses, calendars, project management access. You share specific items with them as you would with a human colleague. Assign work, review output, grant scoped access.

Think of it as **Devin-on-steroids**: not just for coding but for any knowledge work. The AI doesn't impersonate you — it *is* a team member with its own identity and bounded permissions.

The accountability model is straightforward: AI accounts are tagged as such, linked to the human principal or organizational unit that controls them, with clear escalation paths. We're already seeing this pattern in customer service, where acknowledged AI chatbots handle support conversations. This is the next step — the organizational plumbing is simple; the cultural adjustment is the bigger shift.

The METR time-horizon trajectory grounds this concretely: doubling every ~123 days means week-long autonomous tasks are plausible by late 2026. The "AI team member" model becomes practical as soon as agents can sustain coherent work across days, not just hours.

---

## 5. Implications for Discussion (~1 min)

*Not recommendations — provocations for the workshop to take up together.*

### The landscape shift:

| Era | Interaction | Core Skill |
|-----|-------------|------------|
| Chat (2023) | Prompt → Response | Prompt engineering |
| Agents (2024-25) | Delegate → Review | Task decomposition, context engineering |
| Orchestration (2026+) | Configure → Oversee | Systems thinking, trust calibration |

### Questions worth raising:

1. **From "how to prompt" to "how to orchestrate"** — the skillset is shifting toward understanding tool ecosystems (MCP, skills), agent coordination, and context engineering. What does that mean for how we structure our courses?

2. **Non-coding professionals need this now** — Cowork and Claws are making agent patterns accessible beyond developers. AI orchestration is becoming a *general* professional skill.

3. **AI will structure the unstructured** — if AI turns non-coding work into coding work (API-addressable, testable, automatable), what does that mean for the professional roles we're training people for?

4. **The "AI team member" model changes the job description** — if the near future involves managing AI workers with their own identities and accounts, professional competence starts to look more like management and oversight than individual execution.

5. **The pace demands curriculum agility** — six months ago, "Claws" wasn't a concept and Cowork didn't exist. How do we teach in a landscape that moves this fast?

---

## Key Sources

- [ARC-AGI2: Gemini 3 Deep Think at 84.6% (MarkTechPost)](https://www.marktechpost.com/2026/02/12/is-this-agi-googles-gemini-3-deep-think-shatters-humanitys-last-exam-and-hits-84-6-on-arc-agi-2-performance-today/)
- [METR: Task-Completion Time Horizons](https://metr.org/time-horizons/)
- [Claude Opus 4.6: 14.5h Time Horizon (OfficeChai)](https://officechai.com/ai/exponential-progress-claude-opus-4-6-has-50-time-horizon-of-14-5-hours-on-metr-time-horizons-benchmark/)
- [Anthropic: Building a C Compiler with Parallel Claudes](https://www.anthropic.com/engineering/building-c-compiler)
- [Introducing Cowork — Claude Blog](https://claude.com/blog/cowork-research-preview)
- [Claude Blog: Skills Explained](https://claude.com/blog/skills-explained)
- [Claude Blog: Extending Capabilities with Skills and MCP](https://claude.com/blog/extending-claude-capabilities-with-skills-mcp-servers)
- [Claude Code Docs: Agent Teams](https://code.claude.com/docs/en/agent-teams)
- [Claude Code Docs: Hooks Reference](https://code.claude.com/docs/en/hooks)
- [Simon Willison: Karpathy Talks About Claws](https://simonwillison.net/2026/Feb/21/claws/)
- [Karpathy on Claws (tweet)](https://x.com/karpathy/status/2024987174077432126)
- [Steve Yegge: Welcome to Gas Town](https://steve-yegge.medium.com/welcome-to-gas-town-4f25ee16dd04)
- [Steve Yegge: The Future of Coding Agents](https://steve-yegge.medium.com/the-future-of-coding-agents-e9451a84207c)
- [Gas Town: Multi-Agent Orchestration Framework](https://reading.torqsoftware.com/notes/software/ai-ml/agentic-coding/2026-01-15-gas-town-multi-agent-orchestration-framework/)
- [Cognition: Devin's 2025 Performance Review](https://cognition.ai/blog/devin-annual-performance-review-2025)
- [E2E-TTT: End-to-End Test-Time Training (arXiv)](https://arxiv.org/abs/2512.23675)
- [Letta: Continual Learning in Token Space](https://www.letta.com/blog/continual-learning)
- [Letta AI (GitHub)](https://github.com/letta-ai/letta)
- [OpenClaw / Clawdbot (GitHub)](https://github.com/openclaw/openclaw)
- [VentureBeat: Claude Cowork](https://venturebeat.com/orchestration/anthropic-says-claude-code-transformed-programming-now-claude-cowork-is)
- [Devin AI](https://devin.ai/)
- [IBM: Devin as Goldman Sachs' AI Employee](https://www.ibm.com/think/news/goldman-sachs-first-ai-employee-devin)
