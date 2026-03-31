# CCX -- Community Claude Code eXtended

Open-source, language-native reimplementations of Claude Code's AI coding assistant. Born from a source map leak, built by the community.

## Backstory

On March 31, 2026, security researcher Chaofan Shou ([@Fried_rice](https://x.com/Fried_rice/status/2038894956459290963)) discovered that Anthropic's npm package `@anthropic-ai/claude-code` shipped with a 57MB source map file (`cli.js.map`). The file contained the full, unobfuscated TypeScript source code -- 512,000 lines across 1,900+ files -- exposing the complete architecture of one of the most sophisticated AI coding tools ever built.

### What was found

The architecture analysis revealed:

- **43 built-in tools** -- file operations, code search, bash execution, web fetch, agent spawning, and more
- **4-layer context compression** -- micro, auto, session, and full compression to manage the 200K token window
- **Multi-agent orchestration** -- spawning sub-agents with isolated contexts, parallel execution, and channel-based communication
- **MCP protocol** -- Model Context Protocol client for extensible tool and resource discovery
- **Permission DSL** -- rule-based permission system with interactive approval flows and classifier
- **Hidden features** -- BUDDY AI pet, KAIROS daemon mode, Auto-Dream memory consolidation

Full analysis: [verified-skill.com/insights/claude-code](https://verified-skill.com/insights/claude-code)

### Why CCX exists

Rather than just archiving the leak, the community began building clean-room implementations in multiple languages. The goal: open-source, language-native alternatives that developers can own, extend, and deploy without dependency on a single vendor.

[instructkr/claw-code](https://github.com/instructkr/claw-code) (41.7k stars) took a Python metadata/harness approach -- wrapping Claude Code's interface. CCX takes a fundamentally different path: full working implementations with real tool execution, native TUIs, agent systems, and comprehensive test suites in each target language.

## Repositories

| Language | Repo | Binary Size | Stack |
|----------|------|-------------|-------|
| Go | [ccx-go](https://github.com/anton-abyzov/ccx-go) | ~20-30MB | Bubbletea TUI, goroutine agents, testify |
| Rust | [ccx-rs](https://github.com/anton-abyzov/ccx-rs) | ~20MB | Ratatui TUI, Codex crates, tokio async |
| .NET | [ccx-dotnet](https://github.com/anton-abyzov/ccx-dotnet) | ~30-50MB | Spectre.Console TUI, AOT compiled, xUnit |
| Python | [ccx-py](https://github.com/anton-abyzov/ccx-py) | ~50MB | Textual TUI, asyncio agents, pytest |

## Architecture Overview

All implementations share the same core architecture derived from the leaked source:

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

- Original tweet: https://x.com/Fried_rice/status/2038894956459290963
- Architecture analysis: https://verified-skill.com/insights/claude-code
- claw-code (Python wrapper): https://github.com/instructkr/claw-code

## License

MIT
