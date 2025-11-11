# ecommerce-synth-lab
Synthetic storefront signals for Elastic demos — reproducible logs, metrics, traces, and change events.

## Why
Recreate real e-commerce failures (rate-limit misconfig, PII leaks, time skew) so agents can diagnose end-to-end with ESQL, ML, and relevance.

## Scenarios
- A: Gateway rate-limit misconfig → 429 spike (this repo’s starter)
- B: PII leak in logs → compliance workflow
- C: Time-skew hydra → JWT nbf + node drift + retries

## Repo scaffold
ecommerce-synth-lab/
├─ README.md
├─ LICENSE
├─ scenarios/
│  ├─ A_gateway_rate_limit/
│  │  ├─ README.md
│  │  ├─ configs/
│  │  │  ├─ scenario.yaml              # contract: knobs + timeline (spec below)
│  │  │  ├─ ecs_mappings/              # your ECS/TSDS index templates go here
│  │  ├─ datasets/
│  │  │  ├─ samples.ndjson             # tiny exemplar docs (optional)
│  │  ├─ kibana/
│  │  │  ├─ saved_objects.ndjson       # dashboards/lenses for demo
│  │  ├─ generators/                   # (code later) logs | metrics | traces | changes
│  │  ├─ orchestrators/
│  │  │  └─ timeline_runner/           # (code later) baseline → burst → misconfig → recovery
│  │  ├─ makefiles/
│  │  │  └─ Makefile                   # make seed | run | inject-error | recover | clean
│  │  └─ docs/
│  │     ├─ runbook_rate_limit.md
│  │     └─ incident_notes.md
│  ├─ B_pii_leak/                       # placeholder for Scenario B
│  └─ C_time_skew_hydra/                # placeholder for Scenario C
├─ common/
│  ├─ ecs_schemas/                      # shared field lists & mappings (your inputs)
│  ├─ lib/                              # rng seeds, load profiles, bulk batching (code later)
│  ├─ ingest_pipelines/                 # geoip, UA, redaction examples
│  └─ mcp_mocks/                        # config diff, flags, chatops, tickets (stubs later)
└─ CI/
   └─ smoke.yml                         # GH Actions: mapping lint, dry-run, determinism checks (later)


## How it works
Timeline phases (baseline → burst → inject → recover) drive generators for logs/metrics/traces/changes. Deterministic via RNG seed.

## Quick start
1) Add your ECS/TSDS mappings to `scenarios/*/configs/ecs_mappings/`
2) (Optional) import `kibana/saved_objects.ndjson`
3) Run the timeline runner (coming next)

## License
MIT

