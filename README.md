<div align="center">

# proxima-mcp-setup

![Version](https://img.shields.io/badge/version-4.1.0-blue?style=flat)
![Platform](https://img.shields.io/badge/platform-macOS%20%7C%20Windows-lightgrey?style=flat)
![MCP](https://img.shields.io/badge/MCP-enabled-green?style=flat)
![Models](https://img.shields.io/badge/models-ChatGPT%20%7C%20Claude%20%7C%20Gemini%20%7C%20Perplexity-orange?style=flat)
![Cost](https://img.shields.io/badge/API%20cost-zero-brightgreen?style=flat)

**Ask all 4 AI models simultaneously — zero API keys, zero cost.**
Proxima MCP server bridges Claude Code to ChatGPT, Claude, Gemini, and Perplexity via an IPC relay.

</div>

---

## What is Proxima?

| Feature | Detail |
|---|---|
| **Tool count** | 45+ MCP tools |
| **Models** | ChatGPT, Claude, Gemini, Perplexity — all 4 simultaneously |
| **API cost** | Zero — uses browser sessions, no API keys |
| **Protocol** | MCP (Model Context Protocol) via stdio |
| **Transport** | IPC bridge to Electron Agent Hub on port 19222 |
| **macOS** | MCP server runs; Electron GUI is Windows-only |

## 🔥 Hot — Key Tools

| Tool | What it does |
|---|---|
| `ask_all_ais` | Fire the same prompt at all 4 models simultaneously |
| `compare_ais` | Get side-by-side comparison of model answers |
| `smart_query` | Auto-route to best model based on query type |
| `ask_chatgpt` | Direct ChatGPT query |
| `ask_claude` | Direct Claude query |
| `ask_gemini` | Direct Gemini query |
| `ask_perplexity` | Direct Perplexity query (real-time web) |

## Installation

```bash
# Clone
git clone https://github.com/Zen4-bit/Proxima ~/installed-repos/Proxima
cd ~/installed-repos/Proxima
npm install

# Wire to Claude Code
# Add to ~/.mcp.json:
```

```json
{
  "mcpServers": {
    "proxima": {
      "command": "/path/to/node",
      "args": ["/Users/YOU/installed-repos/Proxima/src/mcp-server-v3.js"],
      "type": "stdio",
      "env": {
        "AGENT_HUB_PORT": "19222",
        "PATH": "/path/to/nvm/bin:/opt/homebrew/bin:/usr/local/bin:/usr/bin:/bin"
      }
    }
  }
}
```

## macOS Notes

```
⚠️  Electron GUI = Windows only
✅  MCP server (mcp-server-v3.js) = works on macOS
⚠️  Full tool execution requires Agent Hub on port 19222
✅  Wire to .mcp.json and Claude Code will show 45+ Proxima tools
```

## Auto-activation Keywords

Skill `skill-auto-activate` fires Proxima docs on:
`proxima` · `ask all ais` · `compare ais` · `smart query` · `ask_all_ais` · `compare_ais` · `multi model mcp`

## ■ tip

> Run `node ~/installed-repos/Proxima/src/mcp-server-v3.js` standalone to verify the MCP server starts.
> On macOS you'll see it waiting for IPC — that's correct behavior without the Electron hub.

---

## ☠️ BUSINESSES / AGENCIES

**DigiMinds Global** uses Proxima to compare AI outputs for ad copy, strategy, and research tasks.
Zero-cost multi-model consensus = better decisions, no API spend.

---

*Part of [hmzainjamil/claude-ai-system](https://github.com/hmzainjamil/claude-ai-system) — DigiMinds AI automation stack*
