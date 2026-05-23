# Dhia Shayeb — AI Engineer

**Agentic AI · Hybrid RAG · Full-Stack · MLOps**

I build AI systems that ship to production. Currently finishing my engineering degree at ESPRIT (Jul 2026) while delivering **DeepCoin-Core** at YEBNI — a complete AI platform built solo, from model training to production hardening.

---

## What I'm building right now

### [DeepCoin-Core](https://github.com/ChaiebDhia/DeepCoin-Core) — Agentic AI + RAG + Computer Vision

An end-to-end platform that classifies 2,300-year-old coins from a single photograph in under 20 seconds.

| Metric | Result |
|--------|--------|
| CNN accuracy (EfficientNet-B3, TTA x8, 438 classes) | **80.03%** |
| Knowledge base coverage | **9,541 types — 47,705 vectors** |
| Hallucination on structured facts | **Zero** (citation-block grounding) |
| Test suite | **122 / 122 passing** |
| Services in Docker stack | **7** (FastAPI, Next.js 15, PostgreSQL, Redis, Nginx, MLflow, LocalStack) |
| End-to-end pipeline latency | **< 20 s** |

**How the system works:**

A single coin photograph goes in. A 5-agent LangGraph state machine routes by CNN confidence:
- **> 85%** — Historian agent: hybrid RAG (BM25 + ChromaDB + RRF) generates a grounded historical report
- **40–85%** — Validator agent: multi-scale HSV metal detection + KB consensus override
- **< 40%** — Investigator agent: VLM + OpenCV finds the 3 closest cultural matches from 9,541 types

The system never returns an empty report. Graceful degradation over silent failure, every time.

**One research finding from this build:** The same trained model scored 80% on standard composite photographs but dropped to 15–28% on BNF 1966 catalog scans of identical coin types. Same model, same classes, different photographic era — an intra-dataset distribution shift not previously documented in numismatic ML literature.

```
Stack: PyTorch · LangGraph · FastAPI · Next.js 15 · ChromaDB · PostgreSQL
       Redis · MLflow · Docker · Prometheus · Grafana · GitHub Actions
```

---

## All projects

| Project | What it does | Key result |
|---------|-------------|------------|
| [DeepCoin-Core](https://github.com/ChaiebDhia/DeepCoin-Core) | Agentic AI + RAG + CV for archaeological coin classification | 80.03% accuracy, 47k vectors, 122 tests |
| [DevOps_SpringBoot](https://github.com/ChaiebDhia/DevOps_SpringBoot) | 18-stage Jenkins CI/CD pipeline | 99.98% deployment success, <2 min runtime |
| [Microservices](https://github.com/ChaiebDhia/Microservices) | Spring Cloud travel platform | 6 services, Eureka discovery, API gateway |
| [SkillBridge](https://github.com/InnovativeSquad-PI-4TWIN4/PiWebInovativeSquad) | AI-powered MERN skill exchange platform (team of 5) | Gemini AI, WebRTC, Socket.io, real-time P2P |

---

## Stack

**AI & LLMs**
`LangGraph` `PyTorch` `EfficientNet` `ChromaDB` `BM25` `RRF` `MLflow` `Gemini API` `Ollama` `OpenCV` `Grad-CAM++`

**Backend**
`FastAPI` `Pydantic v2` `PostgreSQL` `Redis` `MongoDB` `JWT` `SQLAlchemy`

**Frontend**
`Next.js 15` `React` `TypeScript` `Tailwind CSS` `Node.js` `Socket.io` `WebRTC`

**DevOps & Cloud**
`Docker Compose` `GitHub Actions` `Jenkins` `Prometheus` `Grafana` `Nginx` `SonarQube` `AWS` `Oracle OCI`

---

## Experience

**AI Engineer — PFE (Graduation Project)** | YEBNI, Tunisia | Feb 2026 – Jul 2026
> Sole architect of DeepCoin-Core. End-to-end ownership: model training, agent orchestration, RAG pipeline, full-stack delivery, security hardening, CI/CD.

**Full-Stack Engineering Intern** | Tunisia Telecom | Jun 2025 – Aug 2025
> Python automation for FTTH/5G infrastructure (14M+ subscribers). Netmiko scripting across Cisco/Huawei equipment — 80% reduction in manual configuration time. Streamlit + Plotly KPI dashboard.

**Full-Stack Intern** | Bright Soft | Jul 2022 – Aug 2022
> React/Node.js SaaS features, AI/NLP document processing workflows.

---

## Education & Certifications

**ESPRIT, Tunis** — Engineering Degree, Intelligent Software Engineering (EUR-ACE accredited, BAC+5) | 2023–2026

**ISIK, Le Kef** — BSc Computer Science | 2020–2023

Certifications: `Anthropic Agent Skills` `Aviatrix ACE` `Oracle OCI Associate` `AWS Cloud Foundations` `Scrum SFC`

---

## Open to work

Looking for **AI Engineer** and **Full-Stack AI** roles in Tunisia, France, or remotely — available July 2026.

**Contact:**
[LinkedIn](https://linkedin.com/in/dhia-shayeb) · [Portfolio](https://dhiashayeb.vercel.app) · dhiashayeb6@gmail.com
