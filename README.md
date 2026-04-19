# AI Supply Chain Orchestrator

A production-grade, multi-agent artificial intelligence system designed for supply chain and inventory management within chemical manufacturing. This system leverages Azure and Microsoft Power Platform to coordinate specialized AI agents, ensuring that regulatory compliance and human safety are prioritized over cost optimization.

## 🏗️ Architecture Overview

The system operates via a **Central Orchestrator Agent** that triages incoming events (IoT data, emails, ERP logs) and dispatches tasks to specialized sub-agents. 

### Core Agents
* **Orchestrator Agent**: The central "brain" managing state, prioritizing actions, and resolving goal conflicts.
* **Inventory Agent**: Monitors real-time stock levels and recalculates reorder points.
* **Forecasting Agent**: Predicts demand spikes looking at historical data and seasonal trends.
* **Supplier Comm Agent**: Connects via Outlook Graph API to parse incoming supplier emails, quotes, and SDS (Safety Data Sheets).
* **Compliance Agent**: Enforces REACH, OSHA, and chemical compatibility constraints. 
* **Decision Agent**: Analyzes trade-offs (Cost vs. Speed vs. Safety) using Azure OpenAI GPT-4o.
* **Workflow Agent**: Executes Power Automate flows, bridging the AI decisions with backend ERP/Dataverse systems.

## 📖 Documentation
Detailed design documentation can be found in the docs folder:
- [Dataverse Schema](docs/dataverse_schema.md): Entity definitions and relationships.
- [Orchestrator Scenarios](docs/orchestrator_scenarios.md): Conflict resolution logic and simulated test cases.

## ⚙️ Technology Stack
* **Cloud Platform**: Azure (Event Hub, Azure ML, Cognitive Services)
* **Automation**: Microsoft Power Automate
* **System of Record**: Microsoft Dataverse
* **Reasoning Engine**: Azure OpenAI (GPT-4o)
* **Business Intelligence**: Power BI

## 🚀 Setup & Phasing
This project is currently moving through a structured 10-phase roadmap:
1. Environment Setup (Azure + Dataverse)
2. Dataverse Schema Design
3. Data Ingestion (Email + IoT Simulation)
4. Central Orchestrator Implementation
5. Agent Development
6. Event-Driven Workflows
7. Copilot Studio Integration
8. Power BI Dashboards
9. End-to-End Testing
10. Deployment

---
*Designed with a "Safety-First" architecture for harsh industrial/chemical environments.*
