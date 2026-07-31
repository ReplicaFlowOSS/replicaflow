# ReplicaFlow Glossary

> ## Purpose
>
> **How does ReplicaFlow speak?**
>
> This document defines the shared vocabulary of ReplicaFlow.
>
> It explains the meaning of the concepts used throughout the project.
>
> Documentation.
>
> Design.
>
> Architecture.
>
> User Interface.
>
> Source Code.
>
> Discussions.
>
> They should all use the same language.
>
> A shared vocabulary creates shared understanding.
>
> Shared understanding creates better software.

---

# Introduction

ReplicaFlow is built around a shared language.

Words shape how people think.

Consistent terminology creates consistent understanding.

This glossary defines the meaning of the concepts used throughout ReplicaFlow.

It is not a technical dictionary.

It is the common language shared by documentation, architecture, design, implementation and the community.

Every concept should have one clear meaning.

Every meaning should have one official definition.

Because shared language creates shared understanding.

And shared understanding creates better software.

---

# Why a Glossary?

As ReplicaFlow grows, so does the number of people contributing to it.

Designers.

Developers.

Writers.

Maintainers.

Community members.

All of them should describe ReplicaFlow using the same concepts.

Without a shared vocabulary, the same idea may be described using different words.

Over time, inconsistent terminology creates inconsistent understanding.

The glossary exists to prevent that.

It provides one shared language for the entire project.

---

# One Concept. One Definition.

Every concept in ReplicaFlow should have exactly one official definition.

Documentation should not redefine concepts.

Architecture should not redefine concepts.

The user interface should not redefine concepts.

Source code should not redefine concepts.

Instead, they should all refer to the same shared vocabulary.

A concept may be explained differently depending on the audience.

Its meaning should never change.

---

# Structure

The glossary is organized by concepts rather than alphabetical order.

Concepts that belong together should be understood together.

The glossary currently contains the following sections:

- Core Concepts
- Information Flow Concepts
- User Experience
- Architecture

Additional sections may be added as ReplicaFlow evolves.

---

# Using the Glossary

When writing documentation, designing interfaces or implementing new features:

- Prefer existing terms over creating new ones.
- Use concepts consistently across the project.
- Avoid synonyms when an official term already exists.
- If a new concept is required, define it here before using it throughout the project.

The glossary should become the canonical vocabulary of ReplicaFlow.

---

# Core Concepts

The following section defines the fundamental concepts upon which ReplicaFlow is built.

Every other concept in the project is based on these foundations.

These concepts should be understood before reading the remaining sections of this glossary.

---

## Understanding

Understanding is the ability to explain how a system works, why it behaves the way it does, and what is likely to happen next.

It is more than knowing individual components.

It is seeing the relationships between them.

ReplicaFlow exists to help people build understanding.

Because understanding enables confident decisions.

---

## Information

Information represents the data, messages, events or knowledge that travel through connected systems.

ReplicaFlow is not limited to a specific type of Information.

A database transaction, an API request, a message, a file, a replication event or a log entry may all represent Information.

ReplicaFlow understands Information by its journey rather than by its format.

Everything that moves through ReplicaFlow is Information.

---

## Information Flow

Information Flow describes the journey of information through connected systems.

It includes where information originates, how it travels, how it is transformed and where it arrives.

ReplicaFlow treats the journey of information as a first-class concept rather than a collection of isolated systems.

Understanding Information Flow means understanding the behavior of the entire system rather than its individual components.

Every visualization in ReplicaFlow exists to make Information Flow understandable.

---

## Control Tower

The Control Tower is the central operational workspace of ReplicaFlow.

It provides a clear overview of Information Flow across connected systems.

Rather than presenting isolated metrics, the Control Tower helps administrators understand relationships, detect changes and make confident decisions.

The Control Tower is not a dashboard.

It is the central place for observing, understanding and operating Information Flow.

Every view in ReplicaFlow should strengthen the administrator's understanding without breaking their mental map.

---

## Workspace

A Workspace is a dedicated environment within the Control Tower where administrators observe, investigate and operate Information Flow.

Each Workspace is designed around a specific task or perspective while remaining part of the same mental model.

Moving between Workspaces should never feel like switching to a different application.

