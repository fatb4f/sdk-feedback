# Event collection, providers, and admission

Store rollout evidence outside every Codex-writable workspace. Append each
Codex SDK method result and streamed notification to a rollout-scoped JSONL
event log. Existing records are never rewritten.

Terminal-event reconciliation checks turn and item pairing, sequence
continuity, SDK errors, provider completion, repository snapshots, and external
effect records. A stream may be sealed while incomplete; affected claims remain
`UNKNOWN`.

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
