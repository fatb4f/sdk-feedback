# Summary and authority

P0 proves one complete, isolated rollout-feedback episode:

```text
CUE constraints
    ↓
generated Pydantic transports
    ↓
Codex lifecycle events
    ↓
immutable append-only raw event log
    ↓
typed pytest, CPython, and pytest-eval observations
    ↓
claim-specific admission
    ↓
estimated control state
    ↓
bounded intervention
    ↓
reconciled and sealed evidence manifest
    ↓
independent qualification kernel
    ↓
PromotionAuthorization
```

Authority is partitioned as follows:

```text
CUE
    defines authored admissibility constraints

Generated Pydantic models
    transport structurally projected data

Admission service
    evaluates claims against CUE constraints

Controller
    selects bounded interventions

Codex
    proposes and executes repository changes

Qualification kernel
    exclusively authorizes merge, release, or deployment
```

`codex_reported_success` is an observation only. It cannot satisfy a promotion
claim or issue authorization.

P0 uses one scoped-cache state-lifetime fixture, one CPython provider, one
`pytest-eval` behavioral case, one planner/implementer trajectory, one repair
turn, and one isolated fork. It includes a deterministic SDK-compatible driver
for mandatory CI and a credential-gated live Codex episode using the same
contracts.

P0 does not include mutation testing, repeated-rollout statistics, adaptive
`python-control`, broad provider registries, live steering, interruption,
Stop-hook continuation, rollback, containers, waivers, or real promotion-effect
adapters.
