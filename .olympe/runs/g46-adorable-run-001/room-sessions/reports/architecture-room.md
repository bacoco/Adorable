# Room Report - architecture-room

Order: 3
Runtime: local-deterministic-super-hermes-fixture
Decision: continue_with_documented_handoff
Human validation required: true

Runtime plan:
- .olympe/runs/g46-adorable-run-001/room-sessions/runtime-plans/architecture-room.json

Prompt:
- .olympe/runs/g46-adorable-run-001/room-sessions/prompts/architecture-room.md

Execution contract:
- .olympe/runs/g46-adorable-run-001/room-sessions/execution-contracts/architecture-room.json

Output templates:
- note-architecture: .olympe/runs/g46-adorable-run-001/room-sessions/output-templates/architecture-room/note-architecture.md
- decoupage-taches: .olympe/runs/g46-adorable-run-001/room-sessions/output-templates/architecture-room/decoupage-taches.md
- decision-architecture: .olympe/runs/g46-adorable-run-001/room-sessions/output-templates/architecture-room/decision-architecture.md

Output drafts:
- note-architecture: .olympe/runs/g46-adorable-run-001/room-sessions/output-drafts/architecture-room/note-architecture.md
- decoupage-taches: .olympe/runs/g46-adorable-run-001/room-sessions/output-drafts/architecture-room/decoupage-taches.md
- decision-architecture: .olympe/runs/g46-adorable-run-001/room-sessions/output-drafts/architecture-room/decision-architecture.md

Agent briefs:
- architect-devlead-agent: .olympe/runs/g46-adorable-run-001/room-sessions/agent-briefs/architecture-room/architect-devlead-agent.md
- facilitator-agent: .olympe/runs/g46-adorable-run-001/room-sessions/agent-briefs/architecture-room/facilitator-agent.md
- product-owner-agent: .olympe/runs/g46-adorable-run-001/room-sessions/agent-briefs/architecture-room/product-owner-agent.md
- security-agent: .olympe/runs/g46-adorable-run-001/room-sessions/agent-briefs/architecture-room/security-agent.md
- documentation-agent: .olympe/runs/g46-adorable-run-001/room-sessions/agent-briefs/architecture-room/documentation-agent.md

Agent positions:
- architect-devlead-agent: .olympe/runs/g46-adorable-run-001/room-sessions/agent-positions/architecture-room/architect-devlead-agent.json
- facilitator-agent: .olympe/runs/g46-adorable-run-001/room-sessions/agent-positions/architecture-room/facilitator-agent.json
- product-owner-agent: .olympe/runs/g46-adorable-run-001/room-sessions/agent-positions/architecture-room/product-owner-agent.json
- security-agent: .olympe/runs/g46-adorable-run-001/room-sessions/agent-positions/architecture-room/security-agent.json
- documentation-agent: .olympe/runs/g46-adorable-run-001/room-sessions/agent-positions/architecture-room/documentation-agent.json

Inputs:
- .olympe/runs/g46-adorable-run-001/project-card.json sha256:93ddbc2e153048f42cf8f73cbf4f579607cf015da389df247e9af4d70e7e8969
- .olympe/runs/g46-adorable-run-001/onboarding-scan.json sha256:daedcd3599d81d29795f7bc5272651649d0d629fa9e8c5c9d6c223c9f763eafb
- .olympe/runs/g46-adorable-run-001/spec-pack.json sha256:65eaba4518ad3ff1cc5eb823f3aff4c59d82280ee69502fdf0daf44dc0249b1f
- .olympe/runs/g46-adorable-run-001/github-memory-plan.json sha256:fcf3effebca5361835a0056ef85273753a583bb173e18a73afae9c2aed5734c3

Constraints:
- no_secret_values_loaded
- source_repo_read_only
- working_repo_only
- no_live_github_mutation
