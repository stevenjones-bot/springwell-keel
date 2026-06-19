# ADR-001: Three-Lane Architecture

**Status:** Proposed — open for challenge and revision
**Date:** June 19, 2026
**Author:** Steven Earl Jones, Founder — LHB Social Enterprise

---

## Context

Springwell-Keel is being designed to solve a specific problem in faith-based and benevolence ministry organizations: people arrive in crisis, receive a one-time response, and disappear. No follow-up. No root cause detection. No routing to the underlying need. We call this band-aid churn.

The system needs to handle three fundamentally different types of work simultaneously:
1. Tracking and following up with **individuals** on their personal journey
2. Managing the **organization's service catalog** — what care options exist and when they're available
3. Sequencing when someone is **ready to hand off** from one care lane to another

These felt like distinct enough concerns that collapsing them into a single agent or workflow would create brittle, hard-to-debug logic.

---

## Decision

We are proposing three coordinated orchestration lanes as a design direction:

**Lane A — Individual Journey Orchestration**
Handles intake, sensing, and sequenced follow-up for individuals. Owns the "drip campaign" metaphor — automated, human-feeling contact that detects sentiment and escalates when needed.

**Lane B — Organizational Service Catalog**
Manages what services a church or benevolence org has available, at what capacity, and during which seasons. Acts as the matching layer between a person's detected need and available resources.

**Lane C — Capability Sequencing & Readiness Handoff**
Determines when someone is ready to move from one care lane to another — e.g., from crisis food assistance to sobriety coaching to financial counseling. Owns the transition logic.

---

## Why Three Lanes and Not One

A single monolithic workflow could theoretically handle all of this. We rejected that approach because:

- Individual journey state changes frequently and unpredictably
- Org service availability changes seasonally and organizationally
- Readiness/handoff logic requires a different kind of reasoning than either of the above

Separating concerns makes each lane testable, replaceable, and volunteer-accessible independently.

---

## What We Are NOT Deciding Here

- Whether these lanes are separate microservices, separate agents, or separate workflow branches within a single process — that is a deliberate open question for contributors
- The specific technology implementation of any lane
- Whether three is the right number — if a contributor can make the case for two or four, that conversation is welcome

---

## Open Questions (Seeking Contributor Input)

1. Should lanes communicate via event bus, direct API call, or shared Postgres state?
2. Is Lane C truly distinct from Lane A, or is readiness detection a feature of the individual journey agent?
3. What does failure look like in each lane, and how does the system degrade gracefully?
4. How does a volunteer contributor spin up a single lane locally without needing the full stack?

---

## Consequences

If this architecture holds:
- Contributors can pick a single lane and go deep without needing to understand the whole system
- Each lane can be tested against a Postgres instance and a Docker-sandboxed agent independently
- The system can be deployed incrementally — Lane A first, B and C when org readiness permits

If this architecture needs revision:
- The cost of changing it now is a conversation. The cost of changing it after six months of code is enormous.
- That is why this ADR exists at Phase 0.

---

*"The window to shape the bones before they calcify — that window is now."*
