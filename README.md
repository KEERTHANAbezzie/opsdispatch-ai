# ⚡ OpsDispatch AI
> **Autonomous Incident Clustering & Shift-State Synthesis Engine for Enterprise IT Operations**

[![Streamlit App](https://static.streamlit.io/badges/streamlit_badge_black_white.svg)](https://gauzzxzcpjandzzi23rytp.streamlit.app)
![License](https://img.shields.io/badge/License-MIT-blue.svg)
![Python](https://img.shields.io/badge/Python-3.10%2B-blue)
![Track](https://img.shields.io/badge/Track-Enterprise%20AI-green)

---

## 📌 Executive Summary
Enterprise IT and SRE teams drown in 100+ unstructured emails, vendor status advisories, and customer tickets every shift. A single production incident (e.g., an RDS connection pool exhaustion) routinely generates dozens of disjointed messages across different communication channels.

* **PagerDuty** handles machine metrics, but misses unstructured human and vendor communication.
* **ServiceNow & Jira** are passive record systems that suffer from ticket duplication and sprawl.
* **Glean** is a passive search bar, rather than an active orchestration engine.

**OpsDispatch AI** serves as the **Upstream Pre-ITSM Middleware Layer**. It ingests high-entropy communication streams, drops non-operational noise, clusters disparate messages describing the same root issue into a single actionable incident, maps contextual runbooks, and dynamically synthesizes the next shift's handover briefing.

---

## 🏗️ Architecture & Data Flow

```text
       [ LAYER 1: Raw Enterprise Event Sources ]
   • CloudWatch / Datadog (Machine Alerts)
   • Shared Inboxes: ops-team@company.internal
   • Vendor Notifications (Stripe, AWS, Adyen)
   • Customer Escalation Portals (VIP Support)
                        │
                        ▼
┌───────────────────────────────────────────────────────────┐
│ LAYER 2: OpsDispatch AI Middleware Engine                 │
│                                                           │
│  1. Ingestion & Noise Gate                                │
│     └── Filters non-ops chatter (HR surveys, lunch forms) │
│                                                           │
│  2. Cross-Boundary Semantic Synthesis                     │
│     └── Groups multi-sender messages without shared keys  │
│         (4 separate emails ──► 1 Unified Incident)        │
│                                                           │
│  3. SLA Calculation & Runbook Binding                     │
│     └── Extracts urgency reason & maps 3-step SOP         │
│                                                           │
│  4. Shift-State Synthesis Engine                          │
│     └── Reconstructs state changes for incoming team      │
└───────────────────────────┬───────────────────────────────┘
                            │
            ┌───────────────┴───────────────┐
            ▼                               ▼
 [ Downstream Alerting ]        [ System of Record ]
    • PagerDuty Webhook            • ServiceNow / Jira Table API
      (Escalate P1 breaches)         (Single deduplicated ticket)
