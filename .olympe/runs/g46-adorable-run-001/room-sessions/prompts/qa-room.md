# Super-Hermes Room Prompt - qa-room

Mode: deterministic fixture now; same prompt shape is intended for live Super-Hermes later.
Room: QA Room
Hermes profile: hermes-integration
Objective: Verifier criteres d acceptation, tests et non-regression.
Runtime plan: .olympe/runs/g46-adorable-run-001/room-sessions/runtime-plans/qa-room.json
Execution contract JSON: .olympe/runs/g46-adorable-run-001/room-sessions/execution-contracts/qa-room.json
Context request ledger: .olympe/runs/g46-adorable-run-001/room-sessions/context-request-ledger.jsonl
Source repo: freestyle-sh/adorable (read-only)
Working repo: operator-or-olympe-workspace/adorable-olympe-work

Execution Contract:
- Execute this room only within the listed objective, outputs and gates.
- Produce a decision, risks, handoff and Argos-observable evidence.
- Stop with `blocked` if required context is missing or a safety rule would be violated.

Context Loading Policy:
- Read only these run refs first:
- .olympe/runs/g46-adorable-run-001/qa-verdict.json sha256:295025d22c42020e63ea15b0d6d8488ca1a1b3458b08774eb3af79eb7391da30
- .olympe/runs/g46-adorable-run-001/code-review.json sha256:5b2369f243d2e0038387d85839331ef667e77742a30f6bdf27808d08e410f843
- .olympe/runs/g46-adorable-run-001/pr-pack.json sha256:5c022a986abe10dce3b09c2456b3ec6b286c2e3b006e1c256146240f3d2e9148
- Defer source file contents, logs and publication approvals until a room decision explicitly requests them.
- Record every loaded, deferred or ignored ref in the room handoff.
- If an agent needs additional context, add a structured `context_requests` entry instead of loading broadly.
- Use only `.olympe/` refs in context requests; source file reads require explicit room decision and operator review if sensitive.

Deliberation Protocol:
- Each agent returns one position with evidence refs, blockers and context requests.
- Facilitator summarizes positions, records unresolved disagreements, then emits the room decision.
- Record unresolved disagreements in both the JSON summary and the handoff.

Agent Turn Order:
- required: test-agent (one_position_with_evidence_then_handoff_needs)
- required: qa-automation-agent (one_position_with_evidence_then_handoff_needs)
- invited: security-agent (one_position_with_evidence_then_handoff_needs)
- invited: rgaa-agent (one_position_with_evidence_then_handoff_needs)
- invited: readiness-agent (one_position_with_evidence_then_handoff_needs)

Required agents:
- test-agent
- qa-automation-agent

Invited agents:
- security-agent
- rgaa-agent
- readiness-agent

Expected outputs:
- acceptance-mapping
- rapport-non-regression
- verdict-qualite

Output Templates:
- acceptance-mapping: .olympe/runs/g46-adorable-run-001/room-sessions/output-templates/qa-room/acceptance-mapping.md sha256:4cda06fb0406873f31404fe8e2ef8d7a7dd131825af989024b0e6a709e320146
- rapport-non-regression: .olympe/runs/g46-adorable-run-001/room-sessions/output-templates/qa-room/rapport-non-regression.md sha256:6e57890d12a8a3afea615dbcf7d1d78e99d21cae8734f8236600d6d2df7ad008
- verdict-qualite: .olympe/runs/g46-adorable-run-001/room-sessions/output-templates/qa-room/verdict-qualite.md sha256:e08dc4998fba2d52c618012b64400bf9fb84f1ce1a4d28123aaa24fc1ef06883
- Every produced output must cite its template ref and evidence refs.
- If an expected output cannot be produced, return an explicit blocker instead of inventing content.

Gates:
- tests
- revue_securite

Response Format:
- Markdown sections: decision, outputs, risks, agent_positions, context_used, context_requests, unresolved_disagreements, handoff
- JSON summary keys: room_id, decision, outputs_produced, risks, gates, context_refs_used, agent_positions, context_requests, unresolved_disagreements, handoff_to_next_room, human_validation_required
- Allowed decisions: continue, needs_human_validation, blocked
- Emit exactly one fenced JSON object named `room_summary` matching the execution contract.
- Every context ref in JSON must be a `.olympe/` ref already listed in the context ledger or handoff.

Forbidden Actions:
- Do not load secret values.
- Keep source repo read-only.
- Do not create branches, issues, PRs, merges, releases or production actions.
- Do not target the source repo for any mutation.

Exit Criteria:
- Decision recorded.
- Expected outputs mapped to evidence refs or explicit blockers.
- Handoff target and human validation requirement stated.
