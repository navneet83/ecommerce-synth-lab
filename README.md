# ecommerce-synth-lab
Synthetic storefront signals for Elastic demos — reproducible logs, metrics, traces, and change events.

## Why
Recreate real e-commerce failures (rate-limit misconfig, PII leaks, time skew) so agents can diagnose end-to-end with ESQL, ML, and relevance.

## Scenarios
- A: Gateway rate-limit misconfig → 429 spike (this repo’s starter)
- B: PII leak in logs → compliance workflow
- C: Time-skew hydra → JWT nbf + node drift + retries

## How it works
Timeline phases (baseline → burst → inject → recover) drive generators for logs/metrics/traces/changes. Deterministic via RNG seed.

## Quick start
1) Add your ECS/TSDS mappings to `scenarios/*/configs/ecs_mappings/`
2) (Optional) import `kibana/saved_objects.ndjson`
3) Run the timeline runner (coming next)

## License
MIT

