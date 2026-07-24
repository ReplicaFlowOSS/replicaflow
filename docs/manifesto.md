# ReplicaFlow Manifesto

**Version 0.1**  
*July 2026*

---

# ReplicaFlow

> **See your data move.**

> *"A database should not require you to think like a database. ReplicaFlow translates database behavior into concepts every human already understands."*  
> — ReplicaFlow Philosophy

---

# Why ReplicaFlow Exists

Modern databases have become incredibly powerful.

They process millions of rows every day.

They replicate data across clusters.

They synchronize data centers.

They keep businesses alive.

Yet when something goes wrong, database administrators still have to open:

- SSH sessions
- SQL consoles
- Monitoring dashboards
- Replication status
- Process lists
- Binlogs
- Log files

...to answer one simple question:

> **Where is my data?**

ReplicaFlow was created to answer exactly that question.

---

# Our Mission

ReplicaFlow does not monitor servers.

ReplicaFlow visualizes **data movement**.

It transforms invisible database activity into understandable visual journeys and allows administrators to understand how information flows through an entire database infrastructure.

---

# Philosophy

Every database is alive.

Every query has a journey.

Every replication has a destination.

Every incident has a story.

ReplicaFlow makes those stories visible.

We believe that understanding creates confidence.

ReplicaFlow does not simplify databases.

ReplicaFlow simplifies understanding.

The underlying data never changes.

Only the way it is presented changes.

---

# We Don't Monitor Servers

We monitor **movement**.

---

# The Railway Principle

ReplicaFlow is inspired by railway traffic control.

A railway operator does not watch rails.

A railway operator watches:

- Trains
- Routes
- Signals
- Switches
- Stations

ReplicaFlow applies exactly the same philosophy to databases.

- Trains represent moving database operations.
- Railway stations represent database servers.
- Railway switches represent replication paths.
- Railway signals represent locks, deadlocks, waiting states and incidents.

The railway is **not** a design choice.

It is a mental model.

People already understand railway traffic.

ReplicaFlow uses this understanding to explain complex database systems.

---

# Our Goal

When an administrator launches an UPDATE query, ReplicaFlow should answer, in real time:

> **Where is it?**

Not:

> Did it finish?

Not:

> Is the server healthy?

But:

> **Where is my data right now?**

---

# Make Databases Visible

A database should become visible.

Not as tables.

Not as rows.

But as **movement**.

---

# We Believe

Data has a journey.

ReplicaFlow helps you see it.

---

# Core Principles

ReplicaFlow should never hide information.

ReplicaFlow should explain.

ReplicaFlow should educate.

ReplicaFlow should make complex database systems understandable.

ReplicaFlow should help junior administrators become senior administrators.

ReplicaFlow should reduce fear during incidents.

ReplicaFlow should inspire curiosity, not fear.

---

# DBA for Humans

Database administration should not require twenty windows.

Database administration should not require memorizing hundreds of SQL commands.

ReplicaFlow should provide answers before administrators even know which SQL query to execute.

ReplicaFlow should teach while people work.

---

# Incident First

ReplicaFlow is built for the worst day.

Not for the best day.

When everything works,

every monitoring system looks good.

ReplicaFlow proves its value

**when everything goes wrong.**

---

# Open Source

ReplicaFlow belongs to the community.

Knowledge should be shared.

Improvements should benefit everyone.

Commercial support is welcome.

Commercial success should never reduce community freedom.

Vendor lock-in is not.

---

# Long-Term Vision

Today:

- MariaDB

Tomorrow:

- MySQL

Later:

- PostgreSQL
- Redis
- Kafka
- RabbitMQ
- NATS

Eventually:

> **Anything that has a journey.**

Because ReplicaFlow is not about databases.

ReplicaFlow is about understanding **information flow.**

---

# The Question

ReplicaFlow should always answer one simple question:

> **Where is my data right now?**

---

# Design Principles

---

## Design Principle #001

# Never move the user's mental map.

People build a spatial understanding of software.

Once they know where something is, they should never have to search for it again.

ReplicaFlow keeps the Control Tower stable.

Only the information shown changes.

The structure does not.

**The user's memory is part of the interface.**

### Why?

During an incident, administrators should think about the problem.

Not about the interface.

A familiar interface reduces stress, speeds up decision making and prevents mistakes.

ReplicaFlow is designed to support the administrator, not distract them.

### Examples

- Database stations always remain in the same position.
- Replication routes never change their layout.
- Incidents always appear at the same location.
- Switching between Explorer, Operator and Expert never changes the layout.

Only the language and the level of detail change.

ReplicaFlow does not redesign the map.

ReplicaFlow reveals more information.

---

## Design Principle #002

# Never surprise the user.

Predictability is more valuable than cleverness.

ReplicaFlow should behave consistently.

The same action should always produce the same result.

The same information should always be found in the same place.

A calm interface creates confident administrators.

---

## Design Principle #003

# Teach. Don't hide.

ReplicaFlow never hides technical details.

Instead, it explains them at the level chosen by the user.

- Explorer explains.
- Operator assists.
- Expert exposes everything.

The software grows together with its users.

---

## Design Principle #004

# Learn one layout. Master your own.

ReplicaFlow has one standard layout.

Every user learns the same interface.

Learning should be universal.

Expertise should be personal.

Expert users may customize their workspace using **Workspace Profiles**.

---

# The Control Tower

> **The Control Tower is home.**

> *No matter how ReplicaFlow evolves, users should always know where they are.*

---

# Our Promise

ReplicaFlow will never become software that users have to fight against.

Technology should adapt to people.

People should not have to adapt to technology.

Every feature we build will be measured against one simple question:

> **Does this help someone understand their data better?**

If the answer is **no**,

it does not belong in ReplicaFlow.

---

# Learning Journey

Learning is not a mode.

It is a journey.

ReplicaFlow grows together with its users.

```
Explorer
    │
    ▼
Learn database concepts.
    │
    ▼
Operator
Operate production systems confidently.
    │
    ▼
Expert
Access every technical detail without limitations.
```

The software evolves together with the administrator.

---

# Closing Statement

ReplicaFlow is not built to replace database administrators.

**ReplicaFlow is built to help them become better ones.**
