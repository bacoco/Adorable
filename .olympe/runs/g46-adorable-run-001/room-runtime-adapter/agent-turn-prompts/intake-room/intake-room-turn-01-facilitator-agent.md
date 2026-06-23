# Super-Hermes Agent Turn Prompt - intake-room-turn-01-facilitator-agent

Room: intake-room
Agent: facilitator-agent
Turn index: 1
Invitation scope: required
Source repo: freestyle-sh/adorable (read-only)
Working repo: bacoco/adorable

Input Refs:
- Agent brief: .olympe/runs/g46-adorable-run-001/room-sessions/agent-briefs/intake-room/facilitator-agent.md
- Room runtime plan: .olympe/runs/g46-adorable-run-001/room-sessions/runtime-plans/intake-room.json
- Room prompt: .olympe/runs/g46-adorable-run-001/room-sessions/prompts/intake-room.md
- Room execution contract: .olympe/runs/g46-adorable-run-001/room-sessions/execution-contracts/intake-room.json
- Agent turn execution contract: .olympe/runs/g46-adorable-run-001/room-runtime-adapter/agent-turn-contracts/intake-room/intake-room-turn-01-facilitator-agent.json
- Context request ledger: .olympe/runs/g46-adorable-run-001/room-sessions/context-request-ledger.jsonl
- Context resolution report: .olympe/runs/g46-adorable-run-001/context-resolution/context-request-resolution.json

Output Draft Refs:
- fiche-besoin: .olympe/runs/g46-adorable-run-001/room-sessions/output-drafts/intake-room/fiche-besoin.md sha256:8f274456b98e9cd96bc0c315e1771a1c1c78c7f0cdbb0613f272fbf04a0dd7df status:deterministic_draft
- pdd-projet: .olympe/runs/g46-adorable-run-001/room-sessions/output-drafts/intake-room/pdd-projet.md sha256:4aa8de7aa84dc04d3b2e6712c65af254ce03f459638de7e8523fcfe18748067f status:deterministic_draft
- decision-intake: .olympe/runs/g46-adorable-run-001/room-sessions/output-drafts/intake-room/decision-intake.md sha256:04a9a0b33f3bec6b279a0b995d88e5eed08f4350498e4c4a4f8f80582d027655 status:deterministic_draft

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
