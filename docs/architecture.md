# FlowEngine — Architecture Diagram

## System Overview

```mermaid
graph TB
    subgraph Users["👥 Users (200+)"]
        EXEC[Executive]
        MGR[Manager]
        ENG[Data Engineer]
        ANALYST[Analyst]
    end

    subgraph Portal["🌐 Self-Service Web Portal"]
        FORM[Pipeline Creation Form]
        DASH[Multi-Persona Dashboard]
    end

    subgraph Manifest["📋 Engine Manifest (AES-256 Encrypted)"]
        CONFIG[Pipeline Definitions<br/>Source, Target, Schedule<br/>Dependencies, Parameters]
        VERSIONS[Version History]
    end

    subgraph Agent["⚙️ Engine Agent (Autonomous Orchestrator)"]
        SCHEDULER[Scheduler]
        DAG[DAG Resolver<br/>Parent-Child + Cross-Pipeline]
        RESOURCE[Resource Analyzer<br/>Memory, Disk, Cores]
        EXECUTOR[Multi-Threaded Executor<br/>Parallel Processing]
        HEALER[Self-Healer<br/>Error Analysis + Auto-Retry]
        POLLER[Source Poller<br/>5-min intervals]
        LOGGER[Execution Logger]
    end

    subgraph Sources["📥 Sources"]
        SQL[SQL Server]
        ORA[Oracle]
        FILES[Flat Files]
        API[REST APIs]
        SFTP[SFTP]
        CLOUD[Cloud Storage]
    end

    subgraph Targets["📤 Targets"]
        TGTDB[SQL Server / Oracle]
        TGTFILE[Files / Extracts]
        TAB[Tableau]
        PBI[Power BI]
        SCRIPTS[Custom Scripts]
    end

    subgraph Alerting["📧 Alerting"]
        EMAIL[Email Reports<br/>Tables, Graphs, Row Counts]
        VALID[Data Validation<br/>Quality Checks]
    end

    Users --> Portal
    FORM --> Manifest
    Manifest --> Agent
    SCHEDULER --> DAG
    DAG --> RESOURCE
    RESOURCE --> EXECUTOR
    EXECUTOR --> Sources
    EXECUTOR --> Targets
    EXECUTOR --> HEALER
    HEALER --> POLLER
    LOGGER --> DASH
    LOGGER --> Alerting
    Targets --> VALID
    VALID --> EMAIL
    EMAIL --> Users
```

## Data Flow

```mermaid
flowchart LR
    subgraph Input
        A[User enters:<br/>Source + Target + Schedule]
    end

    subgraph Engine["Engine Agent Processing"]
        B[Read Manifest]
        C[Resolve Dependencies]
        D[Check Resources]
        E[Execute in Parallel]
        F[Transform Data]
        G[Stream to Target]
    end

    subgraph Output
        H[Write Target]
        I[Summarize Data]
        J[Generate Extracts]
        K[Refresh Dashboards]
        L[Send Notifications]
    end

    A --> B --> C --> D --> E --> F --> G --> H --> I --> J --> K --> L
```

## Self-Healing Flow

```mermaid
flowchart TD
    A[Task Execution] --> B{Success?}
    B -->|Yes| C[Log Success<br/>Continue DAG]
    B -->|No| D[Analyze Error]
    D --> E{Source Down?}
    E -->|Yes| F[Hold Dependencies<br/>Poll every 5 min]
    F --> G{Source Up?}
    G -->|Yes| A
    G -->|No| F
    E -->|No| H{Retryable?}
    H -->|Yes| I[Auto-Retry<br/>with backoff]
    I --> A
    H -->|No| J[Generate Root Cause<br/>+ Fix Recommendation]
    J --> K[Alert User]
```

## Security Model

```mermaid
flowchart LR
    subgraph Access
        AD[Active Directory Groups]
        RBAC[Role-Based Access]
    end

    subgraph Encryption
        AES[AES-256 Key]
        CREDS[Encrypted Credentials<br/>in Manifest]
    end

    subgraph Audit
        LOG[All Operations Logged]
        VER[Manifest Versioning]
    end

    AD --> RBAC --> CREDS
    AES --> CREDS
    RBAC --> LOG
    LOG --> VER
```

## Multi-Persona Dashboard

```mermaid
graph LR
    subgraph Dashboard
        E[Executive View<br/>KPIs, SLA, Revenue]
        M[Manager View<br/>Teams, Capacity, Chargeback]
        D[Engineer View<br/>Logs, Dependencies, Debug]
        A[Analyst View<br/>Status, Schedule, Quality]
    end
```

## Infrastructure

```mermaid
graph TB
    subgraph Server["Single Server: 4 Cores, 16 GB RAM"]
        subgraph EngineBlock["Engine Agent - PowerShell"]
            PS[6,000+ lines of code]
            MT[Multi-threaded execution]
            DAGR[DAG resolver]
            RM[Resource manager]
        end

        subgraph DBBlock["SQL Server"]
            MAN[Engine Manifest - versioned]
            LOGS[Execution logs]
            AUD[Audit trail]
        end

        subgraph WebBlock["IIS Web Portal"]
            ASP[ASP.NET Web Forms]
            MPD[Multi-persona dashboard]
        end
    end

    subgraph Results["Results"]
        R1["1,500+ jobs"]
        R2["1.5M+ task runs in 6 months"]
        R3["2B+ rows processed in 2 hours"]
        R4["99.9999% resiliency"]
    end

    Server --> Results
```
