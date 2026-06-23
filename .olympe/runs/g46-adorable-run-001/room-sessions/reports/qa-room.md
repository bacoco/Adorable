# Room Report - qa-room

Order: 5
Runtime: local-deterministic-super-hermes-fixture
Decision: continue_with_documented_handoff
Human validation required: false

Runtime plan:
- .olympe/runs/g46-adorable-run-001/room-sessions/runtime-plans/qa-room.json

Prompt:
- .olympe/runs/g46-adorable-run-001/room-sessions/prompts/qa-room.md

Execution contract:
- .olympe/runs/g46-adorable-run-001/room-sessions/execution-contracts/qa-room.json

Output templates:
- acceptance-mapping: .olympe/runs/g46-adorable-run-001/room-sessions/output-templates/qa-room/acceptance-mapping.md
- rapport-non-regression: .olympe/runs/g46-adorable-run-001/room-sessions/output-templates/qa-room/rapport-non-regression.md
- verdict-qualite: .olympe/runs/g46-adorable-run-001/room-sessions/output-templates/qa-room/verdict-qualite.md

Output drafts:
- acceptance-mapping: .olympe/runs/g46-adorable-run-001/room-sessions/output-drafts/qa-room/acceptance-mapping.md
- rapport-non-regression: .olympe/runs/g46-adorable-run-001/room-sessions/output-drafts/qa-room/rapport-non-regression.md
- verdict-qualite: .olympe/runs/g46-adorable-run-001/room-sessions/output-drafts/qa-room/verdict-qualite.md

Agent briefs:
- test-agent: .olympe/runs/g46-adorable-run-001/room-sessions/agent-briefs/qa-room/test-agent.md
- qa-automation-agent: .olympe/runs/g46-adorable-run-001/room-sessions/agent-briefs/qa-room/qa-automation-agent.md
- security-agent: .olympe/runs/g46-adorable-run-001/room-sessions/agent-briefs/qa-room/security-agent.md
- rgaa-agent: .olympe/runs/g46-adorable-run-001/room-sessions/agent-briefs/qa-room/rgaa-agent.md
- readiness-agent: .olympe/runs/g46-adorable-run-001/room-sessions/agent-briefs/qa-room/readiness-agent.md

Agent positions:
- test-agent: .olympe/runs/g46-adorable-run-001/room-sessions/agent-positions/qa-room/test-agent.json
- qa-automation-agent: .olympe/runs/g46-adorable-run-001/room-sessions/agent-positions/qa-room/qa-automation-agent.json
- security-agent: .olympe/runs/g46-adorable-run-001/room-sessions/agent-positions/qa-room/security-agent.json
- rgaa-agent: .olympe/runs/g46-adorable-run-001/room-sessions/agent-positions/qa-room/rgaa-agent.json
- readiness-agent: .olympe/runs/g46-adorable-run-001/room-sessions/agent-positions/qa-room/readiness-agent.json

Inputs:
- .olympe/runs/g46-adorable-run-001/qa-verdict.json sha256:295025d22c42020e63ea15b0d6d8488ca1a1b3458b08774eb3af79eb7391da30
- .olympe/runs/g46-adorable-run-001/code-review.json sha256:5b2369f243d2e0038387d85839331ef667e77742a30f6bdf27808d08e410f843
- .olympe/runs/g46-adorable-run-001/pr-pack.json sha256:5c022a986abe10dce3b09c2456b3ec6b286c2e3b006e1c256146240f3d2e9148

Constraints:
- no_secret_values_loaded
- source_repo_read_only
- working_repo_only
- no_live_github_mutation
