<div align="center">

<img src="https://capsule-render.vercel.app/api?type=waving&color=0:0a0a0f,50:003322,100:0a0a0f&height=200&section=header&text=Arnav%20Yadav&fontSize=62&fontColor=00ff88&fontAlign=50&fontAlignY=42&desc=Systems%20Engineer%20%E2%80%94%20AI%20%C2%B7%20Backend%20%C2%B7%20Security&descSize=16&descFontColor=aaffccbb&descAlignY=62&animation=fadeIn" width="100%"/>

<br/>

![Profile Views](https://komarev.com/ghpvc/?username=TDevViper&style=flat-square&color=00ff88&label=PROFILE+VIEWS&labelColor=0a0a0f)
&nbsp;
[![GitHub followers](https://img.shields.io/github/followers/TDevViper?label=FOLLOWERS&style=flat-square&color=00ff88&labelColor=0a0a0f&logo=github&logoColor=00ff88)](https://github.com/TDevViper)
&nbsp;
[![Email](https://img.shields.io/badge/EMAIL-arnavyadavop%40gmail.com-00ff88?style=flat-square&labelColor=0a0a0f&logo=gmail&logoColor=00ff88)](mailto:arnavyadavop@gmail.com)

<br/>

[![Typing SVG](https://readme-typing-svg.demolab.com?font=JetBrains+Mono&weight=600&size=16&duration=2800&pause=1000&color=00FF88&center=true&vCenter=true&width=760&lines=I+build+systems+I+can+defend+in+any+room.;ASTRA+%7C+MLX-Serve+%7C+FineTuneKit+%E2%80%94+one+coherent+stack.;Will+it+hold+under+concurrent+load%3F;Does+the+security+model+survive+adversarial+input%3F;Fine-tune+%E2%86%92+serve+%E2%86%92+orchestrate%2C+all+on-device.)](https://git.io/typing-svg)

</div>

<br/>

---

## 👤 &nbsp;About Me

<img align="right" src="https://github-readme-stats.vercel.app/api?username=TDevViper&show_icons=true&theme=tokyonight&hide_border=true&title_color=00ff88&icon_color=00ff88&text_color=aaaacc&bg_color=0a0a0f&custom_title=GitHub+Stats&rank_icon=github" width="42%"/>

```yaml
Name      : Arnav Yadav
Alias     : TDevViper
Domain    : AI · Backend · Security · ML Systems
Region    : India 🇮🇳
Status    : ASTRA SaaS launch · FineTuneKit v2
Exploring : EEG signals · eBPF · Neuroscience
Open to   : Internships · Research · Collabs
```

CS student from India. I build **end-to-end AI systems** — from fine-tuning LLMs on-device, to serving them at production throughput, to orchestrating agents on top.

My stack is coherent by design: **FineTuneKit** (train) → **MLX-Serve** (serve at 2.2× Ollama speed) → **ASTRA** (orchestrate with memory, RBAC, and Docker sandboxing). Each piece works standalone; together they form a private, local AI platform that rivals cloud setups.

I care about **correctness over feature count.** About *why* a decision was made, not just *that* it was made.

> *Will it hold under concurrent load? Does the security model survive adversarial input? Can someone extend this without touching the core?*

<br clear="right"/>

---

## 🗂️ &nbsp;The Stack

> These aren't isolated experiments — they form one coherent pipeline.

```
FineTuneKit  ──→  fine-tune any LLM on your data, on Apple Silicon (MLX LoRA)
     │
     ▼
MLX-Serve    ──→  serve it at ~90 tok/s flat, OpenAI-compatible API
     │
     ▼
ASTRA        ──→  orchestrate agents on top: memory · RBAC · tools · Docker sandboxing
```

---

## 🚀 &nbsp;Projects

### ◈ ASTRA — Private AI Platform

> **Runs on your hardware. Multi-user. Production-hardened. SaaS-ready.**

```
                         ASTRA REQUEST PIPELINE
  ┌─────────────────────────────────────────────────────────────────┐
  │  User Input (JWT authenticated, rate-limited by role)           │
  │      │                                                          │
  │      ▼                                                          │
  │  [Injection Filter] ──→ adversarial prompts rejected here       │
  │      ▼                                                          │
  │  [Cache Layer] ──→ LRU + semantic similarity (ChromaDB/FAISS)   │
  │      ▼                                                          │
  │  [Intent Classifier]                                            │
  │      ├──→ [Tool Router] ──→ Docker Sandbox (no net, PID cap)    │
  │      │         └──→ [Synthesizer] → natural language reply      │
  │      └──→ [Direct LLM] → Ollama local → Anthropic fallback      │
  │                ▼                                                │
  │          [TruthGuard / Critic]                                  │
  │          [MemoryTransaction] → atomic write · per-user ns       │
  │          [OTel Tracer] → Jaeger · Prometheus · Grafana          │
  │          REPLY (streamed, per-thread history)                   │
  └─────────────────────────────────────────────────────────────────┘
```

<table width="100%">
<tr>
<td width="33%" valign="top" align="center">

**Auth + RBAC**
`JWT · bcrypt · 4 Roles`

Full user account system. Four roles: owner / admin / user / guest. 13 permissions. Privilege escalation prevention baked in — you cannot assign a role equal to or above your own.

→ *No shared API key. Every request is a real identity.*

</td>
<td width="1%" align="center"><sub>│<br/>│<br/>│<br/>│<br/>│<br/>│<br/>│<br/>│</sub></td>
<td width="33%" valign="top" align="center">

**Docker Sandbox**
`Container isolation · No escape`

Code runs in a throwaway container — no network, read-only fs, all Linux capabilities dropped, PID limit, 128MB cap. Fork bombs blocked. Host fs blocked. Verified.

→ *AST walking replaced with kernel-level isolation.*

</td>
<td width="1%" align="center"><sub>│<br/>│<br/>│<br/>│<br/>│<br/>│<br/>│<br/>│</sub></td>
<td width="33%" valign="top" align="center">

**Multi-User SaaS**
`Threads · Rate limits · Isolation`

Per-user conversation threads with history + forking. Redis sliding window rate limits by role: guest 5/min, user 20, admin 60. All memory namespaced by user_id.

→ *One instance, many users, full isolation.*

</td>
</tr>
</table>

**[→ View ASTRA on GitHub](https://github.com/TDevViper/Astra_Presonal_ai)**

---

### ◈ MLX-Serve — LLM Inference for Apple Silicon

> **~90 tok/s flat. OpenAI-compatible. 2.2× faster than Ollama.**

```
Concurrency    MLX-Serve    Ollama    Latency (MLX)    Latency (Ollama)    Speedup
────────────────────────────────────────────────────────────────────────────────────
1 user         84.4 tok/s   37.8      1.52s            3.65s               2.2x ⚡
2 users        89.8 tok/s   43.5      2.18s            4.42s               2.1x ⚡
4 users        91.4 tok/s   43.7      3.51s            7.28s               2.1x ⚡
8 users        89.4 tok/s   39.5      6.38s            14.52s              2.3x ⚡
```

MLX-Serve sustains ~90 tok/s flat via continuous batching. Ollama degrades under load. Features: PagedAttention-style KV cache manager, prefix caching (9× iteration speedup on shared prompts), memory monitor + preemptor, Prometheus `/metrics`, React dashboard.

Drop-in OpenAI replacement — point any client at `http://localhost:8000`.

**[→ View MLX-Serve on GitHub](https://github.com/TDevViper/MLX-Serve)**

---

### ◈ FineTuneKit — Local LLM Fine-Tuning Pipeline

> **LoRA training on Apple Silicon. Config-driven. Full UI. No cloud required.**

Fine-tune any supported LLM on your data using MLX on Apple Silicon Metal GPU. Config-driven via `config.yaml` + Pydantic validation. Ships with a React UI for live loss charts, run comparison, and side-by-side inference between base model and fine-tuned adapter.

```yaml
# One config file controls everything
model:    mlx-community/Qwen1.5-0.5B-Chat
dataset:  data/train.jsonl
training:
  epochs: 3  |  lora_rank: 2  |  learning_rate: 2e-5
```

JSONL ingestion · ROUGE + loss evaluation · run registry · CLI (`ftk run`, `ftk runs`, `ftk validate-data`) · GGUF export · HuggingFace Hub push.

**[→ View FineTuneKit on GitHub](https://github.com/TDevViper/FineTuneKit)**

---

### ◈ Chess AI — AlphaZero-Style Reinforcement Learning

> **Zero human knowledge. Learns purely from self-play. UCI-compatible.**

ResNet policy-value network (10 blocks, 256 filters) + MCTS from scratch in PyTorch. 18 training iterations, 20k self-play games. Implements full AlphaZero loop: Observe → Plan (PUCT, c=1.5) → Act (800 simulations) → Reflect.

```
Training progression:
  Iter  5  →  Draw rate 12%  ·  Value loss 0.245
  Iter 10  →  Draw rate 34%  ·  Value loss 0.187
  Iter 18  →  Draw rate 78%  ·  Value loss 0.121  ← current

Arena (20 games): iter_18 vs iter_5  →  W:14  D:4  L:2
Elo estimate: ~1400 (intermediate club level)
```

Tackled real RL challenges: mode collapse mitigation, draw spiral prevention, training instability via batch norm + gradient clipping, parallel self-play (16 workers).

**[→ View Chess AI on GitHub](https://github.com/TDevViper/chess-ai-mcts)**

---

### ◈ MoodAI — Emotion-Aware Full-Stack App

> **Full-stack. Real transformer-based emotion detection. Not keyword matching.**

FastAPI backend + React 18 frontend. Emotion classification using `distilbert-base-uncased-emotion` — negation-aware, context-sensitive. Mood history tracking, response adaptation based on detected affect.

**[→ Backend](https://github.com/TDevViper/moodai-backend)** &nbsp;|&nbsp; **[→ Frontend](https://github.com/TDevViper/moodai-frontend)**

---

### ◈ Face Verification AI — Siamese Neural Network

> **One-shot face verification. Webcam or image upload. Apple Silicon optimized.**

Siamese Neural Network (TensorFlow/Keras) for real-time face verification. OpenCV preprocessing, Streamlit UI. Optimized for Apple Silicon M1/M2. Future path: FastAPI microservice + ONNX/CoreML export for production deployment.

**[→ View Face Verification AI on GitHub](https://github.com/TDevViper/face_verification_ai)**

---

### ◈ Other Projects

| Project | What it does | Stack |
|---------|-------------|-------|
| [spam-detector](https://github.com/TDevViper/spam-detector) | NLP spam classification pipeline | Python · sklearn |
| [HousePricePredictor](https://github.com/TDevViper/HousePricePredictor) | Regression model for real estate pricing | Python · pandas |
| [FRIDAY_Mood_Predictor](https://github.com/TDevViper/FRIDAY_Mood_Predictor) | Mood prediction module for the FRIDAY AI ecosystem | Python · ML |
| [ChatBotProject](https://github.com/TDevViper/ChatBotProject) | Early-stage conversational AI prototype | Python |

---

## 🛠 &nbsp;Tech Stack

<div align="center">

| Languages | Backend | AI / ML | Security | DevOps |
|:---:|:---:|:---:|:---:|:---:|
| Python · JS · SQL · Rust · C++ | FastAPI · JWT · WebSocket | Ollama · MLX · ChromaDB · FAISS · HuggingFace · PyTorch · TensorFlow | RBAC · Docker Sandboxing · HMAC | Docker · Redis · SQLite · Linux |

<br/>

<img src="https://skillicons.dev/icons?i=python,js,rust,fastapi,docker,redis,linux,git,pytorch,tensorflow&theme=dark&perline=5" />

</div>

**Depth signals:** async event loops · per-request context isolation · atomic memory transactions · LRU + semantic cache layering · sliding-window rate limiting · container-level code sandboxing · JWT + RBAC auth systems · LoRA fine-tuning · continuous batching · PagedAttention KV cache · MCTS with neural priors

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
| Inference engine | MLX on Apple Silicon | CUDA / cloud | 2.2× faster than Ollama on available hardware; zero infrastructure cost |
| Fine-tuning | LoRA via MLX | Full fine-tune | Memory-efficient; adapters are portable, fusable, and exportable to GGUF |
| Observability | Jaeger + Prometheus + Grafana | Managed APM (Datadog) | Full control, zero cost, OTel-compatible for future migration |

---

## 📈 &nbsp;ASTRA Audit Trail

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

## 🔐 &nbsp;Security Surface (ASTRA)

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

## 🎯 &nbsp;Current Focus

<table width="100%">
<tr>
<td width="50%">

- `01` &nbsp; ASTRA — Stripe billing + landing page launch
- `02` &nbsp; FineTuneKit v2 — expanded model support
- `03` &nbsp; EEG signal preprocessing & brain-computer interfaces

</td>
<td width="50%">

- `04` &nbsp; eBPF kernel tracing and performance tooling
- `05` &nbsp; Distributed systems patterns & consensus protocols
- `06` &nbsp; Computational neuroscience + VR signal interfaces

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
