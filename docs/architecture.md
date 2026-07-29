# ReplicaFlow Architecture

> ## Purpose
>
> **How is ReplicaFlow built?**
>
> This document defines the conceptual architecture of ReplicaFlow.
>
> It describes the major system components, their responsibilities and the flow of information between them.
>
> The architecture exists to support one central purpose:
>
> **Visualize, explain and administer Information Flow.**

---

# Architecture Philosophy

ReplicaFlow is designed from the user's perspective.

The user does not begin with collectors, APIs or database drivers.

The user begins in the Control Tower.

The technical architecture exists to make the Control Tower possible.

ReplicaFlow therefore follows a simple direction:

```text
Data Sources
      ↓
Data Collection
      ↓
Normalization
      ↓
Interpretation
      ↓
Information Flow Model
      ↓
Control Tower
```

Every architectural component must contribute to understanding or administering Information Flow.

Technology is replaceable.

The mental model is not.

---

# Why Visualization

Modern infrastructures generate enormous amounts of technical information.

ReplicaFlow does not aim to collect more information.

It aims to transform information into understanding.

Visualization is therefore not decoration.

Visualization is the primary interface between complex systems and human understanding.

Every architectural decision ultimately serves this purpose.

---

# The Control Tower

The Control Tower is the central workspace of ReplicaFlow.

It is the place where administrators:

- Observe Information Flow
- Understand system relationships
- Detect delays and interruptions
- Investigate incidents
- Execute administrative operations
- Learn how the underlying systems behave

From the user's perspective, the Control Tower is ReplicaFlow.

All backend components exist to collect, transform and provide the information required by this workspace.

The Control Tower must remain recognizable and stable.

New features may extend the workspace.

They must not destroy the user's mental map.

---

# High-Level Architecture

ReplicaFlow consists of several independent but connected layers.

```text
┌──────────────────────────────────────────────┐
│                Control Tower                 │
│                                              │
│  Visualization · Operations · Explanation   │
└──────────────────────┬───────────────────────┘
                       │
                       │ API and real-time events
                       ▼
┌──────────────────────────────────────────────┐
│             ReplicaFlow Backend              │
│                                              │
│  API · Authentication · Configuration        │
│  Operations · Historical Data                │
└──────────────────────┬───────────────────────┘
                       │
                       ▼
┌──────────────────────────────────────────────┐
│          Information Flow Engine             │
│                                              │
│  Normalization · Correlation · Interpretation│
│  State Detection · Journey Reconstruction    │
└──────────────────────┬───────────────────────┘
                       │
                       ▼
┌──────────────────────────────────────────────┐
│             Collector Framework              │
│                                              │
│     Scheduling · Connections · Queries       │
│     Events · Provider Management             │
└──────────────────────┬───────────────────────┘
                       │
                       ▼
┌──────────────────────────────────────────────┐
│               IDataProvider                  │
│                                              │
│ MariaDB · MySQL · PostgreSQL · Redis · Kafka │
│ RabbitMQ · NATS · Future Technologies        │
└──────────────────────┬───────────────────────┘
                       │
                       ▼
┌──────────────────────────────────────────────┐
│                Data Sources                  │
│                                              │
│ Databases · Replicas · Clusters · Brokers    │
│ Streams · Queues · Distributed Systems       │
└──────────────────────────────────────────────┘
```

---

# Core Components

## 1. Control Tower

The Control Tower is the visual and operational frontend of ReplicaFlow.

Its primary responsibility is to make Information Flow understandable.

It presents:

- Systems and their relationships
- Replication routes
- Transactions
- Queries
- Delays
- Waiting states
- Locks and deadlocks
- Incidents
- Historical journeys
- Administrative operations

The Control Tower uses one consistent interface for all experience levels.

Explorer, Operator and Expert modes do not create separate applications.

They provide different levels of explanation for the same underlying system.

The layout remains stable.

The level of detail changes.

---

## 2. ReplicaFlow Backend

The Backend coordinates the application.

Its responsibilities include:

- Authentication
- Authorization
- User and workspace management
- Configuration
- API communication
- Real-time event delivery
- Historical data access
- Administrative operations
- Audit logging
- Communication with the Information Flow Engine

