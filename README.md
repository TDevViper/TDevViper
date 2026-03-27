<div align="center">

<img src="https://capsule-render.vercel.app/api?type=waving&color=0:0a0a0f,50:003322,100:0a0a0f&height=200&section=header&text=Arnav%20Yadav&fontSize=62&fontColor=00ff88&fontAlign=50&fontAlignY=42&desc=Systems%20Engineer%20%E2%80%94%20AI%20%C2%B7%20Backend%20%C2%B7%20Security&descSize=16&descFontColor=aaffccbb&descAlignY=62&animation=fadeIn" width="100%"/>

<br/>

![Profile Views](https://komarev.com/ghpvc/?username=TDevViper&style=flat-square&color=00ff88&label=PROFILE+VIEWS&labelColor=0a0a0f)
&nbsp;
[![GitHub followers](https://img.shields.io/github/followers/TDevViper?label=FOLLOWERS&style=flat-square&color=00ff88&labelColor=0a0a0f&logo=github&logoColor=00ff88)](https://github.com/TDevViper)
&nbsp;
[![Email](https://img.shields.io/badge/EMAIL-arnavyadavop%40gmail.com-00ff88?style=flat-square&labelColor=0a0a0f&logo=gmail&logoColor=00ff88)](mailto:arnavyadavop@gmail.com)

<br/>

[![Typing SVG](https://readme-typing-svg.demolab.com?font=JetBrains+Mono&weight=600&size=16&duration=2800&pause=1000&color=00FF88&center=true&vCenter=true&width=720&lines=I+prioritize+correctness+and+extensibility+over+shortcuts.;ASTRA%3A+7+real+bugs+found%2C+documented%2C+fixed+in+order.;Will+it+hold+under+concurrent+load%3F;Does+the+security+model+survive+adversarial+input%3F;I+write+code+I+can+defend+in+any+room.)](https://git.io/typing-svg)

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
Status    : Building + applying to interesting problems
Exploring : EEG signals · eBPF · Neuroscience · VR
```

CS student from India. I build backend systems where **AI meets production reality** — systems that scale, fail safely, and can be extended without touching the core.

My main project — **ASTRA** — went through a structured audit using production engineering principles: concurrency correctness, security surface, architectural gaps. I found 7 real bugs, documented every root cause, and fixed them in order across five phases.

I care about **correctness over feature count.** About *why* a decision was made, not just *that* it was made.

> *Will it hold under concurrent load? Does the security model survive adversarial input? Can someone extend this without touching the core?*

<br clear="right"/>

---

## 🛠 &nbsp;Tech Stack

<div align="center">

| Languages | Backend | AI / Infra | Security | DevOps |
|:---:|:---:|:---:|:---:|:---:|
| Python · JS · SQL · Rust | FastAPI · async/await · WebSocket | Ollama · ChromaDB · FAISS | HMAC · Injection filters · Sandboxing | Docker · Redis · SQLite · Linux |

<br/>

<img src="https://skillicons.dev/icons?i=python,js,rust,fastapi,docker,redis,linux,git,github,sqlite&theme=dark&perline=5" />

</div>

**Depth signals:** async event loops · per-request context isolation · atomic memory transactions · LRU + semantic cache layering · non-blocking OTel span export

---

## 🚀 &nbsp;ASTRA — Local AI Backend

> **100% on-device. No cloud. No data leaves your machine.**

```
                         ASTRA REQUEST PIPELINE
  ┌─────────────────────────────────────────────────────────────────┐
  │                                                                 │
  │  User Input                                                     │
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
  │      │    [Executor] → web_search / git / monitor / sandbox...  │
  │      │         │                                                │
  │      │         ▼                                                │
  │      │    [Synthesizer] → LLM turns result into natural reply   │
  │      │                                                          │
  │      └──→ [Direct LLM] (no tool needed)                         │
  │                │                                                │
  │                ▼                                                │
  │          [TruthGuard / Critic]                                  │
  │                │                                                │
  │                ▼                                                │
  │          [MemoryTransaction] → atomic write or rollback         │
  │                │                                                │
  │                ▼                                                │
  │          [OTel Tracer] → async, fire-and-forget                 │
  │                │                                                │
  │                ▼                                                │
  │             REPLY                                               │
  └─────────────────────────────────────────────────────────────────┘
```

<br/>

<table width="100%">
<tr>
<td width="33%" valign="top" align="center">

### ◈ Structured Tool Calling
`LLM` · `JSON Schema` · `Routing`

LLM reads tool schemas, picks the right tool and extracts typed args — no regex, no hardcoded patterns. 8 tools: web search, git, system monitor, file reader, task manager, python sandbox, smart home, system controller.

**→ Replaces fragile pattern matching with model reasoning.**

</td>
<td width="1%" align="center"><sub>│<br/>│<br/>│<br/>│<br/>│<br/>│<br/>│<br/>│<br/>│<br/>│</sub></td>
<td width="33%" valign="top" align="center">

### ◈ Security Layer
`HMAC` · `Injection Filters` · `Sandboxing`

Adversarial prompts caught before LLM reach. Client-side `approved: true` flags rejected at the server via HMAC-signed tokens. Python execution sandboxed behind a feature flag. No implicit trust.

**→ Server validates everything. Client trusts nothing.**

</td>
<td width="1%" align="center"><sub>│<br/>│<br/>│<br/>│<br/>│<br/>│<br/>│<br/>│<br/>│<br/>│</sub></td>
<td width="33%" valign="top" align="center">

### ◈ Correctness Hardening
`Concurrency` · `Atomic Writes` · `Quality Gates`

Per-request `RequestContext` eliminates shared mutable state across async tasks. `MemoryTransaction` gives atomic batch writes with rollback. 3-session feedback gate blocks accidental dataset poisoning.

**→ Fails safely. No partial state, no silent corruption.**

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
OTel trace overhead:         ~0ms       →  async fire-and-forget, hot path unblocked
```

---

## ⚖️ &nbsp;Tradeoffs I Made (and why)

> Real engineering is about conscious tradeoffs, not optimal choices.

| Decision | What I chose | What I gave up | Why |
|----------|-------------|----------------|-----|
| Storage | SQLite | PostgreSQL multi-user support | Single-user scope; avoid infra complexity for zero users |
| Auth | Session tokens | JWT multi-user auth | Not needed yet; HMAC covers tool security |
| LLM backend | Ollama (local) | OpenAI API (cloud) | Privacy guarantee; pluggable `LLMBackend` ABC makes swap 4 methods |
| Tool routing | LLM + JSON schema | Pure regex | More robust arg extraction; graceful degradation to regex for weak models |
| Memory writes | `MemoryTransaction` | Direct DB writes | Atomic rollback worth the abstraction overhead |
| Tracing | Async OTel | Sync logging | Non-blocking; traces on every request at ~0ms cost |

---

## 📈 &nbsp;Audit Trail

> Structured review using production engineering principles: concurrency correctness, security surface, architectural gaps, performance ceilings.

```
Phase 0    →  62/100  ████████░░░░░░░░  Initial build
Phase 1–3  →  72/100  █████████░░░░░░░  FastAPI migration, OpenTelemetry, structured logging
CR Fixes   →  78/100  ██████████░░░░░░  Concurrent history bug, double LLM call, Flask removal
Security   →  83/100  ███████████░░░░░  Injection filter, signed tokens, session-scoped cache
Arch Fixes →  88/100  ████████████░░░░  Async observability, lifespan mgmt, TruthGuard isolation
Phase C    →  93/100  █████████████░░░  Pipeline registry, LLM abstraction, structured tool calling

Remaining: PostgreSQL + JWT multi-user auth.
Infrastructure, not code. I know what they require.
I chose to ship over engineering for zero users. That's a deliberate call.
```

---

## 🐛 &nbsp;Bugs Found & Fixed

<table width="100%">
<tr>
<td width="34%"><b>Bug</b></td>
<td width="33%"><b>Root Cause</b></td>
<td width="33%"><b>Fix</b></td>
</tr>
<tr><td>Concurrent history corruption</td><td>Shared mutable list across async requests</td><td>Per-request <code>RequestContext</code> isolation</td></tr>
<tr><td>Double LLM invocation</td><td>Control flow ambiguity in pipeline</td><td>Explicit state machine, single exit point</td></tr>
<tr><td>Client-trusted <code>approved</code> flag</td><td>No server-side token validation</td><td>HMAC-signed tool tokens</td></tr>
<tr><td>Partial memory saves on failure</td><td>Non-atomic write operations</td><td><code>MemoryTransaction</code> with rollback</td></tr>
<tr><td>Blocking OTel traces</td><td>Synchronous span flush in hot path</td><td>Async span export, fire-and-forget</td></tr>
<tr><td>Dataset poisoning via feedback</td><td>No quality gate on feedback loop</td><td>3-session confirmation threshold</td></tr>
<tr><td>Regex-based tool routing</td><td>Fragile pattern matching, no arg extraction</td><td>Structured tool calling with JSON schemas</td></tr>
</table>

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

- `01` &nbsp; EEG signal preprocessing & brain-computer interfaces
- `02` &nbsp; eBPF kernel tracing and performance tooling
- `03` &nbsp; vLLM continuous batching architecture

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
