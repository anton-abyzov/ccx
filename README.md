# CCX -- Community Code Extended

Open-source, language-native AI coding assistant implementations. Community-built alternatives to proprietary tools.

![CCX-RS Terminal UI](https://raw.githubusercontent.com/anton-abyzov/ccx-rs/main/assets/screenshot.png)

## About

CCX (Community Code Extended) is a custom AI coding assistant built from the ground up. Each implementation is designed independently using publicly documented API specifications and common patterns in AI-assisted development. While inspired by the general category of AI coding CLIs, CCX is its own application with independent architecture decisions, native implementations, and language-idiomatic designs.

The project spans four languages -- Go, Rust, .NET, and Python -- each providing a fully functional CLI with tool execution, terminal UI, agent orchestration, and extensibility via MCP. The implementations are independent but share the same architectural blueprint, allowing developers to pick the stack they know best.

### Architecture

All implementations share a common architecture with these core subsystems:

- **43 built-in tools** -- file operations (read, write, edit), code search (glob, grep), bash execution, web fetch, agent spawning, notebook editing, and more
- **4-layer context compression** -- micro (truncate tool results), auto (threshold-based), session (manual), and full compression to manage the 200K token window efficiently
- **Multi-agent orchestration** -- spawning sub-agents with isolated contexts, parallel execution, channel-based communication, foreground/background modes, and named agent addressing
- **MCP protocol** -- Model Context Protocol client for extensible tool and resource discovery via JSON-RPC over stdio/SSE
- **Permission DSL** -- rule-based permission system with glob patterns, risk classification (safe/low/medium/high), interactive approval flows, and configurable modes (default, plan, bypass, acceptEdits, auto)
- **Streaming API** -- Server-Sent Events (SSE) parsing for real-time Claude API responses with tool_use protocol handling
- **Memory system** -- persistent user, project, feedback, and reference memories stored as markdown files with YAML frontmatter
- **Skill system** -- markdown-based skill definitions with trigger matching, activation/deactivation, and inline or agent-forked execution
- **Hook system** -- pre/post tool execution hooks with shell commands, environment variable injection, and blocking via exit codes
- **Config cascade** -- settings resolution from CLI flags > session > project > user > defaults, with CLAUDE.md discovery

Full analysis: [verified-skill.com/insights/claude-code](https://verified-skill.com/insights/claude-code)

### Why CCX exists

The goal: open-source, language-native alternatives that developers can own, extend, and deploy without dependency on a single vendor.

[instructkr/claw-code](https://github.com/instructkr/claw-code) (41.7k stars) took a Python metadata/harness approach -- wrapping the interface and cataloging tool inventories as structured data without actual execution. CCX (Community Code Extended) takes a fundamentally different path: full working implementations with real tool execution, native TUIs, agent systems, and comprehensive test suites in each target language.

## Repositories

| Language | Repo | Binary Size | Crates/Packages | Stack |
|----------|------|-------------|-----------------|-------|
| Rust | [ccx-rs](https://github.com/anton-abyzov/ccx-rs) | ~4.7MB | 14 crates | Ratatui TUI, tokio async, 11 tools |
| Go | [ccx-go](https://github.com/anton-abyzov/ccx-go) | ~20-30MB | -- | Bubbletea TUI, goroutine agents, testify |
| .NET | [ccx-dotnet](https://github.com/anton-abyzov/ccx-dotnet) | ~30-50MB | -- | Spectre.Console TUI, AOT compiled, xUnit |
| Python | [ccx-py](https://github.com/anton-abyzov/ccx-py) | ~50MB | -- | Textual TUI, asyncio agents, pytest |

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
