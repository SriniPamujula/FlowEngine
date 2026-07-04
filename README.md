# FlowEngine

Enterprise No-Code Data Pipeline Orchestration Platform — originally built at Johns Hopkins Medicine as "JHM TaskManager" and adopted as the enterprise-wide pipeline standard.

🌐 **Showcase:** [betterai.guru/flow-engine](https://betterai.guru/flow-engine) (coming soon)

## Impact

| Metric | Value |
|--------|-------|
| Analytical Teams | 10+ |
| End Users | 200+ |
| Jobs Onboarded | 1,500+ in 6 months |
| Resiliency | 99.9999% |
| Adoption | Enterprise standard at Johns Hopkins Medicine |

## What It Does

FlowEngine enables authorized users to create, schedule, and monitor data pipelines through a simple web interface — **without writing code**. The platform handles orchestration, dependency management, resource allocation, parallel execution, self-healing, and executive reporting autonomously.

## Architecture

```
┌─────────────────────────────────────────────────────────┐
│ TIER 1: SELF-SERVICE WEB PORTAL                         │
│                                                          │
│ Authorized users enter:                                  │
│ ├── Source details (database, file, API)                 │
│ ├── Target details (destination table/file)              │
│ ├── Schedule (cron, event-trigger, dependency)           │
│ └── Alerting preferences                                 │
│                                                          │
│ Stored in: Engine Manifest Table                         │
└─────────────────────┬───────────────────────────────────┘
                      │
┌─────────────────────┼───────────────────────────────────┐
│ TIER 2: ENGINE AGENT (Autonomous Orchestrator)           │
│                                                          │
│ Continuously running server process that:                │
│ ├── Reads Engine Manifest for new/updated pipelines      │
│ ├── Resolves task dependencies (DAG)                     │
│ ├── Analyzes resource requirements (memory, disk, cores) │
│ ├── Executes tasks in parallel (multi-threaded)          │
│ ├── Self-heals: detects errors → auto-retry              │
│ └── Logs execution details for reporting/debugging       │
│                                                          │
│ Powered by: 6,000+ lines of PowerShell libraries        │
└─────────────────────┬───────────────────────────────────┘
                      │
┌─────────────────────┼───────────────────────────────────┐
│ TIER 3: MONITORING & ALERTING                            │
│                                                          │
│ Dashboard:                                               │
│ ├── Executive view (KPIs, success rates, SLA)            │
│ ├── Manager view (team pipelines, resource usage)        │
│ ├── Engineer view (task details, logs, debugging)        │
│ └── Analyst view (job status, schedule, dependencies)    │
│                                                          │
│ Alerting:                                                │
│ ├── Configurable per pipeline (requester's choice)       │
│ ├── Email with tables + graphs                           │
│ └── Processing accuracy summaries                        │
└─────────────────────────────────────────────────────────┘
```

## Key Features

### 🚀 No-Code Pipeline Creation
- Authorized users create pipelines via web form
- Only requires: source, target, schedule, alert preferences
- No scripting, no YAML, no DAG files — enter details and go

### ⚙️ Autonomous Engine Agent
- Continuously running orchestration agent
- Dependency resolution (DAG-aware execution order)
- Resource-aware: analyzes memory, disk space, compute cores before execution
- Multi-threaded parallel execution for maximum throughput
- 6,000+ lines of PowerShell libraries powering the engine

### 🔄 Self-Healing
- Automatic error detection and classification
- Smart auto-retry with backoff
- Error pattern recognition
- Alerts only when human intervention is truly needed

### 📊 Multi-Persona Dashboard
| Persona | What they see |
|---------|--------------|
| Executive | KPIs, success rates, SLA compliance, enterprise health |
| Manager | Team pipelines, resource utilization, capacity planning |
| Data Engineer | Task details, execution logs, debugging, dependencies |
| Analyst | Job status, schedule, completion tracking |

### 📧 Intelligent Alerting
- Per-pipeline alerting configuration (requester's choice)
- Email reports with embedded tables and graphs
- Daily processing accuracy summaries
- Only alerts when action is needed (reduces noise)

### 📈 Enterprise Metrics
- 1,500+ jobs onboarded in 6 months
- 200+ active end users across 10+ teams
- 99.9999% resiliency (near-zero downtime)
- Adopted as the enterprise-wide standard at Johns Hopkins Medicine

## Technology Stack

| Component | Technology |
|-----------|-----------|
| Web Portal | ASP.NET / Web Forms |
| Engine Agent | PowerShell (6,000+ lines) |
| Database | SQL Server |
| Orchestration | Custom DAG engine with multi-threading |
| Monitoring | Custom dashboard (multi-persona) |
| Alerting | SMTP with embedded HTML reports |
| Deployment | Windows Server |

## How BetterAI Relates

FlowEngine demonstrates the same architecture principles used across all BetterAI products:

| Principle | FlowEngine | Cost Advisor | Decision Engine |
|-----------|-----------|-------------|----------------|
| Autonomous agents | Engine Agent | AI Agents | Trading Bot |
| Self-healing | Auto-retry | Governance alerts | Order reconciliation |
| No-code config | Web form | YAML + DB | Dashboard config |
| Multi-persona dashboards | Exec/Manager/Engineer | Executive/FinOps | Positions/Events |
| Enterprise scale | 1,500+ jobs | Multi-workspace | Multi-symbol |

## Status

This project documents the architecture and capabilities of the platform built at Johns Hopkins Medicine (2014–2024). The code is proprietary to JHM, but the design principles and architecture are showcased here as a portfolio piece demonstrating enterprise-scale platform engineering.

## License

Architecture documentation — © 2025 Srinivasa Pamujula / BetterAI LLC
