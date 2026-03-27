<div align="center">

<img src="https://capsule-render.vercel.app/api?type=cylinder&color=0:000000,50:001a0d,100:000000&height=280&section=header&text=ARNAV%20YADAV&fontSize=80&fontColor=00ff88&animation=blinking&fontAlignY=45&desc=TDevViper%20%E2%80%94%20I%20build%20things%20that%20survive%20scrutiny&descSize=16&descAlignY=68&descColor=44ff99&stroke=00ff88&strokeWidth=1"/>

</div>

<div align="center">

<img src="https://readme-typing-svg.demolab.com?font=JetBrains+Mono&weight=800&size=15&duration=1800&pause=600&color=00FF88&center=true&vCenter=true&width=800&lines=%24+whoami+%E2%86%92+systems+engineer%2C+correctness-first;%24+cat+philosophy.txt+%E2%86%92+%22will+it+hold+under+concurrent+load%3F%22;%24+./astra+--score+%E2%86%92+62%2F100+%E2%86%92+93%2F100+%E2%80%94+five+phases%2C+zero+shortcuts;%24+grep+-r+%22shortcuts%22+.%2F+%E2%86%92+no+matches+found;%24+ls+deep_dives%2F+%E2%86%92+eBPF+%7C+EEG+%7C+vLLM+%7C+neuroscience+%7C+VR" />

<br/>

