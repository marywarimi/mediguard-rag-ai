# mediguard-rag-ai
RAG-grounded AI medical symptom triage assistant with safety guardrails and telemetry logging.
#  AI — RAG-Grounded Clinical Triage Assistant

An AI-powered medical symptom triage assistant built with **Google Gemini** and **ChromaDB**[cite: 1]. Instead of relying on ungrounded LLM generation, it retrieves verified clinical guidelines and applies strict safety guardrails to classify symptom urgency (`LOW`, `MEDIUM`, `HIGH`) and guide patients toward appropriate care[cite: 1].

---

## 🎯 The Problem & Solution

* **The Problem:** Patients experiencing unfamiliar symptoms often rely on unverified internet searches or generic AI chatbots that can hallucinate dangerous medical advice[cite: 1]. Meanwhile, clinics and emergency departments face overcrowding from low-urgency cases while atypical emergencies (such as silent cardiac symptoms) risk being overlooked[cite: 1].
* **The Solution:** A Retrieval-Augmented Generation (RAG) triage layer that grounds every response strictly in verified clinical protocols[cite: 1]. The system **never diagnoses or prescribes**; it assesses symptom urgency in plain language, triggers immediate emergency escalation for red-flag symptoms, and logs telemetry (latency, urgency, and API cost per call) for clinical oversight[cite: 1].
* **Business & Revenue Model (B2B SaaS):** Licensed to outpatient clinics, telemedicine platforms, and health insurers as a white-label "Digital Front Door" widget—reducing nurse triage bottlenecks while operating at fractions of a cent per patient query[cite: 1].

---

## 🏗️ System Architecture

1. **Knowledge Base (`data/` & ChromaDB):** Verified clinical guidelines (Cardiac, Respiratory, Fever) chunked with overlap and embedded into a local vector store for semantic retrieval[cite: 1].
2. **Hardened System Prompt (`src/triage_engine.py`):** Enforces top-priority negative constraints (no diagnosis, no prescriptions) and explicit emergency escalation rules[cite: 1].
3. **Low-Temperature Generation (`gemini-2.0-flash`):** Configured at `temperature <= 0.2` for deterministic, consistent clinical guidance[cite: 1].
4. **Telemetry & Cost Logger (`logs/interactions.csv`):** Tracks timestamp, query, extracted urgency level, latency, token count, and estimated USD cost per interaction[cite: 1].

---

## 🗺️ Build Roadmap

- [x] **Phase 1: Repository & Environment Setup**
  - Initialize GitHub repository, folder architecture, and `.gitignore` security rules.
- [ ] **Phase 2: Core RAG & Guardrail Engine (`notebooks/01_rag_triage_prototype.ipynb`)**
  - Configure Gemini API at low temperature (`0.2`)[cite: 1].
  - Implement document chunking and ChromaDB vector storage for clinical guidelines[cite: 1].
  - Build the retrieval-to-prompt context injection pipeline (`ask_with_rag`)[cite: 1].
- [ ] **Phase 3: Red-Teaming & Automated Evaluation**
  - Test adversarial edge cases (atypical cardiac symptoms, prompt injections, out-of-scope queries)[cite: 1].
  - Run LLM-as-a-judge evaluation across Safety, Relevance, Groundedness, and Clarity[cite: 1].
- [ ] **Phase 4: Telemetry & Production Refactor (`src/triage_engine.py`)**
  - Integrate automated CSV logging for latency, urgency accuracy, and token cost projections[cite: 1].
  - Refactor notebook functions into a clean, modular Python backend.
- [ ] **Phase 5: Live Demo Interface (`app.py`)**
  - Build a clean frontend UI displaying live symptom triage, urgency badges, retrieved guideline sources, and real-time API cost metrics[cite: 1].

---

## 🚀 Local Setup

1. **Clone the repository:**
   ```bash
   git clone [https://github.com/YOUR_USERNAME/afya-triage-ai.git](https://github.com/YOUR_USERNAME/afya-triage-ai.git)
   cd afya-triage-ai