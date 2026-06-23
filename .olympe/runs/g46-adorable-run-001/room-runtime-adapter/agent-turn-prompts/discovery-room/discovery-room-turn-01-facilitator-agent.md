# Super-Hermes Agent Turn Prompt - discovery-room-turn-01-facilitator-agent

Room: discovery-room
Agent: facilitator-agent
Turn index: 1
Invitation scope: required
Source repo: freestyle-sh/adorable (read-only)
Working repo: bacoco/adorable

Input Refs:
- Agent brief: .olympe/runs/g46-adorable-run-001/room-sessions/agent-briefs/discovery-room/facilitator-agent.md
- Room runtime plan: .olympe/runs/g46-adorable-run-001/room-sessions/runtime-plans/discovery-room.json
- Room prompt: .olympe/runs/g46-adorable-run-001/room-sessions/prompts/discovery-room.md
- Room execution contract: .olympe/runs/g46-adorable-run-001/room-sessions/execution-contracts/discovery-room.json
- Agent turn execution contract: .olympe/runs/g46-adorable-run-001/room-runtime-adapter/agent-turn-contracts/discovery-room/discovery-room-turn-01-facilitator-agent.json
- Context request ledger: .olympe/runs/g46-adorable-run-001/room-sessions/context-request-ledger.jsonl
- Context resolution report: .olympe/runs/g46-adorable-run-001/context-resolution/context-request-resolution.json

Output Draft Refs:
- carte-contexte: .olympe/runs/g46-adorable-run-001/room-sessions/output-drafts/discovery-room/carte-contexte.md sha256:4797d92089f2142ae9d842f5c9f36b1ced763bf8771a7f26ceb26a9792f85111 status:deterministic_draft
- questions-ouvertes: .olympe/runs/g46-adorable-run-001/room-sessions/output-drafts/discovery-room/questions-ouvertes.md sha256:65a40464d1baf2cdf14a2629461fc125456432bb26e08bb8cfa66ace3698a728 status:deterministic_draft
- rooms-recommandees: .olympe/runs/g46-adorable-run-001/room-sessions/output-drafts/discovery-room/rooms-recommandees.md sha256:0f4e6731248fa5df43f755991894f04c496d083d51b816a8eb2a1c36e9c5148c status:deterministic_draft

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
