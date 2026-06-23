# Super-Hermes Room Prompt - discovery-room

Mode: deterministic fixture now; same prompt shape is intended for live Super-Hermes later.
Room: Discovery Room
Hermes profile: hermes-cadrage
Objective: Explorer le contexte, les contraintes et les inconnues.
Runtime plan: .olympe/runs/g46-adorable-run-001/room-sessions/runtime-plans/discovery-room.json
Execution contract JSON: .olympe/runs/g46-adorable-run-001/room-sessions/execution-contracts/discovery-room.json
Context request ledger: .olympe/runs/g46-adorable-run-001/room-sessions/context-request-ledger.jsonl
Source repo: freestyle-sh/adorable (read-only)
Working repo: operator-or-olympe-workspace/adorable-olympe-work

Execution Contract:
- Execute this room only within the listed objective, outputs and gates.
- Produce a decision, risks, handoff and Argos-observable evidence.
- Stop with `blocked` if required context is missing or a safety rule would be violated.

Context Loading Policy:
- Read only these run refs first:
- .olympe/runs/g46-adorable-run-001/project-card.json sha256:93ddbc2e153048f42cf8f73cbf4f579607cf015da389df247e9af4d70e7e8969
- .olympe/runs/g46-adorable-run-001/onboarding-scan.json sha256:daedcd3599d81d29795f7bc5272651649d0d629fa9e8c5c9d6c223c9f763eafb
- .olympe/runs/g46-adorable-run-001/progressive-disclosure-log.json sha256:040270bb52c0b382ecffad8cbef0304dfec7900b45e4c8deb66f8a99c360ed2a
- .olympe/runs/g46-adorable-run-001/room-openings.json sha256:1ee1e965e985aa2e5aa7d26d0feb186dae82ab65f34e661033b2d2f94a6aad0d
- Defer source file contents, logs and publication approvals until a room decision explicitly requests them.
- Record every loaded, deferred or ignored ref in the room handoff.
- If an agent needs additional context, add a structured `context_requests` entry instead of loading broadly.
- Use only `.olympe/` refs in context requests; source file reads require explicit room decision and operator review if sensitive.

Deliberation Protocol:
- Each agent returns one position with evidence refs, blockers and context requests.
- Facilitator summarizes positions, records unresolved disagreements, then emits the room decision.
- Record unresolved disagreements in both the JSON summary and the handoff.

Agent Turn Order:
- required: facilitator-agent (one_position_with_evidence_then_handoff_needs)
- required: project-analyst-agent (one_position_with_evidence_then_handoff_needs)
- required: repo-knowledge-agent (one_position_with_evidence_then_handoff_needs)
- invited: product-owner-agent (one_position_with_evidence_then_handoff_needs)
- invited: documentation-agent (one_position_with_evidence_then_handoff_needs)

Required agents:
- facilitator-agent
- project-analyst-agent
- repo-knowledge-agent

Invited agents:
- product-owner-agent
- documentation-agent

Expected outputs:
- carte-contexte
- questions-ouvertes
- rooms-recommandees

Output Templates:
- carte-contexte: .olympe/runs/g46-adorable-run-001/room-sessions/output-templates/discovery-room/carte-contexte.md sha256:54acfab98a417d4af2edc68c52b894a8034d86d8b3a86aab50e9be02fab1a8ee
- questions-ouvertes: .olympe/runs/g46-adorable-run-001/room-sessions/output-templates/discovery-room/questions-ouvertes.md sha256:1c332df7fe4ae97a75482ba142f5ebab0d8bd1a4f1d85fc113ea137a7ead3f77
- rooms-recommandees: .olympe/runs/g46-adorable-run-001/room-sessions/output-templates/discovery-room/rooms-recommandees.md sha256:3a22c83a1cfddac948c31cb5dc85de3a137078b1be8bb76805b6c6f295e29b87
- Every produced output must cite its template ref and evidence refs.
- If an expected output cannot be produced, return an explicit blocker instead of inventing content.

Gates:
- contexte_suffisant
- inconnues_listees

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
