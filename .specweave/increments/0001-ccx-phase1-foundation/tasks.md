# Tasks — 0001-ccx-phase1-foundation

## Summary

| Status | Count |
|--------|-------|
| Completed | 8 |
| In Progress | 0 |
| Pending | 0 |
| **Total** | **8** |

---

### T-001: Go scaffold and Phase 1-6 implementation
**User Story**: US-001 | **Satisfies ACs**: AC-US1-01 through AC-US1-09 | **Status**: [x] completed
**Test**: Given ccx-go repo → When `go test ./...` → Then all 19 test packages pass
**Deliverables**: API client, tool system, Bubble Tea TUI, agent spawning, MCP, permissions, compaction. Single binary ~9.1MB.

### T-002: Rust scaffold and Phase 1-6 implementation
**User Story**: US-002 | **Satisfies ACs**: AC-US2-01 through AC-US2-09 | **Status**: [x] completed
**Test**: Given ccx-rs repo → When `cargo test` → Then 113 tests pass across 13 crates
**Deliverables**: API client (reqwest), tool system (traits), Ratatui TUI, tokio agents, MCP, permissions, compaction. Single binary ~4.6MB.

### T-003: .NET full implementation
**User Story**: US-003 | **Satisfies ACs**: AC-US3-01 through AC-US3-08 | **Status**: [x] completed
**Test**: Given ccx-dotnet repo → When `dotnet test` → Then all tests pass
**Notes**: Full implementation complete (72 source files). 138/138 tests passing on net9.0. Spectre.Console TUI, MCP client, compaction, skills, hooks, permission system all implemented. Downgraded from net10.0 (SDK unavailable on build host) — functionally equivalent.

### T-004: Python full implementation
**User Story**: US-004 | **Satisfies ACs**: AC-US4-01 through AC-US4-10 | **Status**: [x] completed
**Test**: Given ccx-py repo → When `pytest tests/ -v` → Then 131 tests pass
**Deliverables**: httpx async client, SSE parser, 7 tools, Textual TUI, asyncio agents, MCP client, skill system, hook system, permissions with 4 modes, MicroCompact + AutoCompact.

### T-005: Rename repos from claude-code-* to ccx-*
**User Story**: US-005 | **Satisfies ACs**: AC-US5-01 | **Status**: [x] completed
**Test**: Given GitHub repos → When checking names → Then all repos are ccx-{go,rs,dotnet,py}

### T-006: Create ccx umbrella repo
**User Story**: US-005 | **Satisfies ACs**: AC-US5-01, AC-US5-02 | **Status**: [x] completed
**Test**: Given ccx repo → When `specweave` checks config → Then umbrella mode active with 4 child repos

### T-007: Add backstory to all READMEs
**User Story**: US-005 | **Satisfies ACs**: AC-US5-01 | **Status**: [x] completed
**Test**: Given all 4 repos → When reading README.md → Then each contains March 31 2026 backstory

### T-008: Cross-implementation feature parity review
**User Story**: US-001, US-002, US-003, US-004 | **Status**: [x] completed
**Test**: Given all implementations → When reviewed against publicly documented AI assistant CLI patterns → Then feature parity across Go/Rust/.NET/Python verified
**Notes**: All four implementations cover the same feature set: streaming API client, tool system, TUI, permission system, context compaction, MCP client, agent spawning, skill/hook systems.
