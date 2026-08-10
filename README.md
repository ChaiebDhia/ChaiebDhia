<div align="center">

<img src="https://capsule-render.vercel.app/api?type=waving&color=0:0f172a,100:1e40af&height=200&section=header&text=Dhia%20Shayeb&fontSize=60&fontColor=ffffff&fontAlignY=38&desc=AI%20Engineer%20%7C%20Agentic%20Systems%20%C2%B7%20Hybrid%20RAG%20%C2%B7%20MLOps%20%C2%B7%20Full-Stack&descAlignY=58&descSize=18&descColor=93c5fd" width="100%"/>

<br/>

[![Typing SVG](https://readme-typing-svg.demolab.com?font=JetBrains+Mono&weight=600&size=20&duration=3000&pause=1000&color=3B82F6&center=true&vCenter=true&width=750&lines=Building+AI+systems+that+ship+to+production.;LangGraph+%C2%B7+Hybrid+RAG+%C2%B7+MLOps+%C2%B7+Full-Stack;47k-vector+RAG+%C2%B7+92%25+cost+reduction+%C2%B7+80.03%25+CV;Available+Now+%C2%B7+UAE+%C2%B7+Germany+%C2%B7+Netherlands+%C2%B7+Canada)](https://git.io/typing-svg)

<br/>

[![Portfolio](https://img.shields.io/badge/Portfolio-dhiashayeb.vercel.app-000000?style=for-the-badge&logo=vercel&logoColor=white)](https://dhiashayeb.vercel.app)
[![LinkedIn](https://img.shields.io/badge/LinkedIn-dhia--shayeb-0A66C2?style=for-the-badge&logo=linkedin&logoColor=white)](https://linkedin.com/in/dhia-shayeb)
[![Email](https://img.shields.io/badge/Email-dhiashayeb6@gmail.com-EA4335?style=for-the-badge&logo=gmail&logoColor=white)](mailto:dhiashayeb6@gmail.com)
[![Available](https://img.shields.io/badge/Available-Now-22c55e?style=for-the-badge)](mailto:dhiashayeb6@gmail.com)
[![Relocation](https://img.shields.io/badge/Relocation-Immediate-blue?style=for-the-badge)](mailto:dhiashayeb6@gmail.com)

</div>

---

I build AI systems that ship. Not prototypes.

I own the full stack: data pipelines, model training, multi-agent orchestration,
hybrid RAG, secure API design, and MLOps delivery. For my graduation project
at YEBNI, I architected DeepCoin-Core, a 5-agent LangGraph platform with
47,705-vector hybrid retrieval, EfficientNet-B3 at 80.03% TTA accuracy across
438 classes, and zero hallucination on structured facts through citation-constrained
RAG. Delivered end-to-end on a 7-service Docker stack with 122 passing tests,
a full-stack Next.js 15 frontend, and a documented novel ML research finding on
intra-dataset distribution shift.

Available now. Immediate relocation.

---

## Flagship · [DeepCoin-Core](https://github.com/ChaiebDhia/DeepCoin-Core)

> **A single coin photograph in. A grounded, cited historical report out. In under 20 seconds.**

End-to-end agentic AI platform for archaeological numismatics. Classifies 2,300-year-old coins via CNN, validates with computer vision forensics, and generates hallucination-free historical reports using citation-constrained RAG through a 5-agent LangGraph state machine with graceful degradation on every path.

### System Architecture

```
┌──────────────────────────────────────────────────────────────┐
│                    RAW COIN PHOTOGRAPH                       │
└──────────────────────────────┬───────────────────────────────┘
                               │
┌──────────────────────────────▼───────────────────────────────┐
│                  Image Preprocessing                         │
│   HoughCircles autocrop · CLAHE on LAB L-channel             │
│   Aspect-preserving resize  zero-pad 299x299                 │
└──────────────────────────────┬───────────────────────────────┘
                               │
┌──────────────────────────────▼───────────────────────────────┐
│               EfficientNet-B3  (80.03% TTA x8)               │
│   438 classes · ~12M params · 1,536-dim feature vector       │
│   Output: class · confidence · top-5 · Grad-CAM++ 19x19     │
└──────────┬──────────────────┬──────────────────┬────────────┘
           │                  │                  │
       conf > 85%         40 to 85%         conf < 40%
           │                  │                  │
┌──────────▼──────┐  ┌────────▼────────┐  ┌─────▼──────────────┐
│   HISTORIAN     │  │   VALIDATOR     │  │   INVESTIGATOR     │
│ Hybrid RAG      │  │ Multi-scale HSV │  │ Vision LLM         │
│ BM25 + ChromaDB │  │ 3 crop sizes    │  │ (qwen3-vl:4b)      │
│ RRF fusion      │  │ Ag2S patina fix │  │ KB nearest-neigh.  │
│ citation prompt │  │ KB consensus    │  │ 9,541-type search  │
│ LLM narrative   │  │ override        │  │ cultural matches   │
└──────────┬──────┘  └────────┬────────┘  └─────┬──────────────┘
           └─────────────────┬┘──────────────────┘
                             │
┌────────────────────────────▼─────────────────────────────────┐
│                    SYNTHESIS AGENT                           │
│   fpdf2 PDF · Grad-CAM++ heatmap embed · grounded citations │
└────────────────────────────┬─────────────────────────────────┘
                             │
┌────────────────────────────▼─────────────────────────────────┐
│   FastAPI :8000  ·  JWT · HSTS · CSP · slowapi · SSE        │
└────────────────────────────┬─────────────────────────────────┘
                             │
┌────────────────────────────▼─────────────────────────────────┐
│   Next.js 15 :3000  ·  9 pages · Framer Motion · Zustand    │
└──────────────────────────────────────────────────────────────┘

HYBRID RAG ENGINE
  BM25Okapi keyword index  +  ChromaDB cosine search (384-dim)
  RRF fusion: score = sum of 1 divided by (60 + rank)
  5 x [CONTEXT N] citation blocks · 47,705 vectors · under 1ms

LLM FALLBACK CHAIN
  1. GitHub Models API (Gemini 2.5 Flash)
  2. Google AI Studio (1,500 req/day free)
  3. Local Ollama (gemma3:4b / qwen3-vl:4b)
  4. Structured KB fallback  zero crash, zero hallucination

GRACEFUL DEGRADATION  SYSTEM NEVER RETURNS AN EMPTY REPORT
  conf > 85%   CNN  RAG  LLM narrative  full PDF
  40 to 85%    CNN  OpenCV validator  KB consensus  PDF
  under 40%    Investigator  3 nearest KB types  PDF
  LLM offline  KB fields only  structured report, no hallucination
```

### Metrics

| Metric | Result |
|--------|--------|
| CNN accuracy, TTA x8, 438 classes | **80.03%** |
| Macro F1, 438 classes | **0.7763** |
| Knowledge base | **9,541 types · 47,705 vectors** (98.2% Corpus Nummorum) |
| Hallucination on structured facts | **Zero** |
| Test suite | **122 / 122 passing** |
| Docker services | **7** |
| End-to-end latency | **under 20 s** |
| Hybrid search latency | **under 1 ms** |
| PDF generation | **0.4 to 0.5 s** |

### Key Engineering Decisions

| Decision | Choice | Why |
|----------|--------|-----|
| CNN backbone | EfficientNet-B3 | Compound scaling fits 4.3 GB VRAM, B7 does not |
| Preprocessing | CLAHE on LAB L-channel | Enhances contrast without destroying metal patina colour |
| Class imbalance | WeightedRandomSampler | 40 to 1 ratio, equalises per-class exposure |
| Regularisation | Mixup a=0.2 + label smoothing 0.1 | Prevents memorisation on 7,677 images |
| Explainability | Grad-CAM++ at features[-4] 19x19 | 3.6x finer than features[-1] |
| Agent framework | LangGraph over CrewAI | Explicit state machine, conditional routing, cycles |
| RAG retrieval | BM25 + ChromaDB + RRF | Keyword + semantic + zero reranker latency |
| LLM grounding | [CONTEXT N] citation blocks | Structurally prevents hallucination |
| Protocol | MCP (Model Context Protocol) | Standard agent-to-tool interface for extensibility |
| Security | hmac.compare_digest on API keys | Prevents timing-oracle attacks |
| Thread safety | Double-checked locking on singletons | Prevents OOM races on RAGEngine cold startup |

### Research Finding

The same trained model scored **80% on modern photographs** but only **15 to 28% on BNF 1966 catalog scans** of identical coin types. Same model, same classes, different photographic era. An **intra-dataset distribution shift not previously documented** in numismatic ML literature. Documented in `ENGINEERING_JOURNAL.md §184`.

---

## All Projects

| Project | What it does | Stack | Key result |
|---------|-------------|-------|------------|
| [DeepCoin-Core](https://github.com/ChaiebDhia/DeepCoin-Core) | 5-agent LangGraph platform, CNN + hybrid RAG + LLM + full-stack | PyTorch · LangGraph · FastAPI · Next.js 15 · ChromaDB · Docker | 80.03% TTA · 47k vectors · 122/122 tests · zero hallucination |
| [Overlord Pipeline](https://github.com/ChaiebDhia/overlord-ai-video-pipeline) | 5-stage multi-LLM video pipeline, GPT-4o + Whisper word timestamps + FFmpeg | TypeScript · Node.js · OpenAI · Claude · GROQ · FFmpeg | Under 15s generation · approx $0.02/video · 100% free-tier capable |
| [SkillBridge](https://github.com/InnovativeSquad-PI-4TWIN4/PiWebInovativeSquad) | AI-augmented MERN skill exchange platform, team of 5 | React · Node.js · MongoDB · WebRTC · Socket.io · Gemini API | P2P video · quiz engine · PDF summariser · live collab |
| [DevOps Pipeline](https://github.com/ChaiebDhia/DevOps_SpringBoot) | 18-stage Jenkins CI/CD, quality gates, zero-downtime deploys | Jenkins · Docker · SonarQube · Prometheus · Grafana | 99.98% success rate · under 2 min runtime |

---

## Technical Stack

<div align="center">

![LangGraph](https://img.shields.io/badge/LangGraph-000000?style=flat-square)
![MCP](https://img.shields.io/badge/MCP_Model_Context_Protocol-6366F1?style=flat-square)
![PyTorch](https://img.shields.io/badge/PyTorch-EE4C2C?style=flat-square&logo=pytorch&logoColor=white)
![Claude](https://img.shields.io/badge/Claude_API-D4A843?style=flat-square)
![OpenAI](https://img.shields.io/badge/OpenAI-412991?style=flat-square&logo=openai&logoColor=white)
![Gemini](https://img.shields.io/badge/Gemini-4285F4?style=flat-square&logo=google&logoColor=white)
![Ollama](https://img.shields.io/badge/Ollama-000000?style=flat-square)
![ChromaDB](https://img.shields.io/badge/ChromaDB-FF6B35?style=flat-square)
![FastAPI](https://img.shields.io/badge/FastAPI-009688?style=flat-square&logo=fastapi&logoColor=white)
![Next.js](https://img.shields.io/badge/Next.js_15-000000?style=flat-square&logo=next.js&logoColor=white)
![TypeScript](https://img.shields.io/badge/TypeScript-007ACC?style=flat-square&logo=typescript&logoColor=white)
![Docker](https://img.shields.io/badge/Docker-2496ED?style=flat-square&logo=docker&logoColor=white)
![PostgreSQL](https://img.shields.io/badge/PostgreSQL-316192?style=flat-square&logo=postgresql&logoColor=white)
![Redis](https://img.shields.io/badge/Redis-DC382D?style=flat-square&logo=redis&logoColor=white)
![GitHub Actions](https://img.shields.io/badge/GitHub_Actions-2088FF?style=flat-square&logo=githubactions&logoColor=white)
![Jenkins](https://img.shields.io/badge/Jenkins-D24939?style=flat-square&logo=jenkins&logoColor=white)
![Prometheus](https://img.shields.io/badge/Prometheus-E6522C?style=flat-square&logo=prometheus&logoColor=white)
![Grafana](https://img.shields.io/badge/Grafana-F46800?style=flat-square&logo=grafana&logoColor=white)
![AWS](https://img.shields.io/badge/AWS-FF9900?style=flat-square&logo=amazonaws&logoColor=white)
![OpenCV](https://img.shields.io/badge/OpenCV-5C3EE8?style=flat-square&logo=opencv&logoColor=white)
![MLflow](https://img.shields.io/badge/MLflow-0194E2?style=flat-square&logo=mlflow&logoColor=white)

</div>

---

## GitHub Stats

<div align="center">

<img height="170em" src="https://github-readme-stats.vercel.app/api?username=ChaiebDhia&show_icons=true&theme=tokyonight&include_all_commits=true&count_private=true&hide_border=true&bg_color=0d1117&title_color=3b82f6&icon_color=3b82f6&text_color=c9d1d9&hide_rank=true"/>
<img height="170em" src="https://github-readme-stats.vercel.app/api/top-langs/?username=ChaiebDhia&layout=compact&theme=tokyonight&hide_border=true&bg_color=0d1117&title_color=3b82f6&text_color=c9d1d9&langs_count=8&hide=html,css"/>

<br/>

<img src="https://streak-stats.demolab.com/?user=ChaiebDhia&theme=tokyonight&hide_border=true&background=0d1117&ring=3b82f6&fire=3b82f6&currStreakLabel=3b82f6" alt="GitHub Streak"/>

</div>

---

## Experience

**AI Engineer** · YEBNI, Tunisia · Feb 2026 to Aug 2026

Sole architect of DeepCoin-Core. End-to-end ownership from CNN training to production deployment. EfficientNet-B3 with AMP, Mixup, WeightedRandomSampler reaching 80.03% TTA accuracy. 5-agent LangGraph orchestration with confidence-based routing. Hybrid RAG with BM25, ChromaDB, and RRF across 47,705 vectors. 9-page Next.js 15 frontend with SSE streaming. JWT, HSTS, and CSP security hardening. 122-test pytest suite. CI/CD on GitHub Actions. Discovered and documented a novel intra-dataset distribution shift in numismatic ML not previously reported in the literature. Cut commercial LLM spend 92% by routing to local Ollama under Pydantic v2 schema enforcement.

**Full-Stack Engineering Intern** · Tunisia Telecom · June 2025 to Aug 2025

Python automation platform serving 14M+ subscribers. Netmiko scripting across Cisco and Huawei hardware. 80% reduction in manual configuration time. Real-time KPI dashboard with under 25ms latency and 99.5% availability.

**Full-Stack Intern** · Bright Soft · Jul 2022 to Aug 2022

React and Node.js SaaS features and AI/NLP document processing pipelines.

---

## Education

**ESPRIT, Tunis** · Engineering Degree · Intelligent Software Engineering (EUR-ACE, BAC+5) · 2023 to 2026

**ISIK, Le Kef** · BSc Computer Science · Software Engineering · 2020 to 2023

---

## Certifications

`Anthropic Agent Skills` · `Aviatrix ACE Multi-Cloud` · `Oracle OCI Associate` · `AWS Academy Cloud Foundations`

---

## Open to Work

**Available Now · Immediate Relocation**

AI Engineer · Applied AI Engineer · Forward-Deployed AI Engineer

UAE · Germany · Netherlands · Canada · Ireland · Remote

<div align="center">

[![Let's Connect](https://img.shields.io/badge/Let's_Connect-0A66C2?style=for-the-badge&logo=linkedin&logoColor=white)](https://linkedin.com/in/dhia-shayeb)
[![View Portfolio](https://img.shields.io/badge/View_Portfolio-000000?style=for-the-badge&logo=vercel&logoColor=white)](https://dhiashayeb.vercel.app)
[![Send Email](https://img.shields.io/badge/Send_Email-EA4335?style=for-the-badge&logo=gmail&logoColor=white)](mailto:dhiashayeb6@gmail.com)

<img src="https://capsule-render.vercel.app/api?type=waving&color=0:1e40af,100:0f172a&height=100&section=footer" width="100%"/>

</div>
