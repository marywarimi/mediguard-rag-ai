# 🩺 MediGuard — RAG-Grounded Clinical Triage Assistant

An AI assistant that tells patients **how urgent** their symptoms are, using verified clinical guidelines instead of guesses. Built with **Google Gemini** and **ChromaDB**.

---

## 🎯 The Problem

Patients with unfamiliar symptoms often search the internet or ask generic chatbots, which can make up dangerous medical advice. At the same time, clinics are overcrowded with low-urgency cases, and quiet emergencies (like silent cardiac symptoms) can be missed.

## 💡 The Solution

MediGuard looks up verified clinical guidelines first, then answers only from them. It **never diagnoses or prescribes**. It labels each case `LOW`, `MEDIUM` or `HIGH` urgency, and red-flag symptoms trigger an immediate emergency message. Every call is logged (time, urgency, latency, cost) so clinics can check it.

## 💰 Business Model (B2B SaaS)

- **Customers:** outpatient clinics, telemedicine platforms, health insurers
- **Product:** a white-label "Digital Front Door" widget
- **Pricing:** monthly clinic fee + small per-triage charge
- **Cost to us:** about ___ USD per query (from `logs/interactions.csv`)
- **Example:** a clinic with ___ patients a day pays ___ and saves ___ nurse hours

---

## 🏗️ How It Works

1. **Knowledge base** (`data/` + ChromaDB): cardiac, respiratory and fever guidelines, chunked and stored for search
2. **Safe prompt** (`src/triage_engine.py`): no diagnosis, no prescriptions, clear emergency rules
3. **Low-temperature Gemini** (`temperature <= 0.2`): steady, consistent answers
4. **Telemetry log** (`logs/interactions.csv`): timestamp, query, urgency, latency, tokens, cost

## 🚀 Local Setup

```bash
git clone https://github.com/YOUR_USERNAME/mediguard-rag-ai.git
cd mediguard-rag-ai
```