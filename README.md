<div align="center">

# Dhia Shayeb — AI Engineer

**Agentic AI · Hybrid RAG · Computer Vision · MLOps · Full-Stack**

[![Portfolio](https://img.shields.io/badge/Portfolio-dhiashayeb.vercel.app-black?style=flat-square&logo=vercel)](https://dhiashayeb.vercel.app)
[![LinkedIn](https://img.shields.io/badge/LinkedIn-dhia--shayeb-0A66C2?style=flat-square&logo=linkedin)](https://linkedin.com/in/dhia-shayeb)
[![Email](https://img.shields.io/badge/Email-dhiashayeb6@gmail.com-EA4335?style=flat-square&logo=gmail)](mailto:dhiashayeb6@gmail.com)
[![Available](https://img.shields.io/badge/Status-Available%20July%202026-22c55e?style=flat-square)](mailto:dhiashayeb6@gmail.com)

</div>

---

I build AI systems that ship to production — from raw model training through multi-agent orchestration, hybrid RAG, and full-stack delivery. Currently finishing an Engineering degree in Intelligent Software Engineering at ESPRIT (July 2026) while serving as sole architect of **DeepCoin-Core** at YEBNI: a 5-agent LangGraph platform with a 47,705-vector knowledge base, EfficientNet-B3 at 80.03% TTA accuracy, and zero hallucination on structured facts — delivered solo on a 7-service Docker stack with 122 automated tests.

---

## Flagship Project

### [DeepCoin-Core](https://github.com/ChaiebDhia/DeepCoin-Core) — Agentic AI Platform for Archaeological Numismatics

> A single coin photograph in. A grounded, cited historical report out. In under 20 seconds.

```
📷 Coin Photo
      │
      ▼
┌─────────────────────────────────────────────────┐
│  Image Preprocessing                            │
│  HoughCircles autocrop · CLAHE (LAB L-ch.)      │
│  Aspect-preserving 299×299 resize               │
└──────────────────────┬──────────────────────────┘
                       │
                       ▼
┌─────────────────────────────────────────────────┐
│  EfficientNet-B3 CNN                            │
│  438 classes · TTA ×8 · 80.03% accuracy         │
│  → class + confidence + top-5 + Grad-CAM++      │
└───────┬──────────────┬──────────────────┬───────┘
        │              │                  │
    conf > 85%     40 – 85%           conf < 40%
        │              │                  │
        ▼              ▼                  ▼
  ┌──────────┐  ┌──────────────┐  ┌──────────────────┐
  │ Historian│  │  Validator   │  │   Investigator   │
  │ RAG + LLM│  │ Multi-scale  │  │ VLM + OpenCV     │
  │ narrative│  │ HSV forensics│  │ 9,541-type KB    │
  └────┬─────┘  └──────┬───────┘  └────────┬─────────┘
       └────────────────┴──────────────────┘
                        │
                        ▼
          ┌─────────────────────────┐
          │     Synthesis Agent     │
          │  PDF · Grad-CAM embed   │
          │  Grounded citations     │
          └─────────────────────────┘
```

**Hybrid RAG Engine:** BM25 keyword index + ChromaDB vector search (cosine, 384-dim) → RRF fusion → 5 `[CONTEXT N]` citation blocks → LLM writes prose only from verified facts. Zero hallucination on structured fields across all tested queries.

| Metric | Result |
|--------|--------|
| CNN accuracy — TTA ×8, 438 classes | **80.03%** |
| Knowledge base coverage | **9,541 types / 47,705 vectors** |
| Hallucination on structured facts | **Zero** (citation-block grounding) |
| Test suite | **122 / 122 passing** |
| Docker services | **7** (FastAPI · Next.js 15 · PostgreSQL · Redis · Nginx · MLflow · LocalStack) |
| End-to-end latency | **< 20 s** |
| Frontend pages | **9** (classify · history · explore · chat · admin · docs · about · auth) |
| Security hardening | JWT · X-API-Key · HSTS · CSP · slowapi · Pydantic v2 · prompt injection guard |

**Research finding:** The same trained model scored 80% on modern composite photographs but 15–28% on BNF 1966 catalog scans of identical coin types — an intra-dataset distribution shift not previously documented in numismatic ML literature. Documented in Engineering Journal §184.

`PyTorch` · `LangGraph` · `FastAPI` · `Next.js 15` · `ChromaDB` · `BM25` · `PostgreSQL` · `Redis` · `MLflow` · `Docker` · `Prometheus` · `Grafana` · `GitHub Actions`

---

## All Projects

| Project | What it does | Stack | Key result |
|---------|-------------|-------|------------|
| [DeepCoin-Core](https://github.com/ChaiebDhia/DeepCoin-Core) | 5-agent LangGraph platform — archaeological coin classification via CNN + hybrid RAG + LLM | PyTorch · LangGraph · FastAPI · Next.js 15 · ChromaDB · Docker | 80.03% accuracy · 47k vectors · 122/122 tests · < 20 s latency |
| [DevOps_SpringBoot](https://github.com/ChaiebDhia/DevOps_SpringBoot) | 18-stage Jenkins CI/CD pipeline with quality gates, zero-downtime deploys, full observability | Jenkins · Docker · SonarQube · Nexus · Prometheus · Grafana | 99.98% deployment success · < 2 min CI runtime · 100% test coverage enforcement |
| [Microservices](https://github.com/ChaiebDhia/Microservices) | Cloud-native travel management platform — 6 independently scalable services | Spring Cloud · Eureka · Gateway · Angular · MySQL · Docker | Service discovery · inter-service fault tolerance · API gateway routing |
| [SkillBridge](https://github.com/InnovativeSquad-PI-4TWIN4/PiWebInovativeSquad) | AI-augmented MERN skill exchange platform — real-time P2P video + Gemini AI features | React · Node.js · MongoDB · Socket.io · WebRTC · Gemini API · Docker | Chatbot · voice assistant · quiz generator · PDF summariser · live P2P calls |
| [Voice-Controlled IoT](https://github.com/ChaiebDhia/Voice-Controlled-Assistive-Tech-with-Arduino-IoT) | Voice-controlled assistive prototype — Arduino wheelchair simulator + Python GUI | Python · Arduino · Bluetooth (HC-05) · SpeechRecognition · tkinter | Hands-free navigation via voice commands · layered IoT architecture |

---

## Stack

**Agentic AI & LLMs**
`LangGraph` `Multi-agent orchestration` `Confidence routing` `Prompt grounding` `Hallucination mitigation` `Gemini API` `Ollama` `RAG` `ChromaDB` `BM25` `RRF fusion`

**ML & Computer Vision**
`PyTorch` `EfficientNet` `Transfer learning` `TTA` `Grad-CAM++` `Active Learning` `MLflow` `OpenCV` `CLAHE` `HSV forensics`

**Backend**
`FastAPI` `Pydantic v2` `PostgreSQL` `Redis` `MongoDB` `SQLAlchemy` `JWT` `Rate limiting` `Structured logging`

**Frontend**
`Next.js 15 (App Router)` `React` `TypeScript` `Tailwind CSS` `TanStack Query` `Framer Motion` `SSE streaming` `WebRTC` `Socket.io`

**DevOps & Cloud**
`Docker Compose` `GitHub Actions` `Jenkins` `Prometheus` `Grafana` `Nginx` `SonarQube` `AWS` `Oracle OCI`

---

## Experience

**AI Engineer — PFE (Graduation Project)** · YEBNI, Tunisia · Feb 2026 – Jul 2026
> Sole architect of DeepCoin-Core. End-to-end ownership across CNN training, LangGraph agent orchestration, hybrid RAG pipeline, 9-page Next.js 15 frontend, JWT/HSTS/CSP security hardening, and CI/CD. Discovered and documented an unreported intra-dataset distribution shift in numismatic ML.

**Full-Stack Engineering Intern** · Tunisia Telecom · Jul 2025 – Aug 2025
> Built Python automation platform for FTTH & 5G operations serving 14M+ subscribers. Netmiko scripting across Cisco/Huawei equipment for ACL, Anti-DDoS, RADIUS, and QoS — 80% reduction in manual configuration time. Delivered Streamlit + Plotly real-time KPI dashboard (latency < 25 ms · throughput > 95 Mbps · availability > 99.5%).

**Full-Stack Intern** · Bright Soft · Jul 2022 – Aug 2022
> React/Node.js SaaS feature development and AI/NLP document processing workflows.

---

## Education & Certifications

**ESPRIT, Tunis** — Engineering Degree, Intelligent Software Engineering (EUR-ACE accredited, BAC+5) · 2023–2026

**ISIK, Le Kef** — BSc Computer Science · 2020–2023

`Anthropic Agent Skills` · `Aviatrix ACE (Multi-Cloud Network)` · `Oracle OCI Associate` · `AWS Cloud Foundations` · `Scrum SFC`

---

## Open to Work

Seeking **AI Engineer** and **Full-Stack AI** roles — Tunisia · France · Remote. Available **July 2026**.

[LinkedIn](https://linkedin.com/in/dhia-shayeb) · [Portfolio](https://dhiashayeb.vercel.app) · [dhiashayeb6@gmail.com](mailto:dhiashayeb6@gmail.com) · [+216 95026309](tel:+21695026309)