Every Workspace contributes to a consistent understanding of the system.

---

## Information Flow Model

The Information Flow Model is the internal representation of Information Flow within ReplicaFlow.

It provides a common language for providers, the backend, visualizations and future extensions.

Regardless of where information originates, it is translated into the same conceptual model.

This allows different technologies to be understood through one consistent perspective.

---

## Mental Map

A Mental Map is the internal understanding an administrator builds about a system and its Information Flow.

It is formed through observation, experience and consistent visual representation.

ReplicaFlow is designed to strengthen this Mental Map rather than replace it.

Interfaces may evolve.

Technologies may change.

The administrator's Mental Map should remain stable.

A stable Mental Map reduces cognitive load, accelerates problem solving and enables confident decisions.

---

# Information Flow Concepts

The concepts in this section describe the individual elements that make up Information Flow.

Together they form the shared language used to describe the journey of information throughout ReplicaFlow.

---

## Station

A Station is a logical place where Information Flow can arrive, be processed, be transformed or continue its journey.

A Station represents a system, service or component that participates in Information Flow.

Different technologies may represent different kinds of Stations.

Within ReplicaFlow, they are understood through the same conceptual model.

Stations are not defined by their technology, but by their role within Information Flow.

---

## Route

A Route describes the path Information Flow follows between two or more Stations.

Routes define how information travels through a system, regardless of the underlying technology.

A Route may represent replication, messaging, APIs, network communication or any other form of information exchange.

Routes connect Stations into meaningful Information Flow.

Understanding Routes helps administrators understand how information moves throughout a system.

---

## Journey

A Journey is the complete path Information takes while traveling through connected Stations.

A Journey begins at an origin, follows one or more Routes and reaches one or more destinations.

Along its journey, information may be processed, transformed, delayed, replicated or redirected.

A Journey is independent of any specific technology and exists wherever Information Flow can be observed.

ReplicaFlow visualizes Journeys to help administrators understand not only where information is, but how it got there.

Every Journey tells the story of Information Flow.

---

## Event

An Event is a meaningful occurrence during the Journey of Information.

Events describe changes, actions or observations that happen while Information Flow travels through Stations.

An Event may represent processing, replication, delivery, transformation, failure or any other significant moment.

Individual Events explain what happened.

Together they explain the Journey.

---

## State

A State describes the current condition of a Station, Route or Journey at a specific point in time.

Unlike Events, States represent conditions rather than occurrences.

States help administrators understand what is happening now.

Events explain how the current State came to exist.

---

## Delay

A Delay is the difference between the expected and the actual progress of Information Flow.

Delays are not necessarily failures.

They become meaningful when they influence the understanding, timing or reliability of a Journey.

---

## Wait

A Wait describes a period during which Information Flow is intentionally or unintentionally paused before continuing its Journey.

Waiting is not inherently a problem.

Understanding why Information is waiting is often more important than measuring how long it waits.

---

## Lock

A Lock is a condition that temporarily prevents Information Flow from progressing.

Locks may be intentional, required for consistency or caused by contention between multiple Journeys.

ReplicaFlow visualizes Locks to help administrators understand their impact rather than simply report their existence.

---

## Conflict

A Conflict occurs when two or more Journeys cannot progress as intended because their actions or states interfere with each other.

Conflicts may occur within a Station, across multiple Routes or throughout an entire Journey.

Understanding Conflicts helps administrators restore healthy Information Flow.

---

## Incident

An Incident is an unexpected situation that disrupts, degrades or threatens Information Flow.

Incidents are understood through their impact on Journeys rather than through isolated technical symptoms.

ReplicaFlow helps administrators investigate Incidents by making Information Flow visible, understandable and traceable.

Every Incident is an opportunity to build understanding.

---

## Observation

An Observation is the act of collecting or presenting information about a Station, Route or Journey.

Observations provide the evidence required to build Understanding.

Individual Observations become meaningful when they are interpreted within the context of Information Flow.

---

## Operation

An Operation is an intentional action performed by an administrator or ReplicaFlow that influences Information Flow.

Operations may observe, control, modify or restore the behavior of a system.

Every Operation should strengthen understanding rather than reduce it.