The Backend should not contain technology-specific database logic.

Technology-specific behavior belongs inside providers.

This keeps the core platform independent from individual database products.

---

## 3. Collector Framework

The Collector Framework retrieves information from connected systems.

ReplicaFlow initially follows a centralized and agentless collection model.

```text
ReplicaFlow Collector
        │
        ├── MariaDB Server
        ├── MySQL Server
        ├── PostgreSQL Server
        ├── Redis Cluster
        ├── Kafka Cluster
        └── Other Data Sources
```

The central collector connects to data sources using their supported network interfaces, protocols and APIs.

Its responsibilities include:

- Connection management
- Secure credential usage
- Collection scheduling
- Event subscription
- Query execution
- Timeout handling
- Retry handling
- Provider lifecycle management
- Collection health monitoring

Centralized collection simplifies installation and administration.

ReplicaFlow should not require software to be installed on every monitored server unless technically necessary.

---

## Optional Remote Collectors

Some environments may not be reachable directly from the central ReplicaFlow instance.

Future versions may support optional remote collectors.

```text
Remote Environment
        │
        ▼
Remote Collector
        │
        ▼
ReplicaFlow Backend
```

Remote collectors may be useful for:

- Isolated networks
- Restricted security zones
- Large distributed environments
- Systems without externally accessible management interfaces
- Local event collection
- Reduced network latency

Remote collectors should remain optional.

ReplicaFlow should prefer centralized, agentless collection whenever possible.

---

## 4. IDataProvider

ReplicaFlow connects to technologies through a common provider contract.

Conceptually, every supported technology implements:

```text
IDataProvider
```

A provider translates technology-specific information into the common language of ReplicaFlow.

Example providers may include:

```text
IDataProvider
    ├── MariaDBProvider
    ├── MySQLProvider
    ├── PostgreSQLProvider
    ├── RedisProvider
    ├── KafkaProvider
    ├── RabbitMQProvider
    ├── NATSProvider
    └── FutureProvider
```

Each provider is responsible for understanding its own technology.

A provider may expose:

- Systems
- Nodes
- Connections
- Replication relationships
- Processes
- Queries
- Transactions
- Locks
- Waiting states
- Events
- Metrics
- Available operations
- Technology-specific details

The ReplicaFlow Core should not require statements such as:

```text
If the database is MariaDB, do this.

If the database is PostgreSQL, do that.
```

Instead, the Core communicates through the provider contract.

This allows new technologies to be added without redesigning the complete application.

---

## 5. Information Flow Engine

The Information Flow Engine transforms collected technical data into understandable Information Flow.

It is the interpretive layer between providers and the Control Tower.

Its responsibilities include:

- Normalizing provider data
- Correlating events
- Detecting relationships
- Reconstructing journeys
- Calculating states
- Detecting delays
- Identifying interruptions
- Recognizing incidents
- Generating explanations
- Preparing visual representations

A provider may report:

```text
Seconds_Behind_Master: 124
```

The Information Flow Engine may interpret this as:

```text
Replication state: Delayed
Delay: 124 seconds
Affected route: Database A → Database B
Severity: Warning
```

The original technical information must remain available.

Interpretation must never replace facts.

ReplicaFlow should preserve both:

```text
Raw Fact
+
Interpreted Meaning
```

This supports Explorer, Operator and Expert modes without creating different sources of truth.

---

# Information Flow Model

The Information Flow Model is the internal language of ReplicaFlow.

Different technologies use different terminology.

ReplicaFlow translates them into shared concepts that can be visualized consistently.

Possible core concepts include:

- Environment
- System
- Station
- Node
- Route
- Source
- Destination
- Journey
- Flow
- Operation
- Query
- Transaction
- Event
- State
- Delay
- Wait
- Lock
- Conflict
- Incident

Technology-specific details remain available through provider extensions.

The common model does not erase technical differences.

It creates a shared foundation for understanding them.

For example:

```text
MariaDB Replication
PostgreSQL Streaming Replication
Kafka Topic Movement
RabbitMQ Message Delivery
NATS Event Distribution
```

may use different mechanisms.

