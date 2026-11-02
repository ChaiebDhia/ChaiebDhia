<div align="center">

# Dhia Chaieb

**AI / ML Engineer · Applied AI · Computer Vision · MLOps · LLM systems**

I build AI systems end to end: data, model, retrieval, API, interface, monitoring.
Based in Tunis. **Open to new opportunities. Ready to relocate (visa sponsorship needed): UK · EU · Gulf · Singapore · Japan.**

[![LinkedIn](https://img.shields.io/badge/LinkedIn-dhia--shayeb-0A66C2?style=for-the-badge&logo=linkedin&logoColor=white)](https://www.linkedin.com/in/dhia-shayeb/)
[![Email](https://img.shields.io/badge/Email-dhiashayeb6%40gmail.com-EA4335?style=for-the-badge&logo=gmail&logoColor=white)](mailto:dhiashayeb6@gmail.com)
[![Flagship](https://img.shields.io/badge/Flagship-DeepCoin--Core-1e40af?style=for-the-badge&logo=github&logoColor=white)](https://github.com/ChaiebDhia/DeepCoin-Core)

</div>

---

## Flagship: [DeepCoin-Core](https://github.com/ChaiebDhia/DeepCoin-Core)

> One coin photo in. A sourced, explainable report out. About 20 seconds, on local models.

My ESPRIT graduation project, built at YEBNI (Feb to Aug 2026). It identifies ancient coins, shows where the model looked, and writes a report that is grounded in a knowledge base instead of the LLM's memory.

| | |
|---|---|
| **Vision** | EfficientNet-B3 (PyTorch), 438 classes, **79.60%** top-1 with 5-view TTA on a 1,152-image held-out set (79.25% single pass) |
| **Explainability** | Grad-CAM++ heatmaps (19 x 19) in every PDF report and in the web UI |
| **Agents** | 5 LangGraph agents; the CNN's confidence decides the route (RAG report, metal validation, or nearest-known-types search) |
| **Retrieval** | Hybrid BM25 + ChromaDB with Reciprocal Rank Fusion over 47,705 vectors (9,541 coin types), under 1 ms |
| **Product** | FastAPI, Next.js 15, PostgreSQL, Redis, JWT, rate limiting, active-learning loop |
| **MLOps** | MLflow, Docker Compose (11 services), GitHub Actions CI/CD, Prometheus / Alertmanager / Grafana, 133 tests |
| **Runs locally** | Ollama (gemma3:4b, qwen3-vl:4b) on a 4 GB GPU; paid APIs are optional |

**I audit my own numbers.** In October 2026 I re-ran the evaluation, found that the original headline (80.03%) did not reproduce, and published the corrections at the top of the [README](https://github.com/ChaiebDhia/DeepCoin-Core#corrections-oct-2026). Known gaps are listed there too: no load test, no third-party security audit, RAG faithfulness not yet benchmarked.

---

## What I bring to applied and forward-deployed AI roles

- **Ship the whole thing.** Model, retrieval, API, UI, monitoring and deployment in one repo, built solo.
- **Make LLM output checkable.** Retrieval with citations, structured fields copied from a knowledge base, a graceful fallback chain so the system never returns an empty answer.
- **Work inside real constraints.** 4 GB of VRAM, small and imbalanced data (about 17 images per class on average, 40:1 imbalance), local-first models.
- **Say what is not measured.** Honest evaluation and clear limits, in writing.
- **Work across languages and cultures.** Arabic, French, English.

---

## Other projects

| Project | What it does | Stack |
|---|---|---|
| [Overlord Pipeline](https://github.com/ChaiebDhia/overlord-ai-video-pipeline) | 5-stage multi-LLM video generation pipeline with word-level timestamps | TypeScript · Node.js · OpenAI · Whisper · FFmpeg |
| [SkillBridge](https://github.com/InnovativeSquad-PI-4TWIN4/PiWebInovativeSquad) | AI-augmented skill-exchange platform, team of 5 | React · Node.js · MongoDB · WebRTC · Socket.io · Gemini API |
| [DevOps Pipeline](https://github.com/ChaiebDhia/DevOps_SpringBoot) | 18-stage Jenkins CI/CD with quality gates | Jenkins · Docker · SonarQube · Prometheus · Grafana |

---

## Stack

**ML / CV:** PyTorch · EfficientNet · Grad-CAM++ · OpenCV · Albumentations · MLflow
**LLM / RAG:** LangGraph · hybrid retrieval (BM25 + vectors + RRF) · ChromaDB · sentence-transformers · Ollama · Gemini
**Backend / Frontend:** Python · FastAPI · PostgreSQL · Redis · TypeScript · Next.js 15
**Platform:** Docker Compose · GitHub Actions · Jenkins · Prometheus · Grafana · AWS (OCI and AWS certified)

---

## Experience

**AI / ML Engineer** · YEBNI, Tunisia · Feb 2026 to Aug 2026
Sole architect of DeepCoin-Core, from CNN training to monitored deployment.

**Full-Stack Engineering Intern** · Tunisia Telecom · Jun 2025 to Aug 2025
Python network-automation tooling (Netmiko, Cisco and Huawei devices) and a real-time KPI dashboard.

**Full-Stack Intern** · Bright Soft · Jul 2022 to Aug 2022
React and Node.js features, NLP document processing.

## Education and certifications

**ESPRIT, Tunis** · Engineering degree, Intelligent Software Engineering (EUR-ACE, BAC+5) · 2023 to 2026
**ISIK, Le Kef** · BSc Computer Science, Software Engineering · 2020 to 2023
Anthropic Agent Skills · Oracle OCI Associate · Aviatrix ACE Multi-Cloud · AWS Academy Cloud Foundations

---

<div align="center">

### Hiring for AI, ML or computer vision? [Message me on LinkedIn](https://www.linkedin.com/in/dhia-shayeb/) or write to dhiashayeb6@gmail.com.

</div>
