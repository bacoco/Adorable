# Super-Hermes Agent Turn Prompt - architecture-room-turn-01-architect-devlead-agent

Room: architecture-room
Agent: architect-devlead-agent
Turn index: 1
Invitation scope: required
Source repo: freestyle-sh/adorable (read-only)
Working repo: bacoco/adorable

Input Refs:
- Agent brief: .olympe/runs/g46-adorable-run-001/room-sessions/agent-briefs/architecture-room/architect-devlead-agent.md
- Room runtime plan: .olympe/runs/g46-adorable-run-001/room-sessions/runtime-plans/architecture-room.json
- Room prompt: .olympe/runs/g46-adorable-run-001/room-sessions/prompts/architecture-room.md
- Room execution contract: .olympe/runs/g46-adorable-run-001/room-sessions/execution-contracts/architecture-room.json
- Agent turn execution contract: .olympe/runs/g46-adorable-run-001/room-runtime-adapter/agent-turn-contracts/architecture-room/architecture-room-turn-01-architect-devlead-agent.json
- Context request ledger: .olympe/runs/g46-adorable-run-001/room-sessions/context-request-ledger.jsonl
- Context resolution report: .olympe/runs/g46-adorable-run-001/context-resolution/context-request-resolution.json

Output Draft Refs:
- note-architecture: .olympe/runs/g46-adorable-run-001/room-sessions/output-drafts/architecture-room/note-architecture.md sha256:71897a3a7c016836328906d5419c65191994ddab922477ea829f446eacd3309c status:deterministic_draft
- decoupage-taches: .olympe/runs/g46-adorable-run-001/room-sessions/output-drafts/architecture-room/decoupage-taches.md sha256:8282e9a7d94e9c6159d119b513125d7da0c0a672058aec9fff3415a3d73975d4 status:deterministic_draft
- decision-architecture: .olympe/runs/g46-adorable-run-001/room-sessions/output-drafts/architecture-room/decision-architecture.md sha256:153ef7f48de7824a6c8b29941adc9f9b2f494747f4b678b5cb9fcaa5f0ceac3d status:deterministic_draft

Context Loading Policy:
- Load only the refs listed above, output draft refs, and any resolved `.olympe/` refs explicitly assigned to this turn.
- Do not load secret-like paths, credentials, tokens or broad repository contents.
- If context is missing, return a structured context request instead of expanding scope.
- Do not paste raw draft contents into reports; cite draft refs and hashes.

Output Draft Policy:
- Treat deterministic drafts as update targets and evidence refs, not final live outputs.
- Any proposed draft change must cite the relevant `output_draft_refs` entry.
- Final draft replacement requires human validation or live room runtime evidence.

Output Contract:
Return one fenced JSON object named `agent_position` with:
- `turn_id`, `room_id`, `agent_id`, `position`, `evidence_refs`, `output_draft_refs`, `blockers`, `context_requests`, `handoff_notes`.
- `context_requests` entries must include `requested_ref`, `reason`, `status`, `requested_by_agent`, and `human_validation_required`.

Forbidden Actions:
- No GitHub mutation, source repo mutation, merge, push, production action or secret loading.
- Do not include raw prompt, raw brief, raw contract or raw model output in downstream reports.

Exit Criteria:
- The agent position is grounded in `.olympe/` evidence refs.
- Missing context is represented as structured context requests.
- Any disagreement or blocker is explicit.
