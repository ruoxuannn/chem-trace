# ChemTrace — AI Synthesis Intelligence Platform

> 🥇 **1st Place — Encode Club AI London Hackathon 2026**

ChemTrace is a multi-agent AI platform that automates the retrosynthetic analysis and procurement scouting workflow for medicinal chemists. It reduces "Search-to-Bench" latency — the time from molecular design to lab experiment — from days to minutes.

---

## The Problem

Medicinal chemists spend hours manually searching for synthesis routes, comparing supplier prices across geographies, and checking regulatory constraints for each jurisdiction. This process is fragmented across multiple databases and tools with no unified workflow.

## What ChemTrace Does

ChemTrace decomposes this complex decision problem into four specialised AI agents that work in concert:

| Agent | Role |
|-------|------|
| **Architect** | Analyses the target molecule and generates viable synthesis routes, scoring each by yield, cost, and complexity |
| **Librarian** | Queries PubChem PUG REST API for real-time molecular data, reaction precedents, and safety profiles |
| **Procurement** | Aggregates live supplier pricing across geographies using Frankfurter (currency conversion) and REST Countries APIs |
| **Risk** | Screens each route against jurisdiction-specific regulatory frameworks, flagging controlled precursors and restricted reagents |

## Architecture

User Input (target molecule)
│
▼
┌─────────────┐
│  Architect   │ ← Generates synthesis routes
│   Agent      │
└──────┬──────┘
│
┌─────┴─────┐
▼           ▼
┌────────┐ ┌────────────┐
│Librarian│ │Procurement │ ← Parallel data enrichment
│ Agent  │ │   Agent    │
└───┬────┘ └─────┬──────┘
│            │
└─────┬──────┘
▼
┌─────────────┐
│    Risk      │ ← Regulatory screening
│   Agent      │
└──────┬──────┘
│
▼
Ranked Route Recommendations
(yield × cost × risk score)

## Tech Stack

- **Language:** Python
- **LLM:** Anthropic Claude API (claude-sonnet-4-6)
- **External APIs:** PubChem PUG REST (molecular data), REST Countries (geographic data), Frankfurter (FX rates)
- **Architecture:** Multi-agent orchestration with defined inter-agent communication protocol

## My Contribution

I built the **backend and AI layer** of this project:
- Designed the multi-agent architecture and inter-agent communication logic
- Implemented the decision engine that scores and ranks synthesis routes across yield, cost, and supply risk
- Integrated all three external APIs (PubChem, REST Countries, Frankfurter) for real-time data ingestion
- Built the regulatory screening pipeline for jurisdiction-based compliance checks

## Team

Built in 24 hours with [Emilia Staffiero](https://github.com/renee-stack) and teammates at Encode Club AI London 2026.

## Run

```bash
# Clone
git clone https://github.com/ruoxuannn/chem-trace.git
cd chem-trace

# Install dependencies
pip install -r requirements.txt

# Set up environment
cp .env.example .env
# Add your ANTHROPIC_API_KEY to .env

# Run
python main_cli.py
```

## Acknowledgements

Built at [Encode Club AI London Hackathon 2026](https://www.encode.club/).