ReplicaFlow can still represent all of them as Information Flow between connected systems.

---

# Normalization

Providers return technology-specific data.

The normalization layer transforms this data into the Information Flow Model.

```text
Technology-Specific Data
          ↓
Provider Translation
          ↓
Normalized Information
          ↓
Information Flow Model
```

Normalization allows the Control Tower to use consistent visual concepts without pretending that all technologies behave identically.

The normalized model contains shared information.

Provider-specific details remain attached to the normalized objects.

This allows experts to inspect the original technical context when required.

---

# Interpretation

ReplicaFlow does not only collect data.

It helps administrators understand what the data means.

Interpretation may include:

- Healthy
- Delayed
- Waiting
- Blocked
- Interrupted
- Disconnected
- Degraded
- Recovering
- Unknown

Interpretation must be:

- Explainable
- Traceable
- Reversible
- Based on observable facts

Every interpreted state should provide access to the evidence that produced it.

For example:

```text
State: Delayed

Reason:
Replication delay has exceeded the configured threshold.

Evidence:
Current delay: 124 seconds
Configured threshold: 60 seconds
```

ReplicaFlow must never hide the underlying technical facts behind simplified labels.

---

# Visualization Flow

The primary output of the architecture is the visualization of Information Flow.

The complete path is:

```text
Data Source
      ↓
IDataProvider
      ↓
Collector
      ↓
Normalizer
      ↓
Information Flow Engine
      ↓
Information Flow Model
      ↓
Backend API
      ↓
Control Tower
      ↓
Human Understanding
```

The final goal is not collection.

The final goal is understanding.

---

# Real-Time Communication

Information Flow changes continuously.

ReplicaFlow should therefore support real-time communication between the Backend and the Control Tower.

Possible information includes:

- State changes
- New queries
- Replication delay changes
- Lock creation
- Lock release
- Transaction progress
- Route interruption
- Recovery events
- Incident updates

The exact communication technology is an implementation decision.

The architecture only requires that live changes can reach the Control Tower without requiring constant manual refreshes.

---

# Historical Information

Not every incident can be understood in real time.

ReplicaFlow should preserve sufficient historical information to reconstruct previous events.

Historical information may support:

- Incident timelines
- Data Journey Replay
- Replication history
- State transitions
- Query history
- Administrative operations
- Audit trails
- Before-and-after comparisons

Retention should be configurable.

ReplicaFlow should avoid collecting unnecessary sensitive data.

Historical storage must balance:

- Diagnostic value
- Performance
- Privacy
- Storage requirements
- Security
- Compliance

---

# Operations

ReplicaFlow is not only an observation platform.

It is also an administrative workspace.

Providers may expose supported operations through a controlled operations interface.

Examples include:

- Start replication
- Stop replication
- Pause processing
- Resume processing
- Terminate a query
- Explain a query
- Inspect execution plans
- Execute approved SQL
- Change selected configuration values

Operations must be treated differently from observations.

Observations read system state.

Operations change system state.

Every operation should support:

- Permission checks
- Clear explanation
- Target identification
- Impact preview
- Explicit confirmation
- Execution result
- Audit logging

Dangerous operations must never be executed silently.

The administrator remains in control.

---

# Security Boundaries

ReplicaFlow may connect to critical production systems.

Security must therefore be part of the architecture from the beginning.

The architecture should support:

- Encrypted communication
- Secure credential storage
- Least-privilege accounts
- Role-based access control
- Read-only provider connections where possible
- Separate permissions for observations and operations
- Audit logging
- Secret rotation
- Environment separation
- Confirmation for destructive actions

Monitoring credentials should not automatically permit administrative operations.

Read access and write access should remain separable.

---

# AI Assistance

Future versions of ReplicaFlow may include AI-assisted interpretation.

The AI may help administrators:

- Explain system states
- Explain replication errors
- Correlate related events
- Suggest diagnostic steps
- Suggest recovery procedures
- Explain execution plans
- Summarize incidents
- Teach while troubleshooting

The AI is not the source of truth.

It operates on facts collected and interpreted by ReplicaFlow.

The architecture should therefore follow this direction:

