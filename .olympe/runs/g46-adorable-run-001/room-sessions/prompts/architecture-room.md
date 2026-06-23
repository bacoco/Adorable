# Super-Hermes Room Prompt - architecture-room

Mode: deterministic fixture now; same prompt shape is intended for live Super-Hermes later.
Room: Architecture Room
Hermes profile: hermes-cadrage
Objective: Poser une architecture legere et decouper en taches bornees.
Runtime plan: .olympe/runs/g46-adorable-run-001/room-sessions/runtime-plans/architecture-room.json
Execution contract JSON: .olympe/runs/g46-adorable-run-001/room-sessions/execution-contracts/architecture-room.json
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
- .olympe/runs/g46-adorable-run-001/spec-pack.json sha256:65eaba4518ad3ff1cc5eb823f3aff4c59d82280ee69502fdf0daf44dc0249b1f
- .olympe/runs/g46-adorable-run-001/github-memory-plan.json sha256:fcf3effebca5361835a0056ef85273753a583bb173e18a73afae9c2aed5734c3
- Defer source file contents, logs and publication approvals until a room decision explicitly requests them.
- Record every loaded, deferred or ignored ref in the room handoff.
- If an agent needs additional context, add a structured `context_requests` entry instead of loading broadly.
- Use only `.olympe/` refs in context requests; source file reads require explicit room decision and operator review if sensitive.

Deliberation Protocol:
- Each agent returns one position with evidence refs, blockers and context requests.
- Facilitator summarizes positions, records unresolved disagreements, then emits the room decision.
- Record unresolved disagreements in both the JSON summary and the handoff.

Agent Turn Order:
- required: architect-devlead-agent (one_position_with_evidence_then_handoff_needs)
- required: facilitator-agent (one_position_with_evidence_then_handoff_needs)
- invited: product-owner-agent (one_position_with_evidence_then_handoff_needs)
- invited: security-agent (one_position_with_evidence_then_handoff_needs)
- invited: documentation-agent (one_position_with_evidence_then_handoff_needs)

Required agents:
- architect-devlead-agent
- facilitator-agent

Invited agents:
- product-owner-agent
- security-agent
- documentation-agent

Expected outputs:
- note-architecture
- decoupage-taches
- decision-architecture

Output Templates:
- note-architecture: .olympe/runs/g46-adorable-run-001/room-sessions/output-templates/architecture-room/note-architecture.md sha256:23f53e1b5638de89ac55b59e0c60a65cc90381600f247fece186a033832ef752
- decoupage-taches: .olympe/runs/g46-adorable-run-001/room-sessions/output-templates/architecture-room/decoupage-taches.md sha256:2281441c7b743936c5708eab23a100744d66e9a426bb0110f3c80b538a1bcb94
- decision-architecture: .olympe/runs/g46-adorable-run-001/room-sessions/output-templates/architecture-room/decision-architecture.md sha256:07e9243f09d71dcf3ebcf6d5828e0812db6a3184dc8269fe414538b6e17dc03f
- Every produced output must cite its template ref and evidence refs.
- If an expected output cannot be produced, return an explicit blocker instead of inventing content.

Gates:
- architecture_legere_validee
- controle_informations_confidentielles

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
