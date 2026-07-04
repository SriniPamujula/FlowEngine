# FlowEngine

Enterprise No-Code Data Pipeline Orchestration Platform — built at Johns Hopkins Medicine as "JHM TaskManager" and adopted as the enterprise-wide pipeline standard. Designed, built, and led by Srinivasa Pamujula.

## Enterprise Impact

| Metric | Value |
|--------|-------|
| Analytical Teams | 10+ |
| End Users | 200+ |
| Jobs Onboarded | 1,500+ in 6 months |
| Resiliency | 99.9999% |
| Data Processed | 2+ billion rows within 2 hours |
| Infrastructure | 4 cores, 16 GB RAM (no additional hardware/software purchase) |
| Cost Model | Generated revenue via departmental chargeback |
| Critical Use | COVID-19 data submissions (federal, state, local agencies) |
| Scalability | Unlimited — only constrained by management's desired scope |

---

## What It Does

FlowEngine is an **all-in-one** autonomous pipeline platform. Users enter minimal details (source, target, schedule) through a web portal. The Engine Agent handles everything else:

```
Read Source → Write Target → Summarize Data → Generate Extracts → Refresh Dashboards → Notify
```

No scripting. No YAML. No DAG files. No additional software purchases.

---

## Architecture

```
┌────────────────────────────────────────────────────────────┐
│ TIER 1: SELF-SERVICE WEB PORTAL                            │
│                                                             │
│ Any authorized user creates a pipeline by entering:         │
│ ├── Source details (DB, file, API, SFTP, cloud)            │
│ ├── Target details (table, file, dashboard)                │
│ ├── Schedule / trigger                                     │
│ ├── Dependencies (parent tasks, cross-pipeline)            │
│ ├── Alerting preferences                                   │
│ └── Parameters (reusable templates)                        │
│                                                             │
│ Stored in: Engine Manifest (versioned, AES-256 encrypted)  │
└──────────────────────────┬─────────────────────────────────┘
                           │
┌──────────────────────────┼─────────────────────────────────┐
│ TIER 2: ENGINE AGENT (Autonomous Orchestrator)              │
│                                                             │
│ Continuously running process that:                          │
│ ├── Reads Engine Manifest for new/updated pipelines         │
│ ├── Resolves dependencies (parent-child + cross-pipeline)  │
│ ├── Analyzes resource requirements (memory, disk, cores)   │
│ ├── Executes tasks in parallel (multi-threaded)            │
│ ├── Handles data transformations                           │
│ ├── Streams large volumes (2B+ rows in 2 hours)           │
│ ├── Self-heals: error detection → smart auto-retry         │
│ ├── Polls for source availability (5-min intervals)        │
│ └── Logs all execution details for audit/compliance        │
│                                                             │
│ Engine: 6,000+ lines of PowerShell libraries               │
│ Runs on: 4 cores, 16 GB RAM (existing infrastructure)      │
└──────────────────────────┬─────────────────────────────────┘
                           │
┌──────────────────────────┼─────────────────────────────────┐
│ TIER 3: MONITORING, ALERTING & REPORTING                    │
│                                                             │
│ Multi-Persona Dashboard:                                    │
│ ├── Executive:  KPIs, SLA compliance, enterprise health    │
│ ├── Manager:    Team pipelines, capacity, chargeback       │
│ ├── Engineer:   Task logs, dependencies, debugging         │
│ └── Analyst:    Job status, schedule, data quality         │
│                                                             │
│ Alerting:                                                   │
│ ├── Per-pipeline configurable (requester's choice)         │
│ ├── Email with tables, graphs, row counts                  │
│ └── Data validation summaries                              │
└────────────────────────────────────────────────────────────┘
```

---

## Supported Sources & Targets

| Category | Systems |
|----------|---------|
| Databases | SQL Server, Oracle |
| Files | Flat files (CSV, TXT, Excel) |
| Cloud | Azure, AWS (S3, Blob) |
| Transfer | SFTP, FTP |
| APIs | REST APIs, Web Services |
| Analytics | Tableau, Power BI |
| Code | Stored procedures, custom scripts, queries |
| Data Science | Python/R scripts, model scoring |

**Load types:** Full loads and incremental loads

---

## Key Capabilities

### 🚀 No-Code Pipeline Creation
- Any authorized user creates pipelines via web form
- Minimal input: source, target, schedule, alert preference
- No scripting, no YAML, no DAG files
- Parameterized templates (same pipeline, different inputs)
- Multi-environment support (dev / test / prod)

### ⚙️ Autonomous Engine Agent
- Continuously running orchestration agent on minimal hardware
- DAG-aware dependency resolution (parent-child + cross-pipeline)
- Resource-aware: analyzes memory, disk space, compute cores
- Multi-threaded parallel execution for maximum throughput
- Streaming for large data volumes (2+ billion rows in 2 hours)
- Built-in data transformations
- 6,000+ lines of PowerShell libraries

