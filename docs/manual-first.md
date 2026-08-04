# Manual-first operation

## Decision

Topic Loop should not own domain truth or silently decide what deserves durable
attention. It proposes changes; a human or an explicitly delegated policy
accepts them.

The manual and automated workflows therefore use the same contracts:

```text
World
  → Map Candidate
  → accepted Map Node
  → Knowledge Proposal
  → published domain knowledge
  → Assessment Result
  → updated priorities
```

Before Topic Loop implements discovery and compilation, a human can produce the
same artifacts directly. Automation later replaces repetitive work without
changing the result repository's meaning.

## Repository boundary

Topic Loop owns:

- source observation and fetched snapshots;
- event normalization, deduplication, and semantic change detection;
- map and knowledge proposals;
- prioritization suggestions;
- challenge generation and assessment records;
- pipeline state, caches, and execution history.

A domain repository such as `maas-lab` owns:

- the approved scope and domain charter;
- the accepted knowledge map;
- reviewed notes and claims;
- experiments and benchmark evidence;
- human-authored judgments;
- accepted learning and assessment results.

Fetched material and rejected proposals are not durable domain knowledge.

## Manual 0→1: build the map

The human starts by defining a `Scope Charter`:

- why the domain matters;
- the intended ability or decision outcome;
- explicit in-scope and out-of-scope areas;
- time, hardware, compliance, and cost constraints;
- required depth of understanding;
- review cadence.

The human then surveys the world and creates `Map Candidate` records. A
candidate becomes a `Map Node` only after an explicit decision:

```yaml
id: routing.replica-selection
title: Replica selection
question: Which endpoint should receive a request after a model pool is chosen?
priority: P0
status: mapped

curation:
  introduced_by: human
  introduced_at: 2026-06-23
  decision: include
  reason: Core request-path decision with direct latency and reliability impact
```

Rejected and deferred candidates remain useful audit evidence. They explain why
the map has its current boundary and make future rediscovery cheaper.

Future Topic Loop discovery must create candidates, not accepted nodes:

```yaml
curation:
  introduced_by: topic-loop
  proposal_id: map-candidate-...
  decision: pending
```

## Assisted 1→2: compile the knowledge

An accepted map node defines a question and evidence requirements. Existing
agents and code-analysis tools may collect material, but their output starts as
a `Knowledge Proposal`, never as published knowledge.

```text
Map Node
  → source and code analysis
  → cross-source synthesis
  → evidence and contradiction checks
  → Knowledge Proposal
  → human review
  → domain repository
```

A proposal should include:

- the map node and question it addresses;
- claims being introduced, revised, or contradicted;
- source URLs, repository commits, and code paths;
- confidence and known uncertainty;
- comparison with the current published understanding;
- required experiment or validation work;
- the proposed patch to the domain repository.

For technical domains, publication should require evidence appropriate to the
claim. A source-code claim needs a locked commit and code path. A performance
claim needs workload, hardware, versions, and metric definitions. A mock or CPU
experiment must not be promoted as production GPU evidence.

## Cognition feedback

Assessment is not merely spaced repetition. A challenge may require the user
to:

- explain a mechanism without notes;
- trace a request or control flow through source code;
- compare alternatives and state failure conditions;
- diagnose a scenario;
- predict an experiment result;
- design or implement a validation.

The result updates both mastery and attention:

```text
Knowledge gap
  → increase map priority or evidence requirements
  → observe and compile more deeply

Demonstrated mastery
  → reduce review frequency
  → move attention to a weaker or more important node
```

## Minimal state model

Map candidates:

```text
pending → included | watched | deferred | rejected
```

Map nodes:

```text
mapped → compiling → verified → published → stale
```

Knowledge proposals:

```text
draft → review → accepted | rejected | needs-evidence
```

These states should remain explicit even while all transitions are performed
manually.

## First proving loop

The initial MaaS loop should:

1. define a broad but shallow MaaS map manually;
2. select replica routing as one P0 map node;
3. analyze locked versions of vLLM Router, llm-d Router, and vLLM;
4. publish an evidence-backed comparison to `maas-lab`;
5. run a reproducible mock routing experiment;
6. challenge the user's architecture and source-level understanding;
7. use the gaps to revise the MaaS map.

Topic Loop automation should be added only after this manual loop exposes which
steps are repetitive, expensive, or error-prone.
