# Super-Hermes Room Prompt - story-room

Mode: deterministic fixture now; same prompt shape is intended for live Super-Hermes later.
Room: Story Room
Hermes profile: hermes-dev
Objective: Decouper le besoin en taches bornees et verifiables.
Runtime plan: .olympe/runs/g46-adorable-run-001/room-sessions/runtime-plans/story-room.json
Execution contract JSON: .olympe/runs/g46-adorable-run-001/room-sessions/execution-contracts/story-room.json
Context request ledger: .olympe/runs/g46-adorable-run-001/room-sessions/context-request-ledger.jsonl
Source repo: freestyle-sh/adorable (read-only)
Working repo: operator-or-olympe-workspace/adorable-olympe-work

Execution Contract:
- Execute this room only within the listed objective, outputs and gates.
- Produce a decision, risks, handoff and Argos-observable evidence.
- Stop with `blocked` if required context is missing or a safety rule would be violated.

Context Loading Policy:
- Read only these run refs first:
- .olympe/runs/g46-adorable-run-001/spec-pack.json sha256:65eaba4518ad3ff1cc5eb823f3aff4c59d82280ee69502fdf0daf44dc0249b1f
- .olympe/runs/g46-adorable-run-001/story-slicing.yml sha256:70fc8f4961419e3e04207c6826baecc98d6ee4946f59873ddd275c1cb2700c8e
- .olympe/runs/g46-adorable-run-001/runner-task.json sha256:536f360c18d5c489792dbeedfbaf5ffcdb4b05f675a53ec89276cf3f64b8df2d
- Defer source file contents, logs and publication approvals until a room decision explicitly requests them.
- Record every loaded, deferred or ignored ref in the room handoff.
- If an agent needs additional context, add a structured `context_requests` entry instead of loading broadly.
- Use only `.olympe/` refs in context requests; source file reads require explicit room decision and operator review if sensitive.

Deliberation Protocol:
- Each agent returns one position with evidence refs, blockers and context requests.
- Facilitator summarizes positions, records unresolved disagreements, then emits the room decision.
- Record unresolved disagreements in both the JSON summary and the handoff.

Agent Turn Order:
- required: product-owner-agent (one_position_with_evidence_then_handoff_needs)
- required: architect-devlead-agent (one_position_with_evidence_then_handoff_needs)
- required: developer-runner-agent (one_position_with_evidence_then_handoff_needs)
- invited: test-agent (one_position_with_evidence_then_handoff_needs)
- invited: documentation-agent (one_position_with_evidence_then_handoff_needs)

Required agents:
- product-owner-agent
- architect-devlead-agent
- developer-runner-agent

Invited agents:
- test-agent
- documentation-agent

Expected outputs:
- stories
- dependances
- criteres-acceptation

Output Templates:
- stories: .olympe/runs/g46-adorable-run-001/room-sessions/output-templates/story-room/stories.md sha256:a699e0bb6693a7d7424530ba2ef10f566748433171af4fed7f17e3635386e371
- dependances: .olympe/runs/g46-adorable-run-001/room-sessions/output-templates/story-room/dependances.md sha256:fd2f3c3d73f138fb0b20f5667e371bf8a3e137f2da60bb089540eb2047b00969
- criteres-acceptation: .olympe/runs/g46-adorable-run-001/room-sessions/output-templates/story-room/criteres-acceptation.md sha256:8a290ee8e3ed5a5b09320b4c330d0a30146ef4bb68b822b0232f3d55adcbce29
- Every produced output must cite its template ref and evidence refs.
- If an expected output cannot be produced, return an explicit blocker instead of inventing content.

Gates:
- criteres_acceptation_definis
- tests_previsibles
- perimetre_borne

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
