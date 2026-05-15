# proxima-mcp-setup
Proxima MCP wired into Claude Code — ask_all_ais across ChatGPT+Claude+Gemini+Perplexity, 45+ tools, zero API costs

![Node](https://img.shields.io/badge/Node.js-MCP_Server-339933?style=flat&labelColor=555&logo=nodedotjs)
![Claude](https://img.shields.io/badge/Claude-Code-cc785c?style=flat&labelColor=555)
![ChatGPT](https://img.shields.io/badge/ChatGPT-Free_Web-74aa9c?style=flat&labelColor=555)
![Gemini](https://img.shields.io/badge/Gemini-Free_Web-4285F4?style=flat&labelColor=555)
![Perplexity](https://img.shields.io/badge/Perplexity-Search-20808D?style=flat&labelColor=555)
![Status](https://img.shields.io/badge/Status-Active-brightgreen?style=flat&labelColor=555)

[Concepts](#-concepts) · [How It Works](#️-how-it-works) · [Install](#-install) · [Tools](#-tool-list) · [Tips](#-tips-and-tricks-10) · [Startups](#️-startups--businesses)

---

## 🧠 CONCEPTS

| Feature | Location | Description |
|---------|----------|-------------|
| [**ask_all_ais**](src/mcp-server-v3.js) | MCP tool | Same prompt → ChatGPT+Claude+Gemini+Perplexity simultaneously |
| [**compare_ais**](src/mcp-server-v3.js) | MCP tool | Side-by-side model comparison with scoring |
| [**smart_query**](src/mcp-server-v3.js) | MCP tool | Auto-routes to best model based on query type |
| [**ask_perplexity**](src/mcp-server-v3.js) | MCP tool | Real-time web search via Perplexity AI |
| [**Zero API Cost**](src/mcp-server-v3.js) | Architecture | Uses web sessions, not paid APIs |
| [**45+ Tools**](src/tools/) | `src/tools/` | Search, analyze, code, explain, compare, fact-check |

### 🔥 Hot

| Feature | Location | Description |
|---------|----------|-------------|
| [**ask_all_ais**](src/mcp-server-v3.js) | One call | Fire all 4 AIs in parallel — get 4 perspectives instantly |
| [**Zero cost**](src/mcp-server-v3.js) | Web sessions | Uses browser sessions not API keys — GPT-4o free tier |
| [**45 tools**](src/tools/) | All tools | internet_search, code review, fact_check, summarize, generate — all free |

---

## ⚙️ HOW IT WORKS

```
Claude Code → MCP call: ask_all_ais("your question")
         ↓
Proxima MCP Server (port 19222 relay)
         ↓
Fires simultaneously:
  ├── ChatGPT (GPT-4o via web session)
  ├── Claude (claude.ai via web session)
  ├── Gemini (gemini.google.com via web session)
  └── Perplexity (with web search)
         ↓
Responses aggregated → returned to Claude Code
```

> ⚠️ Full execution: Agent Hub on port 19222 (Windows Electron).
> macOS: MCP server wired, tools visible — IPC relay needs hub running.

---

## 🚀 INSTALL

```bash
git clone https://github.com/hmzainjamil/proxima-mcp-setup
cd proxima-mcp-setup
npm install
```

**Wire to Claude Code** — add to `~/.mcp.json`:
```json
{
  "mcpServers": {
    "proxima": {
      "command": "node",
      "args": ["/path/to/proxima-mcp-setup/src/mcp-server-v3.js"]
    }
  }
}
```

---

## 🛠 TOOL LIST

| Tool | Use Case |
|---|---|
| `ask_all_ais` | All 4 AIs simultaneously |
| `ask_chatgpt` | ChatGPT only |
| `ask_gemini` | Gemini only |
| `ask_perplexity` | Perplexity web search |
| `compare_ais` | Side-by-side comparison |
| `smart_query` | Auto-route to best model |
| `internet_search` | Real-time web search |
| `fact_check` | Verify claims across sources |
| `summarize_url` | Summarize any URL |
| `generate_code` | Code gen across models |
| `explain_code` | Code explanation |
| `review_code` | Code review |
| `fix_error` | Error debugging |
| `deep_search` | Multi-source deep research |

---

## 💡 TIPS AND TRICKS (10)

[usage](#tips-usage) · [models](#tips-models) · [search](#tips-search) · [workflow](#tips-workflow)

<a id="tips-usage"></a>■ **Usage (3)**

| Tip | Source |
|-----|--------|
| `ask_all_ais` for important decisions — 4 independent perspectives catch what 1 misses | [HMZ](https://github.com/hmzainjamil) |
| `smart_query` for code → routes to ChatGPT/Claude; for facts → routes to Perplexity | [DigiMinds](https://github.com/hmzainjamil) |
| `compare_ais` for research — shows which model is most confident on a topic | [HMZ](https://github.com/hmzainjamil) |

<a id="tips-models"></a>■ **Model Strengths (3)**

| Tip | Source |
|-----|--------|
| ChatGPT best for code + creative writing; Claude best for reasoning + long context | [HMZ](https://github.com/hmzainjamil) |
| Gemini best for recent events + Google data; Perplexity best for real-time web facts | [DigiMinds](https://github.com/hmzainjamil) |
| Disagreement between models = uncertainty signal — research further before deciding | [HMZ](https://github.com/hmzainjamil) |

<a id="tips-search"></a>■ **Search (2)**

| Tip | Source |
|-----|--------|
| `ask_perplexity` for anything time-sensitive — it cites sources, others hallucinate dates | [HMZ](https://github.com/hmzainjamil) |
| `deep_search` for competitive intel — multi-source synthesis beats single search | [DigiMinds](https://github.com/hmzainjamil) |

<a id="tips-workflow"></a>■ **Workflow (2)**

| Tip | Source |
|-----|--------|
| Chain: `deep_search` → `fact_check` → `summarize_url` for research pipeline | [HMZ](https://github.com/hmzainjamil) |
| Wire Proxima + MAE: `mae run` passes sub-tasks to Proxima for multi-model validation | [DigiMinds](https://github.com/hmzainjamil) |

---

## ☠️ STARTUPS / BUSINESSES

| This Repo / Feature | Replaced |
|-|-|
| **ask_all_ais (multi-model)** | [OpenRouter](https://openrouter.ai), [RouteLLM](https://github.com/lm-sys/RouteLLM), [LiteLLM](https://litellm.ai) |
| **Zero-cost web AI** | [Claude API](https://anthropic.com), [OpenAI API](https://openai.com), [Gemini API](https://ai.google.dev) — paid |
| **45 MCP tools** | [Zapier AI](https://zapier.com/ai), [Make.com AI](https://make.com) — paid automation |
| **Real-time Perplexity search** | [Tavily](https://tavily.com), [Serper](https://serper.dev), [SerpAPI](https://serpapi.com) |

---

## Star History

[![Star History Chart](https://api.star-history.com/svg?repos=hmzainjamil/proxima-mcp-setup&type=Date)](https://star-history.com/#hmzainjamil/proxima-mcp-setup&Date)

---

<div align="center">
Built by <a href="https://github.com/hmzainjamil">HMZ</a> · Multi-model AI at zero API cost
</div>
