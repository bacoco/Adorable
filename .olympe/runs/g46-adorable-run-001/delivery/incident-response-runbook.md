# Incident Response Runbook

Run: g46-adorable-run-001
Release plan: .olympe/runs/g46-adorable-run-001/delivery/release-plan.json
Rollback plan: .olympe/runs/g46-adorable-run-001/delivery/rollback-plan.json

## Trigger

- Production degradation after an approved release.
- Unexpected Argos `gate_blocked` or monitoring threshold breach.

## Immediate Actions

1. Preserve current state and evidence without storing secrets in `.olympe/`.
2. Assign an incident owner and confirm communication channel.
3. Decide rollback only through explicit human approval.
4. Record decisions, timeline and evidence refs.

## Handoff

- Use the rollback plan before any production action.
- Prepare the post-mortem template after resolution.
