# Event collection, providers, and admission

Store rollout evidence outside every Codex-writable workspace. Append each
Codex SDK method result and streamed notification to a rollout-scoped JSONL
event log. Existing records are never rewritten.

AR0 proves producer-boundary-lossless capture over the pinned app-server and
Python SDK observation surfaces. It retains every received payload exactly,
assigns stable source identity, normalizes deterministically, and reconciles
each payload or marks it explicitly unhandled. It does not claim universal
process observability: an expected but unreceived event is not evidence that
the underlying event or state was absent.

Raw app-server payload bytes are retained as private content-addressed
artifacts. The SDK producer retains its complete public notification
representation together with SDK and runtime versions; it does not claim
wire-level details unavailable through the SDK.

Terminal-event reconciliation checks turn and item pairing, sequence
continuity, SDK errors, provider completion, repository snapshots, and external
effect records. A stream may be sealed while incomplete; affected claims remain
`UNKNOWN`.

Sealing requires a policy-relative closure witness identifying the expected
terminal surfaces, observed terminal payloads, unresolved streams, timeout or
termination policy, and closure classification. Closure is bounded observation
closure, not a claim of global completeness.

Implement one project-owned pytest provider that emits normalized collection,
setup/teardown, call, exit, timeout, signal, output, and capture-integrity
facts. It does not classify qualification.

Implement one CPython state-lifetime provider using `weakref`,
`gc.collect()`, and normalized candidate-owned referrer facts. It reports
whether the scoped object remains alive after closure and what candidate
container retains it. It does not derive claim status.

Implement one `pytest-eval` `ai.judge` case over the repair rationale. The case
checks that the repair identifies retained lifecycle state and grounds the
proposed correction in both the hidden probe and CPython observation.

The evaluator runs in a trusted process after Codex execution. Provider, model,
budget, and evaluator configuration are required by `EvaluationSpec`; evaluator
credentials never enter a Codex workspace or process environment.

The admission service evaluates every proposed claim against:

```text
exact subject identity
probe and oracle identity
policy and evaluation digests
environment compatibility
provider identity and version
capture integrity
freshness and applicability
CUE constraints
```

There is no universal confidence scalar. Controller features derived from
admissions are not evidence and cannot be reused as qualification claims.
