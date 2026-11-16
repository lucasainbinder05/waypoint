# Waypoint

An OpenAI-compatible LLM gateway that sits between applications and model providers. It adds
retries and fallback, token-aware rate limiting, caching (exact and semantic), cost tracking,
and cost-aware routing, backed by benchmarks and evaluations.

> Status: early development. See docs/devlog.md for progress.

## Quickstart

```bash
python -m venv .venv
source .venv/bin/activate        # Windows PowerShell: .venv\Scripts\Activate.ps1
pip install -e ".[dev]"
uvicorn waypoint.main:app --reload
```

Then open http://127.0.0.1:8000/health. Run the tests with `pytest`.

## Documentation

- docs/architecture.md: how the pieces fit together (in progress)
- docs/decisions/: short records of design decisions
- docs/benchmarks/: methodology and results (added in Week 6)
