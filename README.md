# National Park Assistant

An AI-enabled prototype that helps users ask practical travel questions about U.S. national parks using grounded, citation-based answers from multiple trusted sources.

This project was designed as a proof-of-value analytics and AI application: instead of building a full production travel platform, the goal was to rapidly create a working MVP that demonstrates how retrieval, source prioritization, and a clean user interface can improve decision support for trip planning.

---

## Project Overview

The National Park Assistant is a retrieval-augmented application that answers park-related questions using a combination of:

- **NPS API** for structured park information
- **NPS park pages** for official park-specific details
- **NPS developer documentation** for API understanding and field interpretation
- **Wikivoyage** for supplemental travel context

The assistant prioritizes official National Park Service data for factual answers and uses external travel content only as secondary support. Responses are grounded in retrieved source content and returned with citations and confidence notes.

---

## Business / Analytical Goal

The objective of this project was to build a lightweight, decision-oriented AI prototype that could:

- answer user questions using **grounded source material rather than unsupported generation**
- combine **structured API data** with **unstructured web content**
- demonstrate how AI can support **travel decision-making** through faster information synthesis
- provide a reusable framework for future expansion into a broader recommendation or trip-planning workflow

From a consulting and analytics perspective, this project focused on translating an ambiguous user need—"help me plan a park visit"—into a practical MVP with clear information hierarchy, source traceability, and usable outputs.

---

## My Role

I contributed to the design and implementation of the MVP by helping define the product goal, structure the source-grounding approach, and support the end-to-end workflow from ingestion to user-facing answers. My work focused on:

- shaping the prototype around a **real user question and decision-support use case**
- organizing a **multi-source retrieval design** with source prioritization
- supporting a system architecture that separates **frontend experience**, **backend orchestration**, and **data ingestion**
- contributing to a prototype workflow that emphasizes **citations, transparency, and factual grounding**

---

## Tools & Technologies

- **Python**
- **FastAPI**
- **Next.js / TypeScript**
- **Docker Compose**
- **SQLite / PostgreSQL**
- **REST API workflows**
- **Retrieval-augmented generation (RAG)**
- **Web ingestion and source grounding**

---

## Architecture

The prototype follows a simple, modular architecture designed for rapid development and clear extensibility.

```text
Next.js UI --> FastAPI /ask --> retrieve park + source chunks --> grounded answer + citations
             FastAPI ingestion endpoints --> NPS API / NPS scrape / Docs scrape / Wikivoyage scrape --> SQLite/Postgres
```

This structure supports fast iteration while keeping the system easy to explain, test, and extend.

---

## Key Features

- **Grounded Q&A experience** using multiple park-related sources
- **Source-aware response generation** with citations and confidence notes
- **Official-source prioritization** for factual fields such as fees, hours, and park status
- **Modular ingestion pipeline** for structured and unstructured data
- **Containerized setup** for reproducible local execution

---

## Why This Project Matters

This project is relevant because it demonstrates several capabilities that are valuable in analytics and AI consulting settings:

- turning an ambiguous problem into a **working proof-of-value prototype**
- integrating **APIs, scraped content, and retrieval logic** into a usable workflow
- building an **AI-enabled MVP** quickly without waiting for full production infrastructure
- emphasizing **traceability and trust** through grounded answers and citations
- creating a foundation that could be handed off and expanded into a larger solution

In other words, this project was not just about building a chatbot. It was about designing a practical AI workflow that helps users make better decisions with real source-backed information.

---

## Quickstart

```bash
cd National-Park-Assistant
docker-compose up --build
```

### Manual backend run

```bash
cd backend
python3 -m venv .venv
source .venv/bin/activate
pip install -r requirements.txt
cp .env.example .env
uvicorn app.main:app --reload --port 8000
```

### Manual frontend run

```bash
cd frontend
npm install
cp .env.example .env.local
npm run dev
```

---

## Ingestion Sequence

```bash
curl -X POST http://localhost:8000/ingest/nps-api
curl -X POST http://localhost:8000/ingest/nps-site
curl -X POST http://localhost:8000/ingest/nps-docs
curl -X POST http://localhost:8000/ingest/wikivoyage
```

---

## Example Query

```bash
curl -X POST http://localhost:8000/ask \
  -H "Content-Type: application/json" \
  -d '{"question":"How much does it cost to go to Yellowstone?","park_name":"Yellowstone"}'
```

---

## Notes

- Official NPS API and NPS site data are prioritized for factual answers.
- Wikivoyage is used as a supplemental source for travel context.
- The prototype returns source citations and confidence notes to improve transparency.

---

## Resume-Relevant Summary

This project demonstrates my experience building a rapid AI-enabled MVP using APIs, retrieval workflows, Python-based backend development, and a user-facing interface. It reflects my broader interest in developing practical analytics and AI solutions that are explainable, usable, and decision-oriented.
