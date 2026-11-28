# Synapse

**An open-source learning agent that maps what you need to know and remembers everything you've learned.**

[![License: AGPL v3](https://img.shields.io/badge/License-AGPL_v3-blue.svg)](LICENSE)
![Status: early development](https://img.shields.io/badge/status-early%20development-orange)

> 🚧 Synapse is in active development and being built in the open. Target for v1.0: **December 31, 2026**.
> Nothing is usable yet; star or watch the repo to follow along.

---

## Why

- **You can't learn what you don't know you're missing.** Explanations of "RNN" assume you already know
  neural networks, gradients and backpropagation.
- **AI tutors forget you.** Every chat starts from zero and explains everything generically.
- **People learn by connecting ideas** ("this is like X, except…"). Today's tools don't do that with
  *your* history.

## What Synapse does

1. **Maps the prerequisites.** Type any topic. Synapse asks a couple of calibration questions, then builds a
   live mind map of everything you need to understand first, and stops at what you already know.
2. **Teaches through chat.** Click a concept to learn it with explanations, worked examples, math,
   diagrams and code, all at your level.
3. **Remembers everything.** Every conversation feeds one lifelong learning memory: what you know, how
   well, when you learned it, and what confused you.
4. **Relates new ideas to old ones.** New concepts are explained as a difference from something you
   already learned: *"LSTM is the RNN you learned on Nov 12, plus three gates."*
5. **Checks understanding and schedules reviews.** Short quizzes and explain-it-back checks update a
   mastery score, and spaced repetition reminds you before you forget.

### How "learned" is decided

The language model grades individual answers against rubrics. **Deterministic, tested code** combines
that evidence into a mastery score and decides the state (Unknown → Learning → Learned → Fading). The
model never marks a concept as learned on its own, so every score is consistent and explainable.

## Roadmap

| Release | Scope                                                                                  |
| ------- | -------------------------------------------------------------------------------------- |
| v0.1    | Topic → streamed prerequisite map; tutor chat per concept; mark concepts as known; per-user LLM budgets |
| v0.2    | One personal memory across all chats; knowledge state on the map; export and delete     |
| v0.3    | Relate engine: explanations built on what you already learned                          |
| v0.4    | Quizzes, explain-back, mastery scores, spaced-repetition reviews, reminders, learning dashboard |
| v0.5    | Self-hosting with Docker Compose, bring your own API key, full audit log, hardening      |
| v1.0    | Load-tested with published SLOs, security review, docs site, public demo account        |

Synapse is built for individual learners: your learning data belongs to you alone, and is never
shared with or owned by a team or organization.

## Tech stack

| Layer       | Choice                                                                        |
| ----------- | ----------------------------------------------------------------------------- |
| Web         | Next.js, TypeScript, Tailwind CSS, React Flow                                 |
| API         | Python 3.12, FastAPI, Pydantic, SQLAlchemy                                    |
| Data        | PostgreSQL 16 with pgvector, Redis                                            |
| Jobs        | Celery                                                                        |
| LLM         | Claude (Anthropic) behind a provider abstraction                              |
| Quality     | pytest, Vitest, Playwright, an LLM evaluation suite in CI                     |
| Observability | OpenTelemetry traces, Sentry errors, Langfuse LLM traces and cost, structured logs |
| Ops         | Docker, GitHub Actions                                                        |

## Getting started

Setup instructions arrive with v0.1. The goal is a single `docker compose up` for local development.

## Contributing

Contributions are welcome once the foundations land. Please read [CONTRIBUTING.md](CONTRIBUTING.md) and
the [Code of Conduct](CODE_OF_CONDUCT.md). To report a vulnerability, see [SECURITY.md](SECURITY.md).

## License

Synapse is licensed under the [GNU Affero General Public License v3.0](LICENSE). If you run a modified
version as a network service, you must make your source code available to its users under the same
license.
