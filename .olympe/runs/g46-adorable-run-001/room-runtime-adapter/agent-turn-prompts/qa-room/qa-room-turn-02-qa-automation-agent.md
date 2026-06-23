# Super-Hermes Agent Turn Prompt - qa-room-turn-02-qa-automation-agent

Room: qa-room
Agent: qa-automation-agent
Turn index: 2
Invitation scope: required
Source repo: freestyle-sh/adorable (read-only)
Working repo: bacoco/adorable

Input Refs:
- Agent brief: .olympe/runs/g46-adorable-run-001/room-sessions/agent-briefs/qa-room/qa-automation-agent.md
- Room runtime plan: .olympe/runs/g46-adorable-run-001/room-sessions/runtime-plans/qa-room.json
- Room prompt: .olympe/runs/g46-adorable-run-001/room-sessions/prompts/qa-room.md
- Room execution contract: .olympe/runs/g46-adorable-run-001/room-sessions/execution-contracts/qa-room.json
- Agent turn execution contract: .olympe/runs/g46-adorable-run-001/room-runtime-adapter/agent-turn-contracts/qa-room/qa-room-turn-02-qa-automation-agent.json
- Context request ledger: .olympe/runs/g46-adorable-run-001/room-sessions/context-request-ledger.jsonl
- Context resolution report: .olympe/runs/g46-adorable-run-001/context-resolution/context-request-resolution.json

Output Draft Refs:
- acceptance-mapping: .olympe/runs/g46-adorable-run-001/room-sessions/output-drafts/qa-room/acceptance-mapping.md sha256:8453ea455331d9b3ac3b8a19fdf7cb8fc9c09c32a228a392552c5afe18774697 status:deterministic_draft
- rapport-non-regression: .olympe/runs/g46-adorable-run-001/room-sessions/output-drafts/qa-room/rapport-non-regression.md sha256:1c3f4299d3cace45e67e608f804a467b055feaba15042565d8d2c75c2a90610c status:deterministic_draft
- verdict-qualite: .olympe/runs/g46-adorable-run-001/room-sessions/output-drafts/qa-room/verdict-qualite.md sha256:35b0b727bb160c1fe3191a5c423d9678c1c9f97dec4f7aed663065a6fb9da6b1 status:deterministic_draft

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
