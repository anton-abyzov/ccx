# CCX -- Community Claude Code eXtended

Open-source, language-native AI coding assistant implementations. Community-built alternatives to proprietary tools.

## About

CCX is a family of clean-room AI coding assistant implementations, built as open-source alternatives to proprietary tools. Each implementation is designed from the ground up using publicly documented API specifications and common patterns in AI-assisted development.

### Architecture

The implementations share a common architecture inspired by analysis of Claude Code's design patterns:

- **43 built-in tools** -- file operations, code search, bash execution, web fetch, agent spawning, and more
- **4-layer context compression** -- micro, auto, session, and full compression to manage the 200K token window
- **Multi-agent orchestration** -- spawning sub-agents with isolated contexts, parallel execution, and channel-based communication
- **MCP protocol** -- Model Context Protocol client for extensible tool and resource discovery
- **Permission DSL** -- rule-based permission system with interactive approval flows and classifier

Full analysis: [verified-skill.com/insights/claude-code](https://verified-skill.com/insights/claude-code)

### Why CCX exists

The goal: open-source, language-native alternatives that developers can own, extend, and deploy without dependency on a single vendor.

[instructkr/claw-code](https://github.com/instructkr/claw-code) (41.7k stars) took a Python metadata/harness approach -- wrapping Claude Code's interface. CCX takes a fundamentally different path: full working implementations with real tool execution, native TUIs, agent systems, and comprehensive test suites in each target language.

## Repositories

| Language | Repo | Binary Size | Stack |
|----------|------|-------------|-------|
| Go | [ccx-go](https://github.com/anton-abyzov/ccx-go) | ~20-30MB | Bubbletea TUI, goroutine agents, testify |
| Rust | [ccx-rs](https://github.com/anton-abyzov/ccx-rs) | ~20MB | Ratatui TUI, Codex crates, tokio async |
| .NET | [ccx-dotnet](https://github.com/anton-abyzov/ccx-dotnet) | ~30-50MB | Spectre.Console TUI, AOT compiled, xUnit |
| Python | [ccx-py](https://github.com/anton-abyzov/ccx-py) | ~50MB | Textual TUI, asyncio agents, pytest |

## Architecture Overview

All implementations share a common architecture based on publicly documented patterns:

```
┌─────────────────────────────────────────────┐
│                  CLI / TUI                   │
├─────────────────────────────────────────────┤
│              Core Agent Loop                 │
│  ┌─────────┐  ┌──────────┐  ┌───────────┐  │
│  │ Streaming│  │  Tool    │  │  Agent    │  │
│  │ API      │  │  System  │  │  Spawning │  │
│  └─────────┘  └──────────┘  └───────────┘  │
├─────────────────────────────────────────────┤
│  ┌─────────┐  ┌──────────┐  ┌───────────┐  │
│  │ Context  │  │Permission│  │   MCP     │  │
│  │ Compress │  │  DSL     │  │  Protocol │  │
│  └─────────┘  └──────────┘  └───────────┘  │
├─────────────────────────────────────────────┤
│  ┌─────────┐  ┌──────────┐  ┌───────────┐  │
│  │ Memory  │  │  Skill   │  │  Config   │  │
│  │ System  │  │  Loader  │  │  Cascade  │  │
│  └─────────┘  └──────────┘  └───────────┘  │
└─────────────────────────────────────────────┘
```

### Shared components across all implementations

- **Tool System**: Pluggable tool interface with permission gating and concurrent execution (43 tools)
- **Agent Spawning**: Sub-agent orchestration with isolated contexts and inter-agent communication
- **Context Compression**: 4-layer compression (micro, auto, session, full) for token management
- **MCP Client**: Model Context Protocol for extensible tool/resource discovery
- **Permission System**: Rule-based DSL with interactive approval and risk classification
- **Memory Persistence**: User, project, feedback, and reference memory types
- **Streaming API**: SSE-based streaming from Claude API with tool_use protocol handling

## Status

| Feature | Go | Rust | .NET | Python |
|---------|:--:|:----:|:----:|:------:|
| Project scaffolding | Done | Done | Done | In progress |
| Claude API streaming | Done | Done | Done | In progress |
| Tool system (43 tools) | Done | Done | Done | Planned |
| TUI | Done | Done | Done | Planned |
| Agent spawning | Done | Done | Done | Planned |
| Context compression | Done | Done | Done | Planned |
| MCP protocol | Done | Done | Done | Planned |
| Permission DSL | Done | Done | Done | Planned |
| Memory system | Done | Done | Done | Planned |
| Test suite | Done | Done | Done | Planned |

## Links

- Architecture analysis: https://verified-skill.com/insights/claude-code
- claw-code (Python wrapper): https://github.com/instructkr/claw-code

## License

MIT
