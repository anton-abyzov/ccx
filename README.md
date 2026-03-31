# CCX

Community rewrites of an AI coding assistant CLI in Go, Rust, and .NET.

## Repositories

| Language | Repo | Binary Size | Key Feature |
|----------|------|-------------|-------------|
| Go | [ccx-go](https://github.com/anton-abyzov/ccx-go) | ~20-30MB | Goroutine agents, Bubbletea TUI |
| Rust | [ccx-rs](https://github.com/anton-abyzov/ccx-rs) | ~20MB | 5ms startup, OS-native sandbox, Codex crates |
| .NET | [ccx-dotnet](https://github.com/anton-abyzov/ccx-dotnet) | ~30-50MB | AOT compiled, enterprise-focused, Spectre.Console |

## Architecture

All three implementations share the same architecture based on analysis of a 512K-line TypeScript codebase:

- **Tool System**: Pluggable tools with permission gating
- **Agent Spawning**: Multi-agent orchestration with inter-agent messaging
- **TUI**: Rich terminal UI with markdown rendering and syntax highlighting
- **Context Management**: Multi-layer compression (micro, auto, session, full)
- **MCP Protocol**: Model Context Protocol for tool/resource discovery
- **Permission System**: Rule-based DSL with interactive prompts

## Status

All three implementations are in early development (Phase 1: Foundation).

## License

MIT (Go, .NET) | MIT + Apache-2.0 (Rust, for Codex-derived crates)
