<div align="center">

<img src="https://capsule-render.vercel.app/api?type=venom&color=0:0a0a0f,40:00ff88,100:0a0a0f&height=240&section=header&text=ARNAV%20YADAV&fontSize=72&fontColor=00ff88&animation=fadeIn&fontAlignY=52&desc=TDevViper%20%2F%2F%20Systems%20Engineer%20%2F%2F%20Correctness-First&descSize=18&descAlignY=72&descColor=aaaacc"/>

<img src="https://readme-typing-svg.demolab.com?font=JetBrains+Mono&weight=700&size=18&duration=2000&pause=800&color=00FF88&center=true&vCenter=true&width=780&lines=I+build+things+that+are+more+than+they+need+to+be.;ASTRA%3A+62%2F100+%E2%86%92+93%2F100+%E2%80%94+five+phases%2C+documented+reasoning;Will+it+hold+under+concurrent+load%3F;Does+the+security+model+survive+adversarial+input%3F;I+write+code+I+can+defend+in+any+room." alt="Typing SVG" />

<br/>

[![GitHub followers](https://img.shields.io/github/followers/TDevViper?style=for-the-badge&logo=github&color=00ff88&labelColor=0a0a0f)](https://github.com/TDevViper)
[![Email](https://img.shields.io/badge/Email-arnavyadavop%40gmail.com-00ff88?style=for-the-badge&logo=gmail&logoColor=white&labelColor=0a0a0f)](mailto:arnavyadavop@gmail.com)
[![LinkedIn](https://img.shields.io/badge/LinkedIn-Connect-00ff88?style=for-the-badge&logo=linkedin&logoColor=white&labelColor=0a0a0f)](https://linkedin.com)
![Profile views](https://komarev.com/ghpvc/?username=TDevViper&style=for-the-badge&color=00ff88&labelColor=0a0a0f)

</div>

---

<img align="right" width="360" src="https://media.giphy.com/media/qgQUggAC3Pfv687qPC/giphy.gif"/>

### `> whoami`

CS student from India who builds things that are **more than they need to be**.

My main project — **ASTRA** — is a local AI system with a modular pipeline architecture, hybrid memory, async inference, and a security model I audited end-to-end and rebuilt from scratch. It went from **62 → 93/100** across five phases of critical fixes, security hardening, and architectural refactors.

I care about **systems correctness** more than feature count. I care about *why* a design decision was made more than *that* it was made.

What sets me apart: I don't stop at "it works." I ask —
> *Will it hold under concurrent load? Does the security model survive adversarial input? Can someone else extend this without touching the core?*

Currently exploring: **computational neuroscience + VR + brain-signal analysis**

<br clear="right"/>

---

## `> cat dev_log.md`

> Updated every meaningful session — code, research, or architecture.

| Date | Session |
|------|---------|
| `2026-03-22` | README overhaul — structure, devlog, badges |
| `2026-03-21` | Deep dive: eBPF kernel tracing internals |
| `2026-03-20` | ASTRA: Refining the injection filter layer |
| `2026-03-19` | Reading: vLLM continuous batching architecture |
| `2026-03-18` | EEG signal preprocessing experiments |

---

## `> cat stack.py`

<div align="center">

<img src="https://skillicons.dev/icons?i=python,fastapi,docker,redis,linux,git,github,bash,rust&theme=dark" />
<br/>
<img src="https://skillicons.dev/icons?i=js,sqlite,c,cpp&theme=dark" />

</div>

<br/>

```python
arnav = {
    "languages":   ["Python", "JavaScript", "SQL", "Rust (learning)"],
    "backend":     ["FastAPI", "async/await", "WebSocket", "SSE"],
    "ai_stack":    ["Ollama", "ChromaDB", "FAISS", "LLMBackend abstraction"],
    "infra":       ["Docker Compose", "Redis", "SQLite", "OpenTelemetry"],
    "security":    ["HMAC tokens", "injection filters", "sandboxed execution"],
    "exploring":   ["eBPF", "EEG signal processing", "distributed systems"],
    "region":      "India 🇮🇳",
    "status":      "building + applying to interesting problems"
}
```

---

## `> ./astra --info`

> A production-quality local AI backend. **100% on-device. No cloud. No data leaves your machine.**

```
User Input → Sanitize → Cache → Intent → Tools → Memory
                                       ↓
                    Web Search → ReAct Agent → LLM → Critic → Reply
```

| Component | Why it matters |
|-----------|---------------|
| Modular `PipelineRegistry` | Add capabilities without touching `brain.py` |
| Pluggable `LLMBackend` ABC | Swap Ollama → OpenAI → vLLM in 4 method overrides |
| Per-request `RequestContext` | No shared state = no race conditions |
| `MemoryTransaction` | Atomic batch writes — no partial saves under failure |
| HMAC-signed tool tokens | `client_approved: true` is rejected at the server |
| 3-session feedback quality gate | One accidental thumbs-up can't poison the dataset |
| Async OTel observability | Non-blocking traces on every request, zero overhead |
| Injection filter layer | Adversarial prompt inputs caught before LLM reach |

**[→ View ASTRA on GitHub](https://github.com/TDevViper/Astra_Presonal_ai)**

---

## `> git log --audit`

> This is the part most people skip. I didn't.

ASTRA went through a full Staff+ engineering audit — concurrency correctness, security surface, architectural gaps, performance ceilings. Then I fixed everything, in phases, with documented reasoning for every decision.

```
Phase 0    →  62/100  ████████░░░░░░░░  Initial build
Phase 1–3  →  72/100  █████████░░░░░░░  FastAPI migration, OpenTelemetry, structured logging
CR fixes   →  78/100  ██████████░░░░░░  Concurrent history bug, double LLM call, Flask removal
Security   →  83/100  ██████████░░░░░░  Injection filter, signed tokens, session-scoped cache
Arch fixes →  88/100  ███████████░░░░░  Async observability, lifespan mgmt, TruthGuard isolation
Phase C    →  93/100  ████████████░░░░  Pipeline registry, LLM abstraction, parallel tools, quality gate
```

> **The remaining 7 points:** PostgreSQL migration and JWT multi-user auth. Infrastructure changes, not code changes. I know exactly what they require. I chose to ship instead of over-engineering for zero users. **That's also an architectural decision.**

---

## `> grep -r "bugs_found" audit/`

| Issue | Root Cause | Fix |
|-------|-----------|-----|
| Concurrent history corruption | Shared mutable list across async requests | Per-request `RequestContext` isolation |
| Double LLM invocation | Control flow ambiguity in pipeline | Explicit state machine with single exit |
| Client-trusted `approved` flag | No server-side token validation | HMAC-signed tool tokens |
| Partial memory saves on failure | Non-atomic write operations | `MemoryTransaction` with rollback |
| Blocking OTel traces | Synchronous span flush in hot path | Async span export, fire-and-forget |
| Dataset poisoning via feedback | No quality gate on feedback loop | 3-session confirmation threshold |

---

## `> neofetch --stats`

<div align="center">

<img src="https://github-readme-stats.vercel.app/api?username=TDevViper&show_icons=true&theme=tokyonight&hide_border=true&bg_color=0a0a0f&title_color=00ff88&icon_color=00ff88&text_color=aaaacc&ring_color=00ff88" height="160"/>
<img src="https://github-readme-streak-stats.herokuapp.com/?user=TDevViper&theme=tokyonight&hide_border=true&background=0a0a0f&ring=00ff88&fire=00ff88&currStreakLabel=00ff88" height="160"/>

<br/>

<img src="https://github-readme-stats.vercel.app/api/top-langs/?username=TDevViper&layout=compact&theme=tokyonight&hide_border=true&bg_color=0a0a0f&title_color=00ff88&text_color=aaaacc" height="140"/>

</div>

---

## `> cat activity_graph`

<div align="center">
<img src="https://github-readme-activity-graph.vercel.app/graph?username=TDevViper&theme=react-dark&bg_color=0a0a0f&color=00ff88&line=00ff88&point=ffffff&hide_border=true" width="100%"/>
</div>

---

## `> ls ~/deep_dives/`

```bash
$ ls -la ~/deep_dives/
drwxr-xr-x  eBPF_kernel_tracing/
drwxr-xr-x  EEG_signal_processing/
drwxr-xr-x  distributed_systems_patterns/
drwxr-xr-x  vLLM_continuous_batching/
drwxr-xr-x  computational_neuroscience_intro/
drwxr-xr-x  VR_brain_signal_interface_research/
```

---

## `> diff interests.txt not_interests.txt`

<div align="center">

| `+` Looking for | `-` Not looking for |
|----------------|-------------------|
| Hard systems problems | Tutorials disguised as projects |
| Security + AI intersection | Another CRUD app |
| Neuroscience + data science | Surface-level ML wrappers |
| Code review + architecture | Shipping fast without understanding |
| Research with real engineering depth | Hype without substance |
| Correctness-first design | "It works on my machine" |

</div>

---

<div align="center">

```
╔══════════════════════════════════════════════════════════════╗
║  "If it doesn't survive a concurrent load test,              ║
║   it doesn't exist yet."                                     ║
║                                            — personal rule   ║
╚══════════════════════════════════════════════════════════════╝
```

**Open to research collabs, interesting problems, and people who care about correctness.**

[![Email](https://img.shields.io/badge/email-arnavyadavop%40gmail.com-00ff88?style=for-the-badge&logo=gmail&logoColor=white&labelColor=0a0a0f)](mailto:arnavyadavop@gmail.com)
[![GitHub](https://img.shields.io/badge/GitHub-TDevViper-00ff88?style=for-the-badge&logo=github&logoColor=white&labelColor=0a0a0f)](https://github.com/TDevViper)

<br/>

<img src="https://capsule-render.vercel.app/api?type=waving&color=0:0a0a0f,100:00ff88&height=120&section=footer"/>

</div>
