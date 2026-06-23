# Super-Hermes Agent Turn Prompt - story-room-turn-02-architect-devlead-agent

Room: story-room
Agent: architect-devlead-agent
Turn index: 2
Invitation scope: required
Source repo: freestyle-sh/adorable (read-only)
Working repo: bacoco/adorable

Input Refs:
- Agent brief: .olympe/runs/g46-adorable-run-001/room-sessions/agent-briefs/story-room/architect-devlead-agent.md
- Room runtime plan: .olympe/runs/g46-adorable-run-001/room-sessions/runtime-plans/story-room.json
- Room prompt: .olympe/runs/g46-adorable-run-001/room-sessions/prompts/story-room.md
- Room execution contract: .olympe/runs/g46-adorable-run-001/room-sessions/execution-contracts/story-room.json
- Agent turn execution contract: .olympe/runs/g46-adorable-run-001/room-runtime-adapter/agent-turn-contracts/story-room/story-room-turn-02-architect-devlead-agent.json
- Context request ledger: .olympe/runs/g46-adorable-run-001/room-sessions/context-request-ledger.jsonl
- Context resolution report: .olympe/runs/g46-adorable-run-001/context-resolution/context-request-resolution.json

Output Draft Refs:
- stories: .olympe/runs/g46-adorable-run-001/room-sessions/output-drafts/story-room/stories.md sha256:e82358590ab24315be0dedae360fadd0f9d871c422e6800c8f84a79d42d0a871 status:deterministic_draft
- dependances: .olympe/runs/g46-adorable-run-001/room-sessions/output-drafts/story-room/dependances.md sha256:27f94158ee6f48fab4075d9da44745f333b716ef00b249264cbc3aa37df704c0 status:deterministic_draft
- criteres-acceptation: .olympe/runs/g46-adorable-run-001/room-sessions/output-drafts/story-room/criteres-acceptation.md sha256:8fdc69d04b5a636f457b50b9da62f959256c93a286c44701249bfd7f4abcf689 status:deterministic_draft

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
