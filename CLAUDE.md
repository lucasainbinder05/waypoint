# Waypoint

OpenAI-compatible LLM gateway: provider routing, resilience, rate limiting, caching, cost tracking.
Session log: docs/devlog.md. Design decisions: docs/decisions/.

## Stack
Python 3.12, FastAPI (async), Redis, Postgres + pgvector, pytest, k6, Docker Compose.

## Commands
- Install: pip install -e ".[dev]"
- Run server: uvicorn waypoint.main:app --reload
- Tests: pytest
- Lint: ruff check . && ruff format --check .
- Local services (from Week 3): docker compose up -d

## Layout
src/waypoint/ holds the app, one package per concern: api, auth, ratelimit, cache, routing,
providers, resilience, accounting, observability. tests/ mirrors it. bench/ has load tests and
the mock provider server. evals/ has labeled datasets and eval scripts.

## Rules
- Write or update tests with every change, and run them before calling anything done.
- Small, focused commits with clear messages. One concern per commit.
- Ask before adding a dependency.
- Never commit secrets. Keys live in .env (gitignored).
- Non-obvious design decisions get a short ADR in docs/decisions/.
- Benchmark and eval numbers must come from real runs. Never invent figures.
- Explain tradeoffs briefly when proposing a design. I make the final call.
