# Plan — 0001-ccx-phase1-foundation

## Architecture Decision

### Multi-Language Approach

CCX implements the same AI coding assistant architecture across four languages, each leveraging its ecosystem's strengths:

| Language | HTTP | TUI | Async | Types | Testing |
|----------|------|-----|-------|-------|---------|
| **Go** | net/http | Bubble Tea | goroutines | structs | go test |
| **Rust** | reqwest | Ratatui | tokio | traits + enums | cargo test |
| **.NET** | HttpClient | Spectre.Console | async/await | interfaces | xUnit |
| **Python** | httpx | Textual | asyncio | Pydantic v2 | pytest |

### Core Components (all languages)

1. **API Client** — Streaming SSE connection to Claude Messages API
2. **Tool System** — Abstract tool interface with registry and dispatch
3. **Query Engine** — Agentic loop: stream → collect tool_use → execute parallel → repeat
4. **Agent System** — Sub-agent spawning as concurrent tasks
5. **TUI** — Full terminal UI (not just print statements)
6. **Permissions** — Risk classification with configurable modes
7. **Context Compaction** — Token estimation, truncation, and automatic compaction
8. **MCP** — JSON-RPC 2.0 over stdio for tool server integration
9. **Skills** — Markdown-based skill loading and execution
10. **Hooks** — Pre/post tool execution shell hooks

### Differentiation from Existing Projects

Each implementation is architecturally distinct from existing community projects:
- **Go**: vs claude-squad (multi-session manager) — ccx-go is a full single-session assistant
- **Rust**: vs claude-rs (API wrapper) — ccx-rs includes TUI, tools, agents, compaction
- **Python**: vs claw-code (metadata catalog) — ccx-py has real execution, async, Textual TUI
- **.NET**: no prior community implementation exists

### Implementation Strategy

1. **Parallel development** — All 4 languages built simultaneously by separate agents
2. **Spec-driven** — Same architectural spec, language-idiomatic implementations
3. **Test-first where possible** — Each language has its own test framework
4. **Binary outputs** — Go and Rust produce single binaries; Python and .NET use their package managers
