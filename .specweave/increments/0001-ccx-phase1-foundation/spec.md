# CCX Phase 1: Foundation

## Overview

Build the foundation layer of the CCX (Claude Code eXtended) project across four language implementations: Go, Rust, .NET, and Python. Each implementation provides a working AI coding assistant CLI with API client, tool system, TUI, agent spawning, context compression, MCP integration, and permission controls.

## Background

On March 31, 2026, the Claude Code CLI system prompt was found embedded in plaintext within the npm package. The ~100KB prompt exposed the complete architecture. CCX is a collection of clean-room implementations built from these architectural insights.

---

## User Stories

### US-001: Go Implementation (ccx-go)

**As a** Go developer,
**I want** a native Go implementation of the AI coding assistant,
**So that** I can use a single-binary CLI with no runtime dependencies.

**Acceptance Criteria:**
- [x] AC-US1-01: API client with streaming SSE parser
- [x] AC-US1-02: Tool system (bash, file read/write/edit, glob, grep, web fetch)
- [x] AC-US1-03: Agentic query loop with parallel tool execution
- [x] AC-US1-04: Bubble Tea TUI with markdown rendering
- [x] AC-US1-05: Permission system with risk classification
- [x] AC-US1-06: Context compaction (MicroCompact, AutoCompact)
- [x] AC-US1-07: MCP client (JSON-RPC over stdio)
- [x] AC-US1-08: All 19 test packages passing
- [x] AC-US1-09: Single binary build (~9.1MB)

### US-002: Rust Implementation (ccx-rs)

**As a** Rust developer,
**I want** a native Rust implementation with maximum performance and safety,
**So that** I can use a memory-safe, zero-cost-abstraction CLI.

**Acceptance Criteria:**
- [x] AC-US2-01: API client with async streaming (reqwest + eventsource)
- [x] AC-US2-02: Tool system with trait-based dispatch
- [x] AC-US2-03: Agentic query loop with tokio tasks
- [x] AC-US2-04: Ratatui TUI with crossterm backend
- [x] AC-US2-05: Permission system with risk classification
- [x] AC-US2-06: Context compaction
- [x] AC-US2-07: MCP client
- [x] AC-US2-08: 13 crates, 113 tests passing
- [x] AC-US2-09: Single binary build (~4.6MB)

### US-003: .NET Implementation (ccx-dotnet)

**As a** .NET developer,
**I want** a .NET 10 implementation of the AI coding assistant,
**So that** I can use it within the .NET ecosystem.

**Acceptance Criteria:**
- [x] AC-US3-01: Phase 1 API client with HttpClient streaming
- [x] AC-US3-02: Phase 1 tool system with interface-based dispatch
- [x] AC-US3-03: Phase 1 query engine structure
- [ ] AC-US3-04: Spectre.Console TUI (Phases 2-6)
- [ ] AC-US3-05: Full permission system (Phases 2-6)
- [ ] AC-US3-06: Context compaction (Phases 2-6)
- [ ] AC-US3-07: MCP client (Phases 2-6)
- [ ] AC-US3-08: All tests passing

### US-004: Python Implementation (ccx-py)

**As a** Python developer,
**I want** an async Python implementation with modern tooling,
**So that** I can use and extend the CLI in the Python ecosystem.

**Acceptance Criteria:**
- [x] AC-US4-01: Async API client (httpx) with SSE streaming parser
- [x] AC-US4-02: Tool system with ABC base and registry (7 tools)
- [x] AC-US4-03: Agentic query loop with asyncio.gather for parallel tools
- [x] AC-US4-04: Textual TUI with chat display, input, status bar
- [x] AC-US4-05: Permission system (4 modes, risk classifier, glob rules)
- [x] AC-US4-06: Context compaction (MicroCompact, AutoCompact)
- [x] AC-US4-07: MCP client (JSON-RPC over stdio)
- [x] AC-US4-08: Skill system (markdown loader, executor, trigger matching)
- [x] AC-US4-09: Hook system (pre/post tool, blocking via exit code 2)
- [x] AC-US4-10: 131 tests passing via pytest

### US-005: Umbrella Repository

**As a** project maintainer,
**I want** a central umbrella repo tracking all implementations,
**So that** progress, specs, and issues are coordinated across repos.

**Acceptance Criteria:**
- [x] AC-US5-01: SpecWeave initialized in ccx umbrella repo
- [x] AC-US5-02: All 4 child repos registered in config.json
- [x] AC-US5-03: GitHub sync profiles configured
- [x] AC-US5-04: Increment 0001 created tracking Phase 1 work
- [x] AC-US5-05: GitHub issues created for umbrella and per-repo tracking
