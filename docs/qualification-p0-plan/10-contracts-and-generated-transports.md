# Contracts and generated transports

Define a closed, versioned CUE contract family for:

```text
RolloutSpec
RolloutIdentity
RolloutEpisode
LifecycleEvent
ToolInvocationObservation
PytestObservation
CPythonObservation
LLMBehaviorObservation
ClaimAdmission
ControlState
ControlAction
RepairDirective
BranchFork
RolloutResidual
ExternalEffectManifest
EvidenceManifest
QualificationVerdict
PromotionAuthorization
QualifiedInconclusiveResult
```

Every record carries the qualification schema identifier. `RolloutIdentity`
contains:

```text
rollout_id
parent_rollout_id?
thread_id
turn_id?
item_id?
event_sequence_id
repository_snapshot_before
repository_snapshot_after?
workspace_instance_id
environment_digest
model_configuration_digest
evaluation_spec_digest
policy_digest
provider_id?
provider_version?
cue_schema_digest
generator_version
admission_service_version
```

Digests are domain-tagged SHA-256 values over canonical JSON or canonical
repository entries. Repository snapshots include normalized paths, bytes, and
executable modes while excluding VCS metadata, virtual environments, caches,
evidence logs, and runtime artifacts.

`ClaimAdmission` is the only source of claim status:

```python
class ClaimAdmission(BaseModel):
    claim_id: str
    status: Literal["SATISFIED", "VIOLATED", "UNKNOWN"]
    applicability: Applicability
    freshness: Freshness
    provenance: Provenance
    admitted_observation_ids: tuple[str, ...]
    rejected_observation_ids: tuple[str, ...]
    cue_schema_digest: str
    admission_service_version: str
    validation_result_digest: str
```

Use these obligation classes in P0:

```text
HARD_EXECUTABLE
    deterministic pytest behavior and object-release semantics

HARD_SEMANTIC
    the single rollout-behavior evaluation

ADVISORY_DIAGNOSTIC
    additional CPython retention details
```

Generated Pydantic models are frozen and reject extra fields. Providers cannot
author admissions, claims, residuals, controller state, transitions, or
verdicts. The generator validates CUE, exports deterministic JSON Schema,
generates the models, formats them with locked Ruff, and supports a byte-for-byte
check mode.
