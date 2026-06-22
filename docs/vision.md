# Vision

## Problem

Information systems optimize for collecting and retrieving content. They do not
reliably answer:

1. What has meaningfully changed relative to what I already know?
2. Which changes deserve my limited attention?
3. What should update in my current knowledge?
4. Do I actually understand the domain well enough to explain, choose, debug,
   or build within it?

Topic Loop treats these as one continuous system.

## Three loops

### Intelligence loop

```text
Scope → Observe → Normalize → Deduplicate → Detect Delta → Prioritize
```

The primary output is not a stream of new documents. It is a ranked set of
meaningful changes: corroborations, revisions, contradictions, emergent
concepts, trend shifts, and action triggers.

### Knowledge loop

```text
Change Set → Claims → Evidence → Verification → Proposal → Publication
```

Raw events and evidence history remain traceable. A wiki or knowledge repository
is a projection of the current best understanding, not the source of truth.

### Cognition loop

```text
Knowledge Map → Challenge → Assessment → Gap → Reprioritization
```

Assessment should go beyond flashcards. For technical domains it may include
closed-book explanation, source tracing, trade-off analysis, debugging,
prediction, experiment design, and implementation.

## Initial boundaries

- The engine should be domain-neutral.
- Domain policies define trusted sources, ontology, impact, evidence standards,
  and assessment methods.
- Result repositories remain separate from pipeline state and source caches.
- Human review is required before publishing durable knowledge.
- The first implementation should be a modular monolith, not a distributed
  multi-agent platform.

## Initial non-goals

- Building a universal knowledge graph from day one.
- Replacing RSS readers, search engines, or code intelligence tools.
- Automatically treating summaries as verified knowledge.
- Measuring progress by document, page, or graph-node count.
- Claiming generality before one technical domain is proven end to end.

## First validation

For MaaS replica routing:

1. Monitor selected GitHub repositories.
2. Detect capability and architecture changes rather than reporting every
   commit.
3. Map changes to affected claims and notes.
4. Produce a reviewable knowledge proposal.
5. Generate architecture and source-level challenges.
6. Use the assessment result to update the next observation priorities.
