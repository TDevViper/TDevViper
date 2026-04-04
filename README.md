<div align="center">

<img src="https://capsule-render.vercel.app/api?type=waving&color=0:0a0a0f,50:003322,100:0a0a0f&height=200&section=header&text=Arnav%20Yadav&fontSize=62&fontColor=00ff88&fontAlign=50&fontAlignY=42&desc=Systems%20Engineer%20%E2%80%94%20AI%20%C2%B7%20Backend%20%C2%B7%20Security&descSize=16&descFontColor=aaffccbb&descAlignY=62&animation=fadeIn" width="100%"/>

<br/>

![Profile Views](https://komarev.com/ghpvc/?username=TDevViper&style=flat-square&color=00ff88&label=PROFILE+VIEWS&labelColor=0a0a0f)
&nbsp;
[![GitHub followers](https://img.shields.io/github/followers/TDevViper?label=FOLLOWERS&style=flat-square&color=00ff88&labelColor=0a0a0f&logo=github&logoColor=00ff88)](https://github.com/TDevViper)
&nbsp;
[![Email](https://img.shields.io/badge/EMAIL-arnavyadavop%40gmail.com-00ff88?style=flat-square&labelColor=0a0a0f&logo=gmail&logoColor=00ff88)](mailto:arnavyadavop@gmail.com)

<br/>

[![Typing SVG](https://readme-typing-svg.demolab.com?font=JetBrains+Mono&weight=600&size=16&duration=2800&pause=1000&color=00FF88&center=true&vCenter=true&width=720&lines=I+prioritize+correctness+and+extensibility+over+shortcuts.;ASTRA%3A+audited%2C+hardened%2C+and+now+production-ready+SaaS.;Will+it+hold+under+concurrent+load%3F;Does+the+security+model+survive+adversarial+input%3F;I+write+code+I+can+defend+in+any+room.)](https://git.io/typing-svg)

</div>

<br/>

---

## 👤 &nbsp;About Me

<img align="right" src="https://github-readme-stats.vercel.app/api?username=TDevViper&show_icons=true&theme=tokyonight&hide_border=true&title_color=00ff88&icon_color=00ff88&text_color=aaaacc&bg_color=0a0a0f&custom_title=GitHub+Stats&rank_icon=github" width="42%"/>

```yaml
Name      : Arnav Yadav
Alias     : TDevViper
Domain    : AI · Backend · Security
Region    : India 🇮🇳
Status    : Building ASTRA → SaaS launch
Exploring : EEG signals · eBPF · Neuroscience 
```

CS student from India. I build backend systems where **AI meets production reality** — systems that scale, fail safely, and can be extended without touching the core.

My main project — **ASTRA** — started as a personal AI assistant, went through a structured FAANG-level audit (scored 3.8/10), and I systematically fixed every issue across 5 phases — ending at ~7.8/10 with full multi-user SaaS infrastructure.

I care about **correctness over feature count.** About *why* a decision was made, not just *that* it was made.

> *Will it hold under concurrent load? Does the security model survive adversarial input? Can someone extend this without touching the core?*

<br clear="right"/>

---

## 🛠 &nbsp;Tech Stack

<div align="center">

| Languages | Backend | AI / Infra | Security | DevOps |
|:---:|:---:|:---:|:---:|:---:|
| Python · JS · SQL · Rust | FastAPI · JWT · WebSocket | Ollama · ChromaDB · FAISS | RBAC · Sandboxing · HMAC | Docker · Redis · SQLite · Linux |

<br/>

<img src="https://skillicons.dev/icons?i=python,js,rust,fastapi,docker,redis,linux,git,github,sqlite&theme=dark&perline=5" />

</div>

**Depth signals:** async event loops · per-request context isolation · atomic memory transactions · LRU + semantic cache layering · sliding-window rate limiting · container-level code sandboxing · JWT + RBAC auth systems

---

## 🚀 &nbsp;ASTRA — Private AI Platform

> **Runs on your hardware. Multi-user. Production-hardened. SaaS-ready.**

```
                         ASTRA REQUEST PIPELINE
  ┌─────────────────────────────────────────────────────────────────┐
  │                                                                 │
  │  User Input (JWT authenticated, rate-limited by role)           │
  │      │                                                          │
  │      ▼                                                          │
  │  [Injection Filter] ──→ adversarial prompts rejected here       │
  │      │                                                          │
  │      ▼                                                          │
  │  [Cache Layer] ──→ LRU + semantic similarity (ChromaDB/FAISS)   │
  │      │                                                          │
  │      ▼                                                          │
  │  [Intent Classifier]                                            │
  │      │                                                          │
  │      ├──→ [Tool Router] ──→ LLM reads JSON schemas              │
  │      │         │             picks tool + extracts args         │
  │      │         ▼                                                │
  │      │    [Docker Sandbox] → isolated container, no network,    │
  │      │         │             read-only fs, PID limit, 128MB cap │
  │      │         ▼                                                │
  │      │    [Synthesizer] → LLM turns result into natural reply   │
  │      │                                                          │
  │      └──→ [Direct LLM] → Ollama local → Anthropic fallback      │
  │                │                                                │
  │                ▼                                                │
  │          [TruthGuard / Critic]                                  │
  │                │                                                │
  │                ▼                                                │
  │          [MemoryTransaction] → atomic write or rollback         │
  │          [per-user namespace] → ChromaDB + SQLite isolated      │
  │                │                                                │
  │                ▼                                                │
  │          [OTel Tracer] → Jaeger · Prometheus · Grafana          │
  │                │                                                │
  │                ▼                                                │
  │             REPLY (streamed, per-thread history)                │
  └─────────────────────────────────────────────────────────────────┘
```

<br/>

<table width="100%">
<tr>
<td width="33%" valign="top" align="center">

### ◈ Auth + RBAC
`JWT` · `bcrypt` · `4 Roles`

Full user account system — register, login, refresh tokens. Four roles: owner / admin / user / guest. 13 permissions mapped by role. Privilege escalation prevention baked in — you cannot assign a role equal to or higher than your own.

**→ No shared API key. Every request is a real identity.**

</td>
<td width="1%" align="center"><sub>│<br/>│<br/>│<br/>│<br/>│<br/>│<br/>│<br/>│<br/>│<br/>│</sub></td>
<td width="33%" valign="top" align="center">

### ◈ Docker Sandbox
`Container isolation` · `No escape`

Code execution runs in a throwaway Docker container — no network, read-only root filesystem, all Linux capabilities dropped, PID limit enforced, 128MB memory cap. Verified: host filesystem blocked, fork bombs blocked, network blocked.

**→ AST walking replaced with real kernel-level isolation.**

</td>
<td width="1%" align="center"><sub>│<br/>│<br/>│<br/>│<br/>│<br/>│<br/>│<br/>│<br/>│<br/>│</sub></td>
<td width="33%" valign="top" align="center">

### ◈ Multi-User SaaS
`Threads` · `Rate limits` · `Isolation`

Per-user conversation threads with message history and forking from any message. Per-user rate limiting (Redis sliding window): guest 5/min, user 20, admin 60, owner unlimited. All memory namespaced by user_id — zero cross-user data leakage.

**→ One instance, many users, full isolation.**

</td>
</tr>
</table>

<div align="center">

**[→ View ASTRA on GitHub](https://github.com/TDevViper/Astra_Presonal_ai)**

</div>

---

## ⚡ &nbsp;Performance

> Measured locally on MacBook (M-series), Ollama running llama3.2, locust load tests.

```
Concurrent users (locust):   120 req    →  stable, no dropped connections
Avg response latency:        ~180ms     →  intent classify + LLM + reply
Peak memory (full pipeline): ~1.2 GB   →  LLM model loaded + ChromaDB in-memory
Cache hit latency:           <5ms       →  LRU layer, bypasses LLM entirely
Tool call overhead:          +40ms avg  →  schema read + arg extraction + synthesis
Docker sandbox cold start:   ~800ms     →  container spin-up + execution + teardown
OTel trace overhead:         ~0ms       →  async fire-and-forget, hot path unblocked
JWT validation overhead:     <1ms       →  in-process JOSE decode, no DB hit
```

---

## ⚖️ &nbsp;Tradeoffs I Made (and why)

> Real engineering is about conscious tradeoffs, not optimal choices.

| Decision | What I chose | What I gave up | Why |
|----------|-------------|----------------|-----|
| Sandbox | Docker container | gVisor / Firecracker | Mac-compatible; same isolation guarantees for Python execution |
| Auth | JWT + bcrypt | OAuth / SSO | Sufficient for SaaS v1; swap is 1 file change via auth module boundary |
| Rate limiting | Redis sliding window + memory fallback | Pure Redis | Resilient — works even when Redis is down |
| Memory isolation | user_id namespace in SQLite + ChromaDB | Separate DB per user | Simpler ops; same isolation at query layer |
| LLM fallback | Ollama → Anthropic Claude | Single provider | Eliminates single point of failure; local-first with cloud escape hatch |
| Conversation storage | SQLite threads table | Postgres | Zero infra overhead; thread forking works at this scale |
| Observability | Jaeger + Prometheus + Grafana in compose | Managed APM (Datadog) | Full control, zero cost, OTel-compatible for future migration |

---

## 📈 &nbsp;Audit Trail

> Started with a FAANG-level production readiness audit. Fixed everything. Built a SaaS.

```
Initial audit score  →  3.8/10  ████░░░░░░░░░░░░  10 critical issues found
Phase 1 (Security)   →  5.5/10  █████░░░░░░░░░░░  Auth, token limits, dead code, lint gate
Phase 2 (AI/Code)    →  6.5/10  ██████░░░░░░░░░░  Emotion ML, memory namespacing, agent fixes
Phase 3 (Arch)       →  7.0/10  ███████░░░░░░░░░  Structured tool calling, observability stack
Phase 4 (Sandbox)    →  7.5/10  ███████░░░░░░░░░  Docker container isolation, verified escape-proof
Multi-user SaaS      →  7.8/10  ████████░░░░░░░░  JWT auth, RBAC, threads, rate limiting, dashboard

Remaining gap: managed vector DB, conversation search, Stripe billing.
Deliberate call — shipping > engineering for zero users.
```

---

## 🐛 &nbsp;Critical Issues Found & Fixed

<table width="100%">
<tr>
<td width="34%"><b>Issue</b></td>
<td width="33%"><b>Root Cause</b></td>
<td width="33%"><b>Fix</b></td>
</tr>
<tr><td>Unauthenticated streaming endpoint</td><td>/chat/stream had no auth dependency</td><td>Depends(require_api_key) + JWT rate_limit added</td></tr>
<tr><td>Global shared memory (all users)</td><td>Single memory.json, no user_id concept</td><td>Per-user namespaced paths + ChromaDB metadata filter</td></tr>
<tr><td>Python sandbox escape</td><td>AST walking bypassable via __mro__</td><td>Docker container: no network, read-only fs, cap-drop ALL</td></tr>
<tr><td>2048 token context starvation</td><td>Hardcoded 2021-era limits</td><td>8192 ctx, 1024 predict, intent-aware token budgets</td></tr>
<tr><td>Flask + FastAPI dual codebase</td><td>Half-completed migration, dead code</td><td>7 Flask files deleted, single FastAPI codebase</td></tr>
<tr><td>Hardcoded model names in agent loop</td><td>AgentLoop bypassed ModelManager</td><td>Wired to ModelManager.select_model()</td></tr>
<tr><td>_log_counter race condition</td><td>Global int mutation without lock</td><td>threading.Lock() wrapping all increments</td></tr>
<tr><td>Bag-of-words emotion detection</td><td>Keyword list, no negation handling</td><td>distilbert-base-uncased-emotion via HuggingFace</td></tr>
<tr><td>No per-user auth or sessions</td><td>Single shared API key for all users</td><td>JWT access + refresh tokens, bcrypt password hashing</td></tr>
<tr><td>No access control on dangerous ops</td><td>Any authenticated user could wipe memory / run shell</td><td>RBAC: 4 roles, 13 permissions, privilege escalation blocked</td></tr>
</table>

---

## 🔐 &nbsp;Security Surface

```
Layer 1 — Transport    : HTTPS + CORS env-gated (not wildcard in prod)
Layer 2 — Auth         : JWT Bearer tokens (60min access, 7d refresh)
Layer 3 — Identity     : bcrypt-hashed passwords, per-user SQLite store
Layer 4 — Authorization: RBAC — 4 roles, 13 permissions, no escalation
Layer 5 — Rate limits  : Redis sliding window per user_id, role-aware limits
Layer 6 — Input        : Prompt injection filter, unicode normalization
Layer 7 — Execution    : Docker sandbox — no network, no host fs, PID cap
Layer 8 — Memory       : user_id namespace — zero cross-user data access
Layer 9 — Audit        : Every request logged — endpoint, user, duration, status
```

---

## 📊 &nbsp;GitHub Analytics

<div align="center">

<img src="https://github-readme-stats.vercel.app/api/top-langs/?username=TDevViper&layout=compact&theme=tokyonight&hide_border=true&title_color=00ff88&text_color=aaaacc&bg_color=0a0a0f&langs_count=8" height="165"/>
&nbsp;&nbsp;
<img src="https://streak-stats.demolab.com?user=TDevViper&theme=tokyonight-duo&hide_border=true&ring=00ff88&fire=00ff88&currStreakLabel=00ff88&background=0a0a0f" height="165"/>

<br/><br/>

<img src="https://github-readme-activity-graph.vercel.app/graph?username=TDevViper&theme=react-dark&bg_color=0a0a0f&color=00ff88&line=00ff88&point=ffffff&hide_border=true&area=true&area_color=00ff8815" width="97%"/>

</div>

---

## 🏆 &nbsp;Trophies

<div align="center">
<br/>
<img src="https://github-profile-trophy.vercel.app/?username=TDevViper&theme=tokyonight&no-frame=true&no-bg=true&margin-w=6&column=6" width="97%"/>
</div>

---

## 🎯 &nbsp;Current Focus

<table width="100%">
<tr>
<td width="50%">

- `01` &nbsp; ASTRA — Stripe billing + landing page launch
- `02` &nbsp; EEG signal preprocessing & brain-computer interfaces
- `03` &nbsp; eBPF kernel tracing and performance tooling

</td>
<td width="50%">

- `04` &nbsp; Distributed systems patterns & consensus protocols
- `05` &nbsp; Computational neuroscience + VR signal interfaces
- `06` &nbsp; LLM tool calling and structured inference pipelines

</td>
</tr>
</table>

---

## 🐍 &nbsp;Contribution Trail

<div align="center">
<br/>
<picture>
  <source media="(prefers-color-scheme: dark)" srcset="https://raw.githubusercontent.com/TDevViper/TDevViper/output/github-contribution-grid-snake-dark.svg">
  <source media="(prefers-color-scheme: light)" srcset="https://raw.githubusercontent.com/TDevViper/TDevViper/output/github-contribution-grid-snake.svg">
  <img alt="snake animation" src="https://raw.githubusercontent.com/TDevViper/TDevViper/output/github-contribution-grid-snake-dark.svg" width="97%"/>
</picture>
</div>

---

## 🤝 &nbsp;Connect

<div align="center">
<br/>

[![LinkedIn](https://img.shields.io/badge/LinkedIn-Connect-0a0a0f?style=for-the-badge&logo=linkedin&logoColor=00ff88)](https://linkedin.com)
&nbsp;
[![GitHub](https://img.shields.io/badge/GitHub-TDevViper-0a0a0f?style=for-the-badge&logo=github&logoColor=00ff88)](https://github.com/TDevViper)
&nbsp;
[![Email](https://img.shields.io/badge/Gmail-Reach%20Out-0a0a0f?style=for-the-badge&logo=gmail&logoColor=00ff88)](mailto:arnavyadavop@gmail.com)

<br/><br/>

*" I don't stop at it works — I ask if it holds under load, survives adversarial input, and lets someone else extend it without touching the core. "*

<br/>

</div>

<img src="https://capsule-render.vercel.app/api?type=waving&color=0:0a0a0f,50:003322,100:0a0a0f&height=130&section=footer" width="100%"/>
