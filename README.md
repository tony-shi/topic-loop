# Topic Loop

Topic Loop is an experimental system that continuously follows a topic, keeps
your knowledge current, and tests what you understand.

It is not only a feed reader, deep-search agent, RAG system, or generated wiki.
Its intended loop is:

```text
Orient → Observe → Detect Change → Forge Knowledge → Challenge → Adapt
```

- **Orient** — define what the user is trying to understand and why.
- **Observe** — continuously monitor repositories, releases, papers, news, and
  other relevant sources.
- **Detect Change** — remove duplication and identify semantic changes,
  contradictions, emerging topics, and trend shifts.
- **Forge Knowledge** — turn evidence into traceable claims, living knowledge,
  and reviewable proposals.
- **Challenge** — test whether the user can explain, compare, debug, design, or
  implement what they believe they understand.
- **Adapt** — reprioritize monitoring and research based on domain impact and
  demonstrated knowledge gaps.

## First proving ground

The first domain will be MaaS and LLM inference infrastructure. The initial
vertical slice will follow changes across projects such as vLLM Router and
llm-d Router, determine which changes matter, propose evidence-backed updates
to a separate knowledge repository, and challenge the user's understanding of
the affected architecture.

## Project status

Idea and architecture validation. No production-ready implementation exists
yet.

See [docs/vision.md](docs/vision.md) for the initial product boundary.
See [docs/manual-first.md](docs/manual-first.md) for how a domain can be
bootstrapped before Topic Loop automation exists.

## License

[MIT](LICENSE)
