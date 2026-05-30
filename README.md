<div align="center">

<h1>Dhia Shayeb</h1>

<p><strong>AI Engineer · Agentic Systems · Hybrid RAG · Computer Vision · MLOps · Full-Stack</strong></p>

[![Portfolio](https://img.shields.io/badge/Portfolio-dhiashayeb.vercel.app-000000?style=flat-square&logo=vercel&logoColor=white)](https://dhiashayeb.vercel.app)
[![LinkedIn](https://img.shields.io/badge/LinkedIn-dhia--shayeb-0A66C2?style=flat-square&logo=linkedin&logoColor=white)](https://linkedin.com/in/dhia-shayeb)
[![Email](https://img.shields.io/badge/Email-dhiashayeb6@gmail.com-EA4335?style=flat-square&logo=gmail&logoColor=white)](mailto:dhiashayeb6@gmail.com)
[![Status](https://img.shields.io/badge/Available-July%202026-22c55e?style=flat-square)](mailto:dhiashayeb6@gmail.com)
[![Location](https://img.shields.io/badge/Location-Tunis%2C%20Tunisia-6B7280?style=flat-square)](https://linkedin.com/in/dhia-shayeb)

</div>

---

I build AI systems that ship to production. Not demos — platforms. I own the full stack: data pipelines, model training, multi-agent orchestration, hybrid RAG, secure API design, and MLOps delivery.

Currently finishing an Engineering degree in Intelligent Software Engineering at ESPRIT (July 2026) while serving as **sole architect** of DeepCoin-Core at YEBNI: a 5-agent LangGraph platform with 47,705-vector hybrid retrieval, EfficientNet-B3 at 80.03% TTA accuracy across 438 classes, and **zero hallucination on structured facts** — delivered solo on a 7-service Docker stack with 122 automated tests and a documented novel ML research finding.

---

## Flagship · [DeepCoin-Core](https://github.com/ChaiebDhia/DeepCoin-Core)

> **A single coin photograph in. A grounded, cited historical report out. In under 20 seconds.**

End-to-end agentic AI platform for archaeological numismatics. Classifies 2,300-year-old coins via CNN, validates with computer vision forensics, and generates hallucination-free historical reports using citation-constrained RAG — all through a 5-agent LangGraph state machine with graceful degradation on every path.

### System Architecture

```
 ┌──────────────────────────────────────────────────────────────┐
 │                    RAW COIN PHOTOGRAPH                       │
 └──────────────────────────────┬───────────────────────────────┘
                                │
 ┌──────────────────────────────▼───────────────────────────────┐
 │                  Image Preprocessing                         │
 │   HoughCircles autocrop · CLAHE on LAB L-channel             │
 │   Aspect-preserving resize → zero-pad 299×299                │
 └──────────────────────────────┬───────────────────────────────┘
                                │
 ┌──────────────────────────────▼───────────────────────────────┐
 │               EfficientNet-B3  (80.03% TTA ×8)               │
 │   438 classes · ~12M params · 1,536-dim feature vector       │
 │   Output: class · confidence · top-5 · Grad-CAM++ 19×19     │
 └──────────┬──────────────────┬──────────────────┬────────────┘
            │                  │                  │
        conf > 85%         40 – 85%           conf < 40%
            │                  │                  │
 ┌──────────▼──────┐  ┌────────▼────────┐  ┌─────▼──────────────┐
 │   HISTORIAN     │  │   VALIDATOR     │  │   INVESTIGATOR     │
 │                 │  │                 │  │                    │
 │ Hybrid RAG      │  │ Multi-scale HSV │  │ Vision LLM         │
 │ BM25 + ChromaDB │  │ 3 crop sizes    │  │ (qwen3-vl:4b)      │
 │ RRF fusion      │  │ 40/60/80%       │  │ + OpenCV fallback  │
 │ [CONTEXT N]     │  │ Ag2S patina fix │  │ KB nearest-neigh.  │
 │ citation prompt │  │ KB consensus    │  │ 9,541-type search  │
 │ → LLM narrative │  │ override        │  │ → cultural matches │
 └──────────┬──────┘  └────────┬────────┘  └─────┬──────────────┘
            └──────────────────┴──────────────────┘
                                │
 ┌──────────────────────────────▼───────────────────────────────┐
 │                    SYNTHESIS AGENT                           │
 │   fpdf2 PDF · Grad-CAM++ heatmap embed · confidence pill     │
 │   Greek legend transliteration · grounded citations         │
 └──────────────────────────────┬───────────────────────────────┘
                                │
 ┌──────────────────────────────▼───────────────────────────────┐
 │              FastAPI Backend  (:8000)                        │
 │   JWT · X-API-Key · slowapi · HSTS · CSP · GZip             │
 │   SQLite WAL · X-Request-ID · Pydantic v2 · SSE streaming   │
 └──────────────────────────────┬───────────────────────────────┘
                                │
 ┌──────────────────────────────▼───────────────────────────────┐
 │             Next.js 15 Frontend  (:3000)                     │
 │   9 pages · Framer Motion · TanStack Query · Zustand         │
 │   3-state CNN display · streaming chat · admin panel        │
 └──────────────────────────────────────────────────────────────┘

 ──────────────────────────────────────────────────────────────
 HYBRID RAG ENGINE
 ──────────────────────────────────────────────────────────────
   Query ──┬── BM25Okapi keyword index  (rank-bm25)
           └── ChromaDB cosine search  (384-dim, all-MiniLM-L6-v2)
                          │
           RRF fusion:  score = Σ 1 / (60 + rank_r)
                          │
           Top-k → 5 × [CONTEXT N] citation blocks
           Source: Corpus Nummorum (DFG-funded, Berlin-Brandenburg Academy)
           Coverage: 9,541 types · 47,705 vectors · 5 semantic chunks/type
 ──────────────────────────────────────────────────────────────

 ──────────────────────────────────────────────────────────────
 LLM PROVIDER FALLBACK CHAIN
 ──────────────────────────────────────────────────────────────
   Priority 1: GITHUB_TOKEN   → GitHub Models API (Gemini 2.5 Flash)
   Priority 2: GOOGLE_API_KEY → Google AI Studio  (1,500 req/day free)
   Priority 3: OLLAMA_HOST    → Local Ollama       (gemma3:4b / qwen3-vl:4b)
   Priority 4: no keys set    → Structured KB fallback (zero crash, zero hallucination)
 ──────────────────────────────────────────────────────────────

 ──────────────────────────────────────────────────────────────
 GRACEFUL DEGRADATION — THE SYSTEM NEVER RETURNS AN EMPTY REPORT
 ──────────────────────────────────────────────────────────────
   Level 1 (conf > 85%):  CNN → Historian → RAG → LLM narrative → full PDF
   Level 2 (40–85%):      CNN hesitates → Validator OpenCV → KB consensus → PDF
   Level 3 (< 40%):       OOD input → Investigator → 3 nearest KB types → PDF
   LLM offline:           KB fields only → structured report, no prose hallucination
 ──────────────────────────────────────────────────────────────
```

### Metrics

| Metric | Result |
|--------|--------|
| CNN accuracy — TTA ×8, 438-class fine-grained classification | **80.03%** |
| Macro F1 — 438 classes | **0.7763** |
| Knowledge base coverage | **9,541 types · 47,705 vectors** (98.2% of Corpus Nummorum) |
| Hallucination on structured facts | **Zero** — citation-block grounding, all tested queries |
| Test suite | **122 / 122 passing** (unit + integration, pytest-asyncio) |
| Docker services | **7** — FastAPI · Next.js 15 · PostgreSQL · Redis · Nginx · MLflow · LocalStack |
| End-to-end pipeline latency | **< 20 s** |
| KB hybrid search latency | **< 1 ms** |
| PDF generation | **~0.4–0.5 s** |
| Frontend pages | **9** — classify · history · explore · chat · admin · docs · about · auth |
| CI matrix | Python 3.11 + 3.12 · flake8 · black · tsc |

### Key Engineering Decisions

| Decision | Choice | Why |
|----------|--------|-----|
| CNN backbone | EfficientNet-B3 | Compound scaling fits 4.3 GB VRAM; B7 does not |
| Preprocessing | CLAHE on LAB L-channel | Enhances contrast without destroying metal patina colour information |
| Class imbalance | WeightedRandomSampler | 40:1 ratio — equalises per-class exposure |
| Regularisation | Mixup α=0.2 + label smoothing 0.1 | Prevents memorisation on small dataset (7,677 images) |
| Explainability | Grad-CAM++ at `features[-4]` 19×19 | 3.6× finer than `features[-1]`; sharper multi-instance attention |
| Agent framework | LangGraph over CrewAI | Explicit state machine, conditional routing, cycles, production-ready |
| RAG retrieval | BM25 + ChromaDB + RRF | BM25 catches exact keyword hits; vectors catch semantic similarity; RRF merges both at zero reranker latency |
| Chunking | 5 semantic chunks per coin type | Targeted embeddings — material queries hit the material chunk, not a blurred blob |
| LLM grounding | `[CONTEXT N]` citation blocks | LLM writes prose; KB provides facts — structurally prevents hallucination |
| Security | `hmac.compare_digest` on API keys | Constant-time comparison prevents timing-oracle attacks |
| Thread safety | Double-checked locking on all singletons | Prevents OOM races on RAGEngine + LLM client cold startup |
| Monolith over microservices | Modular monolith | 1-person team — microservices would be premature; clean module interfaces are correct |

### Research Finding

The same trained model scored **80% on modern composite photographs** but only **15–28% on BNF 1966 catalog scans** of identical coin types — same model, same classes, different photographic era. This is an **intra-dataset distribution shift** not previously documented in numismatic ML literature. Documented in `ENGINEERING_JOURNAL.md §184`. Directly relevant to any institution digitising from analog historical catalogs.

`PyTorch` `LangGraph` `EfficientNet-B3` `ChromaDB` `BM25` `RRF` `FastAPI` `Next.js 15` `PostgreSQL` `Redis` `MLflow` `Docker` `Prometheus` `Grafana` `GitHub Actions` `Grad-CAM++` `Active Learning` `Pydantic v2` `Ollama` `fpdf2`

---

## All Projects

| Project | What it does | Stack | Key result |
|---------|-------------|-------|------------|
| [DeepCoin-Core](https://github.com/ChaiebDhia/DeepCoin-Core) | 5-agent LangGraph platform for archaeological coin classification — CNN + hybrid RAG + LLM + full-stack | PyTorch · LangGraph · FastAPI · Next.js 15 · ChromaDB · Docker | 80.03% TTA · 47k vectors · 122/122 tests · < 20 s latency · zero hallucination |
| [DevOps_SpringBoot](https://github.com/ChaiebDhia/DevOps_SpringBoot) | 18-stage Jenkins CI/CD pipeline — quality gates, zero-downtime deploys, full observability | Jenkins · Docker · SonarQube · Nexus · Prometheus · Grafana | 99.98% deployment success · < 2 min CI runtime · 100% test coverage gate |
| [Microservices](https://github.com/ChaiebDhia/Microservices) | Cloud-native travel platform — 6 independently scalable services with service mesh | Spring Cloud (Eureka · Gateway · Config) · Angular · MySQL · Docker | Service discovery · inter-service fault tolerance · API gateway routing |
| [SkillBridge](https://github.com/InnovativeSquad-PI-4TWIN4/PiWebInovativeSquad) | AI-augmented MERN skill exchange platform — real-time P2P video + Gemini AI (team of 5) | React · Node.js · MongoDB · Socket.io · WebRTC · Gemini API · Docker | Chatbot · voice assistant · quiz generator · PDF summariser · live P2P calls |
| [Voice-Controlled IoT](https://github.com/ChaiebDhia/Voice-Controlled-Assistive-Tech-with-Arduino-IoT) | Voice-controlled assistive prototype — Arduino wheelchair simulator + Python GUI assistant | Python · Arduino · HC-05 Bluetooth · SpeechRecognition · tkinter | Hands-free navigation · layered IoT architecture (perception → network → application) |

---

## Technical Stack

**Agentic AI & LLM Systems**
`LangGraph` `Multi-agent orchestration` `Confidence-based routing` `Graceful degradation` `Prompt grounding` `Hallucination mitigation` `Citation-block RAG` `Gemini API` `Ollama` `LangChain`

**RAG & Hybrid Search**
`ChromaDB` `BM25` `RRF fusion` `Semantic chunking` `all-MiniLM-L6-v2` `Vector indexing` `Knowledge base construction`

**ML & Computer Vision**
`PyTorch` `EfficientNet` `Transfer learning` `TTA` `Grad-CAM++` `Active Learning` `MLflow` `OpenCV` `CLAHE` `HSV forensics` `Albumentations`

**Backend & Data**
`FastAPI` `Pydantic v2` `PostgreSQL` `Redis` `MongoDB` `SQLAlchemy` `JWT` `HSTS/CSP` `Rate limiting` `Structured JSON logging` `SSE streaming`

**Frontend**
`Next.js 15 (App Router)` `React` `TypeScript` `Tailwind CSS` `TanStack Query` `Framer Motion` `Zustand` `WebRTC` `Socket.io` `i18n (next-intl)`

**DevOps & Cloud**
`Docker Compose` `GitHub Actions` `Jenkins (18-stage)` `Prometheus` `Grafana` `Alertmanager` `Nginx` `SonarQube` `Nexus` `AWS` `Oracle OCI`

---

## Experience

**AI Engineer — PFE (Graduation Project)** · YEBNI, Tunisia · Feb 2026 – Jul 2026

Sole architect and engineer of DeepCoin-Core. End-to-end ownership across CNN training (EfficientNet-B3, AMP, Mixup, WeightedRandomSampler, 80.03% TTA), 5-agent LangGraph orchestration, hybrid RAG pipeline (BM25 + ChromaDB + RRF, 47,705 vectors), 9-page Next.js 15 frontend, JWT/HSTS/CSP security hardening, 122-test pytest suite, and CI/CD on GitHub Actions. Discovered and documented a novel intra-dataset distribution shift in numismatic ML not previously reported in the literature.

**Full-Stack Engineering Intern** · Tunisia Telecom · Jul 2025 – Aug 2025

Python automation platform for FTTH & 5G operations serving 14M+ subscribers. Netmiko scripting across Cisco/Huawei network equipment for ACL, Anti-DDoS, RADIUS, and QoS provisioning — 80% reduction in manual configuration time. Delivered Streamlit + Plotly real-time KPI dashboard (latency < 25 ms · throughput > 95 Mbps · availability > 99.5%).

**Full-Stack Intern** · Bright Soft · Jul 2022 – Aug 2022

React/Node.js SaaS feature development and AI/NLP document processing workflows. Introduced unit testing practices that improved release confidence.

---

## Education

**ESPRIT, Tunis** — Engineering Degree · Intelligent Software Engineering (EUR-ACE accredited, BAC+5) · 2023–2026

**ISIK, Le Kef** — BSc Computer Science · Software Engineering · 2020–2023

---

## Certifications

`Anthropic Agent Skills` · `Aviatrix ACE — Multi-Cloud Network Associate` · `Oracle OCI Associate` · `AWS Cloud Foundations` · `Scrum Fundamentals Certified (SFC)`

---

## Open to Work

Seeking **AI Engineer** and **Full-Stack AI** roles — Tunisia · France · Remote. Available **July 2026**.

[LinkedIn](https://linkedin.com/in/dhia-shayeb) · [Portfolio](https://dhiashayeb.vercel.app) · [dhiashayeb6@gmail.com](mailto:dhiashayeb6@gmail.com)
