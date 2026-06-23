# Room Output Draft - dependances

Run: g46-adorable-run-001
Room: story-room
Output id: dependances
Status: deterministic-draft
Runtime: local-deterministic-super-hermes-fixture
Live model invoked: false
Raw source content stored: false
Source repo: freestyle-sh/adorable (read-only)
Working repo: operator-or-olympe-workspace/adorable-olympe-work
Template: .olympe/runs/g46-adorable-run-001/room-sessions/output-templates/story-room/dependances.md sha256:fd2f3c3d73f138fb0b20f5667e371bf8a3e137f2da60bb089540eb2047b00969
Runtime plan: .olympe/runs/g46-adorable-run-001/room-sessions/runtime-plans/story-room.json
Execution contract: .olympe/runs/g46-adorable-run-001/room-sessions/execution-contracts/story-room.json

## Decision Link
- Room decision: continue_with_documented_handoff
- Human validation required: false
- Next room: qa-room

## Evidence Refs
- .olympe/runs/g46-adorable-run-001/room-sessions/runtime-plans/story-room.json
- .olympe/runs/g46-adorable-run-001/room-sessions/execution-contracts/story-room.json
- .olympe/runs/g46-adorable-run-001/room-sessions/output-templates/story-room/dependances.md
- .olympe/runs/g46-adorable-run-001/spec-pack.json
- .olympe/runs/g46-adorable-run-001/story-slicing.yml
- .olympe/runs/g46-adorable-run-001/runner-task.json
- .olympe/runs/g46-adorable-run-001/room-sessions/agent-positions/story-room/product-owner-agent.json
- .olympe/runs/g46-adorable-run-001/room-sessions/agent-positions/story-room/architect-devlead-agent.json
- .olympe/runs/g46-adorable-run-001/room-sessions/agent-positions/story-room/developer-runner-agent.json
- .olympe/runs/g46-adorable-run-001/room-sessions/agent-positions/story-room/test-agent.json
- .olympe/runs/g46-adorable-run-001/room-sessions/agent-positions/story-room/documentation-agent.json

## Agent Positions
- product-owner-agent: .olympe/runs/g46-adorable-run-001/room-sessions/agent-positions/story-room/product-owner-agent.json
- architect-devlead-agent: .olympe/runs/g46-adorable-run-001/room-sessions/agent-positions/story-room/architect-devlead-agent.json
- developer-runner-agent: .olympe/runs/g46-adorable-run-001/room-sessions/agent-positions/story-room/developer-runner-agent.json
- test-agent: .olympe/runs/g46-adorable-run-001/room-sessions/agent-positions/story-room/test-agent.json
- documentation-agent: .olympe/runs/g46-adorable-run-001/room-sessions/agent-positions/story-room/documentation-agent.json

## Draft Body
- This deterministic draft maps `dependances` to the current room contract, evidence refs and agent positions.
- Treat it as an operator-facing draft, not as final live Super-Hermes output.
- Finalization requires either human validation or a future live room execution evidence pack.
- Claims without evidence refs must remain assumptions or blockers.

## Gates
- criteres_acceptation_definis: documented
- tests_previsibles: documented
- perimetre_borne: documented

## Handoff
- Next room or operator: qa-room
- Context still needed: request only explicit `.olympe/` refs through the context request ledger.
- Safe next action: review this draft, then continue through the planned room handoff.
