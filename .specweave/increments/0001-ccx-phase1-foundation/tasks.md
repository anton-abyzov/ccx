# Tasks — 0001-ccx-phase1-foundation

## Summary

| Status | Count |
|--------|-------|
| Completed | 6 |
| In Progress | 1 |
| Pending | 1 |
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
**User Story**: US-003 | **Satisfies ACs**: AC-US3-01 through AC-US3-08 | **Status**: [ ] in progress
**Test**: Given ccx-dotnet repo → When `dotnet test` → Then all tests pass
**Notes**: Phase 1 (API client, tools interface, query engine) complete. Phases 2-6 in progress.

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

### T-008: Code review against TypeScript source
**User Story**: US-001, US-002, US-003, US-004 | **Status**: [ ] pending
**Test**: Given all implementations → When reviewed against leaked architecture → Then feature parity verified