### 🔄 Self-Healing & Resilience
- Automatic error detection and classification
- Smart auto-retry with configurable backoff
- Source system monitoring: polls every 5 minutes until available
- All dependent pipelines hold automatically when upstream is down
- 99.9999% resiliency over years of production operation

### 🔐 Security
- Active Directory group-based multi-tenancy (teams isolated)
- Credentials encrypted with AES-256 in the Engine Manifest
- Authorized access only (role-based portal access)
- Full audit trail of all operations

### 📊 Multi-Persona Dashboard

| Persona | Capabilities |
|---------|-------------|
| **Executive** | Enterprise health, SLA metrics, success rates, chargeback revenue |
| **Manager** | Team pipelines, resource utilization, capacity planning, cost allocation |
| **Data Engineer** | Task details, execution logs, dependency graphs, debugging |
| **Analyst** | Job status, scheduling, data validation, completion tracking |

### 📧 Intelligent Alerting
- Per-pipeline configurable (requester's choice)
- Email reports with embedded tables and graphs
- Row count validation summaries
- Data quality checks with visual indicators
- Alerts only when human action is needed

### 📈 Data Validation & Quality
- Automated row count verification
- Source-to-target reconciliation
- Quality check results delivered to specific teams/users
- Graphs and tables showing data accuracy

### 🔁 All-in-One Pipeline Execution
Each pipeline automatically handles the full workflow:
1. **Read** source data
2. **Write** to target
3. **Summarize** target data
4. **Generate** dashboard extracts
5. **Refresh** Tableau/Power BI dashboards
6. **Notify** stakeholders with results

### 💰 Revenue Generation
- Departmental chargeback model
- Usage tracking per team/pipeline
- Generated revenue for the data engineering department

### ⏱️ Pressure-Tested
- Operates under tight processing windows
- Handles time-critical submissions with small notice
- **COVID-19 data submissions** — delivered federal, state, and local agency reporting requirements under extreme time pressure
- Many high-priority, deadline-critical data deliveries

---

## What Makes It Special

| Differentiator | Detail |
|---------------|--------|
| **Zero cost** | No software licenses purchased. PowerShell + existing infrastructure only |
| **Minimal hardware** | 4 cores, 16 GB RAM processes 2B+ rows and 1,500+ jobs |
| **Unlimited scalability** | Architecture scales horizontally — only constraint is organizational scope |
| **Battle-tested** | COVID-19 federal reporting. High-pressure, small-window deliveries |
| **Revenue-generating** | Not a cost center — generates department revenue via chargeback |
| **Version controlled** | Pipeline manifests are versioned for rollback and audit |
| **Multi-environment** | Same pipeline definitions work across dev/test/prod |

---

## Technology Stack

| Component | Technology |
|-----------|-----------|
| Web Portal | ASP.NET Web Forms |
| Engine Agent | PowerShell (6,000+ lines, multi-threaded) |
| Database | SQL Server (manifest, logging, audit) |
| Security | Active Directory + AES-256 encryption |
| Orchestration | Custom DAG engine with dependency resolution |
| Monitoring | Custom multi-persona dashboard |
| Alerting | SMTP with embedded HTML (tables + graphs) |
| Analytics | Tableau, Power BI integration |
| Infrastructure | Windows Server (4 cores, 16 GB RAM) |

---

## Connection to BetterAI Product Suite

FlowEngine demonstrates the same architecture principles across all BetterAI products:

| Principle | FlowEngine | Cost Advisor | Decision Engine | AutoML |
|-----------|-----------|-------------|----------------|--------|
| Autonomous agents | Engine Agent | 5 AI Agents | Trading Bot | Pipeline Runner |
| Self-healing | Auto-retry + source polling | Governance alerts | Order reconciliation | Error handling |
| No-code config | Web form | YAML + DB | Dashboard config | CSV upload |
| Multi-persona dashboards | Exec/Mgr/Eng/Analyst | Executive/FinOps | Positions/Events | Results |
| Enterprise scale | 1,500+ jobs, 2B rows | Multi-workspace | Multi-symbol | Multi-model |
| Security | AES-256 + AD | Unity Catalog | Auth + rate limit | Upload validation |

---

## Status

This repository documents the architecture and capabilities of the platform built at Johns Hopkins Medicine (2014–2024). The source code is proprietary to JHM. This serves as a portfolio piece demonstrating enterprise-scale platform engineering, autonomous system design, and production data infrastructure at scale.

---

## About the Builder

**Srinivasa Pamujula** — Lead Data Engineer at Johns Hopkins Medicine (10 years)

Built FlowEngine from concept to enterprise-wide adoption. Designed, coded, deployed, and operated the system serving 200+ users and 1,500+ production pipelines — including critical COVID-19 federal data submissions — on a single 4-core server with zero software license costs.

🌐 [betterai.guru](https://betterai.guru) | 💼 [LinkedIn](https://www.linkedin.com/in/pamujula)
