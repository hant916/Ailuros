# Ailuros Governance Capability Roadmap

> Status: strategic roadmap only. This document does **not** commit the project to immediate implementation, sequencing dates, API compatibility, or delivery milestones.
>
> Purpose: define the business-priority governance planes Ailuros may grow into as a reusable AI-agent governance runtime.

## Product thesis

Ailuros should not be reduced to a single rule gate.

The long-term product model is a governance runtime that can answer, in a controlled and auditable way:

1. **Can we trust this conclusion?**
2. **Can this action execute?**
3. **Did the agent follow the required process?**
4. **Who is acting, for whom, and under what authority?**
5. **Can we prove why the system reached this result?**
6. **Which data and context may be used?**
7. **How much risk, cost, time, and blast radius may this execution consume?**

The roadmap is ordered by **business importance**, not by implementation convenience or technical novelty.

---

## Priority model

| Priority | Governance plane | Business question | Primary business value |
|---|---|---|---|
| **P0** | Decision governance | Can we trust this conclusion? | Prevents unsupported or misleading intelligence from entering downstream decisions |
| **P0** | Action governance | Can this action execute? | Prevents direct operational, financial, compliance, or public-service impact |
| **P0** | Execution-path governance | Did the agent follow the required process? | Prevents bypassed approvals, skipped validation, false success, and invalid lifecycle transitions |
| **P1** | Evidence & accountability governance | Can we prove why this was accepted or executed? | Supports audit, review, incident analysis, regulatory acceptance, and human accountability |
| **P1** | Identity & authority governance | Who is acting for whom? | Establishes delegation, least privilege, ownership, and responsibility boundaries |
| **P1/P2** | Data & context governance | What may the agent see and use? | Controls sensitive data, provenance, cross-boundary context, and contamination risk |
| **P2** | Resource & risk-budget governance | How much may this execution consume or affect? | Bounds cost, runtime, tool usage, blast radius, and autonomous operational risk |

---

# P0 — Core business governance

## 1. Decision Governance

### Business question

**Can we trust this conclusion?**

This is critical when an agent does not merely retrieve information but proposes a business-significant claim, risk signal, classification, recommendation, or decision.

Example:

> “Company A is showing signs of operational contraction.”

Ailuros should eventually be able to govern whether that claim is allowed to become a trusted system conclusion.

### Candidate governance flow

```text
Agent proposes claim
        ↓
Evidence collection
        ↓
Source validation
        ↓
Cross-source validation
        ↓
Contradiction detection
        ↓
Evidence policy
        ↓
Governance judgment
        ↓
ACCEPT / ESCALATE / REJECT
        ↓
Decision receipt
        ↓
Replay / Audit
```

### Candidate capabilities

- Structured claims rather than opaque prose-only conclusions
- Evidence attachment and provenance
- Source-quality policy
- Independent-source counting
- Source-dependency detection
- Contradiction detection
- Evidence sufficiency rules
- Confidence thresholds as policy inputs, not sole truth criteria
- Human escalation for unresolved material claims
- Versioned governance policies
- Decision receipts

### Reference validation projects

- **CreationRadar** — enterprise-state change detection and risk/opportunity intelligence
- **Clarify.run** — fact, source, evidence, and contradiction validation

### Strategic value

Decision governance moves Ailuros beyond “tool-call authorization” into **governed intelligence**.

CreationRadar can discover *what changed*; Ailuros can govern *whether the interpretation is sufficiently supported to be trusted and propagated*.

---

## 2. Action Governance

### Business question

**Can this action execute?**

This remains the clearest and most immediate governance case.

Examples:

- refund money
- send external communications
- modify production data
- change a supplier status
- create or approve a purchase
- publish a risk alert
- invoke privileged tools

### Candidate governance flow

```text
Agent proposes action
        ↓
Policy evaluation
        ↓
Authority / scope check
        ↓
Risk / threshold check
        ↓
ALLOW / REQUIRE APPROVAL / BLOCK
        ↓
Execution receipt
```

### Candidate capabilities

- Pre-action interception
- Policy-as-runtime enforcement
- Human approval gates
- Tool allow/deny rules
- Monetary and operational thresholds
- Context-aware policy evaluation
- Explicit blocked / pending-approval / allowed states
- Execution receipts

### Reference validation projects

- **EverRun** — governed multi-agent execution with real side effects
- **Stikrai** — user-facing AI workflows where policy and action boundaries matter

### Strategic value

Action governance prevents agent errors from becoming real-world loss, policy violation, or unauthorized system change.

---

## 3. Execution-Path Governance

### Business question

**Did the agent follow the required process?**

A correct-looking final result is not necessarily a governed result.

Example required path:

```text
Collect evidence
→ Validate
→ Judge
→ Human review if required
→ Publish
```

A path that jumps directly from collection to publication is a governance violation even if the final conclusion happens to be correct.

### Candidate capabilities

- Required-step contracts
- Typed lifecycle states
- Allowed state transitions
- Required validator / judge stages
- Bypass detection
- False-success detection
- Ownership attribution
- Proof-of-work / proof-of-validation
- Terminal-state consistency
- Replayable execution paths

### Reference validation project

- **EverRun** — strongest engineering testbed for path governance, including multi-agent planning, implementation, validation, judging, lifecycle transitions, evidence, and false-success failure modes

### Strategic value

Execution-path governance is a likely source of durable differentiation because it governs **how** autonomous work was completed, not merely whether the output looks acceptable.

---

# P1 — Accountability and authority

## 4. Evidence & Accountability Governance

### Business question

**Can we prove why the system reached this judgment or performed this action?**