```text
Observed Facts
      ↓
Information Flow Engine
      ↓
Structured Context
      ↓
AI Assistance
      ↓
Explanation or Suggestion
      ↓
Administrator Decision
```

AI assistance should remain:

- Explainable
- Optional
- Auditable
- Permission-aware
- Clearly distinguishable from verified facts

The AI may suggest.

The administrator decides.

---

# Plugin Architecture

ReplicaFlow should eventually provide an extensible plugin architecture.

Providers are the first major extension point.

Future extension points may include:

- Data providers
- Visualization modules
- Operations
- Incident analyzers
- Export formats
- Notification systems
- Authentication integrations
- AI assistants

The core platform should remain focused.

Extensions should add capabilities without weakening the shared Information Flow Model or the stable Control Tower experience.

Plugins must not redefine the mental map of ReplicaFlow.

---

# Deployment Model

The initial deployment model should remain simple.

```text
ReplicaFlow Instance
    ├── Control Tower
    ├── Backend
    ├── Information Flow Engine
    ├── Collector Framework
    └── Providers
```

This allows ReplicaFlow to operate as one centrally managed application.

Future deployments may separate components for scalability or security.

Examples include:

```text
Control Tower
      │
      ▼
Backend Cluster
      │
      ▼
Collector Nodes
      │
      ▼
Distributed Data Sources
```

Component separation should occur only when required.

ReplicaFlow should not introduce distributed complexity without a clear operational benefit.

---

# Scalability

ReplicaFlow should scale gradually.

The architecture should support:

- Multiple environments
- Multiple providers
- Multiple collectors
- Large numbers of systems
- High-frequency events
- Historical data retention
- Concurrent users
- Workspace Profiles
- Independent visualization modules

Scalability must not make small installations unnecessarily complex.

A single administrator monitoring several databases should be able to run ReplicaFlow without building a distributed platform.

---

# Failure Isolation

A failure in one provider or data source must not stop the complete Control Tower.

Examples:

- One unavailable database should affect only that connection.
- One failing provider should not stop other providers.
- One malformed response should not corrupt the Information Flow Model.
- One visualization failure should not stop collection.
- AI assistance failure should not affect core monitoring.

Components should fail independently wherever possible.

The Control Tower should clearly show when information is:

- Current
- Delayed
- Incomplete
- Unavailable
- Unknown

ReplicaFlow must not present stale information as current information.

---

# Source of Truth

ReplicaFlow may provide several representations of the same situation:

- Raw provider data
- Normalized information
- Interpreted state
- Human explanation
- AI-generated assistance

These representations must remain connected.

The architecture should preserve traceability:

```text
Explanation
      ↓
Interpretation
      ↓
Normalized Information
      ↓
Provider Data
      ↓
Original Data Source
```

An administrator must always be able to move from explanation back to evidence.

---

# Architecture Boundaries

This document defines the conceptual architecture.

It intentionally does not define:

- Programming languages
- Framework versions
- Database schemas
- API endpoints
- Network ports
- Container images
- Deployment scripts
- Class structures
- Exact message formats

Those decisions belong in Architecture Decision Records and implementation documentation.

Architecture defines the system.

ADRs document why specific technologies and implementation strategies were chosen.

---

# Guiding Principles

The ReplicaFlow architecture follows these principles:

## The Control Tower is the center

The architecture exists to support the administrator's workspace.

## Visualization is the core

Information Flow must become visible and understandable.

## Collect centrally when possible

Avoid unnecessary agents and installation complexity.

## Providers isolate technology-specific logic

The core platform communicates through common contracts.

## Facts and interpretation remain connected

Simplification must never hide evidence.

## Operations require control

Explain, preview, confirm and audit.

## AI assists

It does not silently decide.

## Components fail independently

One failure must not hide the rest of the system.

## Start simple

Add distributed complexity only when it provides real value.

## Preserve the mental map

Technical evolution must not force users to relearn ReplicaFlow.

---

# Final Principle

ReplicaFlow is not built around a specific database.

It is not built around a specific framework.

It is not built around a specific deployment model.

ReplicaFlow is built around the visualization and administration of Information Flow.

The architecture may evolve.

The Control Tower must remain understandable.