[![GitHub followers](https://img.shields.io/github/followers/TDevViper?style=for-the-badge&logo=github&color=00ff88&labelColor=060d0a&logoColor=00ff88)](https://github.com/TDevViper)
[![Email](https://img.shields.io/badge/arnavyadavop%40gmail.com-write%20me-00ff88?style=for-the-badge&logo=gmail&logoColor=00ff88&labelColor=060d0a)](mailto:arnavyadavop@gmail.com)
[![LinkedIn](https://img.shields.io/badge/LinkedIn-connect-00ff88?style=for-the-badge&logo=linkedin&logoColor=00ff88&labelColor=060d0a)](https://linkedin.com)
![Views](https://komarev.com/ghpvc/?username=TDevViper&style=for-the-badge&color=00ff88&labelColor=060d0a&label=PROFILE+VIEWS)

</div>

---

```
┌─────────────────────────────────────────────────────────────────────────┐
│  > INITIALIZING PROFILE...                                              │
│  > LOADING: arnav_yadav.json                                            │
│  > STATUS: building in public — one phase at a time                     │
└─────────────────────────────────────────────────────────────────────────┘
```

<img align="right" width="340" src="https://media.giphy.com/media/qgQUggAC3Pfv687qPC/giphy.gif"/>

### `$ cat about.txt`

CS student from India. My main project — **ASTRA** — is a local AI system I rebuilt from scratch after a full Staff+ engineering audit: concurrency correctness, security surface, architectural gaps, performance ceilings.

It went from **62 → 93/100** across five documented phases. Not because I added features — because I fixed what was actually wrong.

I care about **why** a decision was made, not just **that** it was made.

Three questions I ask before shipping anything:

```python
assert system.survives_concurrent_load()      # ✓ or it doesn't exist
assert security_model.survives_adversarial()  # ✓ or it's not secure
assert codebase.extensible_without_core_edits() # ✓ or it's a monolith
```

Currently exploring: **EEG signal processing × VR × computational neuroscience**

<br clear="right"/>

---

### `$ ./astra --architecture`

> **100% on-device. No cloud. No data leaves your machine.**

```
┌──────────────────────────────────────────────────────────────────┐
│                        ASTRA PIPELINE                            │
├──────────────────────────────────────────────────────────────────┤
│                                                                  │
│  Input → [Injection Filter] → [Cache] → [Intent Classifier]     │
│                                              │                   │
│              ┌───────────────────────────────┘                   │
│              ▼                                                   │
│         [Tool Router] ──→ LLM selects tool via JSON schema       │
│              │            (web_search / git / monitor / ...)     │
│              ▼                                                   │
│         [Executor] → [Synthesizer] → [Critic / TruthGuard]      │
│              │                                                   │
│              ▼                                                   │
│         [MemoryTransaction] → atomic write or rollback           │
│              │                                                   │
│              ▼                                                   │
│         [OTel Tracer] → async, non-blocking, fire-and-forget     │
│              │                                                   │
│              ▼                                                   │
│           REPLY                                                  │
└──────────────────────────────────────────────────────────────────┘
```

| Component | Why it exists |
|-----------|--------------|
| `PipelineRegistry` | Add capabilities without touching `brain.py` |
| `LLMBackend` ABC | Swap Ollama → OpenAI → vLLM in 4 method overrides |
| `RequestContext` | Per-request isolation — no shared state, no race conditions |
| `MemoryTransaction` | Atomic batch writes — no partial saves under failure |
| HMAC-signed tokens | `client_approved: true` is rejected at the server |
| 3-session quality gate | One accidental thumbs-up can't poison the dataset |
| Async OTel spans | Non-blocking traces on every request |
| Injection filter layer | Adversarial prompts caught before LLM reach |
| Structured tool calling | LLM reads JSON schemas, picks tool + args — no regex |

**[→ ASTRA on GitHub](https://github.com/TDevViper/Astra_Presonal_ai)**

---

### `$ git log --audit --oneline`

> Most people ship. I audited, documented every flaw, then fixed them in order.

```
┌─────────────────────────────────────────────────────────────────┐
│  PHASE 0    62/100  ██████▒▒▒▒▒▒▒▒▒▒  Initial build            │
│  PHASE 1–3  72/100  ███████▒▒▒▒▒▒▒▒▒  FastAPI, OTel, logging   │
│  CR FIXES   78/100  ████████▒▒▒▒▒▒▒▒  Concurrency, double LLM  │
│  SECURITY   83/100  █████████▒▒▒▒▒▒▒  Injection, signed tokens  │
│  ARCH       88/100  ██████████▒▒▒▒▒▒  Async obs, lifespan mgmt  │
│  PHASE C    93/100  ████████████▒▒▒▒  Pipeline, abstraction     │
└─────────────────────────────────────────────────────────────────┘

  Remaining 7pts: PostgreSQL + JWT multi-user auth.
  Infrastructure, not code. I know what they require.
  I chose to ship over engineering for zero users.
  That's also an architectural decision.
```

---

### `$ grep -r "bugs_found" audit/ --format=table`

| Bug | Root Cause | Fix Applied |
|-----|-----------|-------------|
| Concurrent history corruption | Shared mutable list across async requests | `RequestContext` per-request isolation |
| Double LLM invocation | Control flow ambiguity in pipeline | Explicit state machine, single exit |
| Client-trusted `approved` flag | No server-side token validation | HMAC-signed tool tokens |
| Partial memory saves on failure | Non-atomic write operations | `MemoryTransaction` with rollback |
| Blocking OTel traces | Synchronous span flush in hot path | Async export, fire-and-forget |
| Dataset poisoning via feedback | No quality gate | 3-session confirmation threshold |
| Regex-based tool routing | Fragile pattern matching | Structured tool calling with JSON schemas |

---

### `$ cat stack.py`

<div align="center">

<img src="https://skillicons.dev/icons?i=python,fastapi,docker,redis,linux,git,bash,rust,sqlite&theme=dark" />
<br/>
<img src="https://skillicons.dev/icons?i=js,c,cpp,github&theme=dark" />

</div>

```python
class Arnav:
    languages  = ["Python", "JavaScript", "SQL", "Rust (learning)"]
    backend    = ["FastAPI", "async/await", "WebSocket", "SSE"]
    ai_stack   = ["Ollama", "ChromaDB", "FAISS", "LLMBackend abstraction"]
    infra      = ["Docker Compose", "Redis", "SQLite", "OpenTelemetry"]
    security   = ["HMAC tokens", "injection filters", "sandboxed execution"]
    exploring  = ["eBPF tracing", "EEG signal processing", "distributed systems"]
    region     = "India 🇮🇳"
    status     = "building + applying to interesting problems"

    def ships_when(self, feature) -> bool:
        return (
            feature.survives_concurrent_load()
            and feature.security_model_is_sound()
            and feature.someone_else_can_extend_it()
        )
```

---

### `$ ls -la ~/deep_dives/`

```bash
drwxr-xr-x  eBPF_kernel_tracing/          # perf, bcc, kernel internals
drwxr-xr-x  EEG_signal_processing/        # bandpass filters, artifact removal
drwxr-xr-x  vLLM_continuous_batching/     # PagedAttention, throughput theory
drwxr-xr-x  distributed_systems_patterns/ # consensus, replication, CRDTs
drwxr-xr-x  computational_neuroscience/   # spiking networks, Hodgkin-Huxley
drwxr-xr-x  VR_brain_signal_interface/    # BCI research, P300, motor imagery
```

---

### `$ cat dev_log.md`

| Date | Session |
|------|---------|
| `2026-03-27` | ASTRA: Structured tool calling — LLM picks tools via JSON schemas |
| `2026-03-22` | README overhaul — structure, devlog, badges |
| `2026-03-21` | Deep dive: eBPF kernel tracing internals |
| `2026-03-20` | ASTRA: Refining the injection filter layer |
| `2026-03-19` | Reading: vLLM continuous batching architecture |
| `2026-03-18` | EEG signal preprocessing experiments |

---

### `$ diff what_i_want.txt what_i_dont.txt`

<div align="center">

| `[+] LOOKING FOR` | `[-] NOT LOOKING FOR` |
|-------------------|----------------------|
| Hard systems problems | Tutorials dressed as projects |
| Security × AI intersection | Another CRUD wrapper |
| Neuroscience + real engineering | Surface-level ML scripts |
| Architecture reviews | "Ship fast, fix never" |
| Research with implementation depth | Hype without substance |
| Correctness-first teams | "It works on my machine" |

</div>

---

### `$ neofetch --stats`

<div align="center">

<img src="https://github-readme-stats.vercel.app/api?username=TDevViper&show_icons=true&theme=tokyonight&hide_border=true&bg_color=060d0a&title_color=00ff88&icon_color=00ff88&text_color=aaaacc&ring_color=00ff88" height="165"/>
<img src="https://github-readme-streak-stats.herokuapp.com/?user=TDevViper&theme=tokyonight&hide_border=true&background=060d0a&ring=00ff88&fire=00ff88&currStreakLabel=00ff88" height="165"/>

<br/>

<img src="https://github-readme-stats.vercel.app/api/top-langs/?username=TDevViper&layout=compact&theme=tokyonight&hide_border=true&bg_color=060d0a&title_color=00ff88&text_color=aaaacc&langs_count=8" height="145"/>

</div>

---

### `$ cat activity_graph`

<div align="center">
<img src="https://github-readme-activity-graph.vercel.app/graph?username=TDevViper&theme=react-dark&bg_color=060d0a&color=00ff88&line=00ff88&point=ffffff&hide_border=true&area=true&area_color=00ff8820" width="100%"/>
</div>

---

<div align="center">

```
╔═══════════════════════════════════════════════════════════════════╗
║                                                                   ║
║   "I don't stop at it works.                                      ║
║    I ask: will it hold under concurrent load?                     ║
║           does the security model survive adversarial input?      ║
║           can someone extend this without touching the core?      ║
║                                                                   ║
║    If the answer to any of those is no — it's not done yet."      ║
║                                                                   ║
╚═══════════════════════════════════════════════════════════════════╝
```

**Open to: research collabs · hard problems · people who care about correctness**

[![Email](https://img.shields.io/badge/arnavyadavop%40gmail.com-00ff88?style=for-the-badge&logo=gmail&logoColor=00ff88&labelColor=060d0a)](mailto:arnavyadavop@gmail.com)
[![GitHub](https://img.shields.io/badge/TDevViper-00ff88?style=for-the-badge&logo=github&logoColor=00ff88&labelColor=060d0a)](https://github.com/TDevViper)

<br/>

<img src="https://capsule-render.vercel.app/api?type=cylinder&color=0:000000,50:001a0d,100:000000&height=120&section=footer&text=%24+exit+0&fontSize=24&fontColor=00ff88&animation=blinking"/>

</div>