### Candidate outputs

- Decision receipt
- Execution receipt
- Evidence chain
- Policy version
- Source provenance
- Human approval record
- Agent / tool identity
- Execution path
- Replay package

### Candidate principle

Ailuros should not only output a result. It should be able to output **why that result was allowed to become trusted or executable**.

### Strategic value

This is especially relevant for public-sector, regulated, critical-business, and high-consequence deployments.

---

## 5. Identity & Authority Governance

### Business question

**Who is acting, for whom, and under what delegated authority?**

Agent identity is not equivalent to user identity.

Candidate model:

```text
Human / Organization
        ↓ delegates
Agent identity
        ↓ receives scoped authority
Tool / resource access
```

### Candidate capabilities

- Agent identity
- Human sponsor / principal
- Delegated authority
- Session-scoped permissions
- Least-privilege tool access
- Role / tenant / organization boundaries
- Agent-to-agent delegation records
- Authority expiry and revocation

### Strategic value

This establishes responsibility boundaries when autonomous agents operate in shared enterprise or public systems.

---

# P1/P2 — Supporting governance planes

## 6. Data & Context Governance

### Business question

**What information is the agent allowed to access, carry forward, combine, or disclose?**

### Candidate capabilities

- Sensitive-data boundaries
- Secret / credential policies
- PII controls
- Tenant boundaries
- Data residency constraints
- Context provenance
- Source provenance
- Context contamination detection
- Policy-controlled memory use
- Controlled disclosure to external tools / models

### Strategic value

Important for trustworthy operation, but should support the core decision/action/execution story rather than redefine Ailuros as a generic data-security product.

---

# P2 — Scale and autonomous-risk control

## 7. Resource & Risk-Budget Governance

### Business question

**How much resource, cost, time, and operational impact may this agent consume?**

### Candidate controls

```text
max_cost
max_tool_calls
max_runtime
max_model_calls
max_records_changed
max_external_actions
max_concurrent_agents
max_blast_radius
```

### Candidate capabilities

- Execution budgets
- Cost ceilings
- Time ceilings
- Tool-call ceilings
- Change-volume limits
- External-action limits
- Risk-class dependent budgets
- Escalation on budget exhaustion

### Reference validation project

- **EverRun** — suitable testbed for long-running, multi-agent, tool-heavy execution budgets and autonomous blast-radius control

### Strategic value

This becomes increasingly important as agents move from isolated tasks to persistent autonomous operation.

---

# Unified governance model

The long-term Ailuros model can be summarized as three primary business gates with four cross-cutting control planes.

```text
                     AILUROS
              Governance Runtime
                     │
        ┌────────────┼────────────┐
        │            │            │
   Decision Gate  Action Gate  Execution Gate
   Can we trust?  Can it act?   Did it follow
                               the required path?
        │            │            │
        └────────────┼────────────┘
                     │
       Identity · Data · Evidence · Budget
             cross-cutting governance
```

A compact product statement:

> **Ailuros governs what an AI system may believe, what it may do, and how it must get there — with identity, evidence, data boundaries, and accountability preserved across the execution.**

---

# Business sequencing

This roadmap should be validated through concrete workloads rather than implemented as a large speculative platform rewrite.

## Recommended validation order

### Phase A — Strengthen existing core

Focus on concepts already demonstrated by current workloads:

- Action governance
- Execution-path governance
- Evidence / replay primitives

Primary validation workload: **EverRun**.

### Phase B — Governed intelligence

Use **CreationRadar** and **Clarify.run** to validate:

- Structured claims
- Evidence provenance
- Source quality
- Contradiction handling
- Decision receipts
- Human escalation

This establishes the progression:

```text
CreationRadar discovers change
        ↓
Ailuros governs whether the interpretation is trustworthy
        ↓
Trusted intelligence
        ↓
Ailuros governs what follow-up action is allowed
```

### Phase C — Authority and boundaries

Add identity, delegated authority, data/context policy, and stronger accountability semantics as real integrations require them.

### Phase D — Autonomous scale

Add resource and risk-budget governance when long-running / high-volume autonomous workloads make those controls operationally necessary.

---

# Reference-project roles

The current ecosystem should not be presented as four equivalent logos. Each project validates a different part of the governance thesis.

| Project | Strategic role for Ailuros |
|---|---|
| **CreationRadar** | Business wedge for decision governance and enterprise-state change intelligence |
| **EverRun** | Runtime governance stress test for action, path, evidence, replay, lifecycle, and autonomous execution |
| **Clarify.run** | Evidence, source, claim, and contradiction validation workload |
| **Stikrai** | End-user AI application workload for policy, execution, and user-facing governance boundaries |

---

# Explicit non-goals of this roadmap

This document does **not** require:

- implementing all seven governance planes now
- introducing a large state-management framework
- rewriting current working runtime code to match future abstractions
- building a generic policy DSL before concrete use cases require one
- introducing heavyweight workflow/BPM infrastructure
- claiming compliance certifications that do not exist
- claiming production-volume metrics from engineering-validation counts
- coupling all reference projects directly into the Ailuros repository

KISS applies: future abstractions should be earned by repeated real workloads.

---

# Roadmap acceptance criteria

A roadmap item should move toward implementation only when at least one of the following is true:

1. A real reference workload requires it.
2. The same governance problem appears in more than one workload.
3. The absence of the capability creates a material safety, auditability, or business-correctness gap.
4. A customer / public-sector integration requires the capability.
5. Existing implementation evidence shows the abstraction can remain small and composable.

Until then, the item remains a **roadmap capability**, not an implementation mandate.
