# LangGraph Tutorial: Beginner to Advanced

Welcome! This is a self-contained tutorial for [LangGraph](https://langchain-ai.github.io/langgraph/), the
graph-based framework for building stateful, multi-step LLM applications and agents.

It is written against the code in this repository — in particular `langgraph_agents_demo.py`
(planner → researcher/calculator → writer) — so every concept has a working example you can actually run
with `python langgraph_agents_demo.py "..."`.

## Who this is for

You should know basic Python and have used an LLM API before (OpenAI, Anthropic, Ollama, etc.). No prior
LangGraph or LangChain experience is assumed.

## How the tutorial is organized

The chapters build on each other. Each one introduces one or two new ideas and ends with a small runnable
example.

| # | Chapter | You'll learn |
|---|---------|---------------|
| 1 | [Getting Started](01-getting-started.md) | Install LangGraph, build and run your first graph |
| 2 | [Core Concepts](02-core-concepts.md) | `State`, nodes, edges, reducers, `StateGraph`, compiling |
| 3 | [Conditional Routing](03-conditional-routing.md) | Branching logic, routers, loops — the "planner" pattern |
| 4 | [Tools & Agents](04-tools-and-agents.md) | Tool calling, `ToolNode`, the ReAct loop, `create_react_agent` |
| 5 | [Memory & Persistence](05-memory-and-persistence.md) | Checkpointers, threads, time travel, human-in-the-loop |
| 6 | [Multi-Agent Systems](06-multi-agent-systems.md) | Supervisor pattern, subgraphs, the repo's planner/researcher/calculator/writer graph |
| 7 | [Streaming](07-streaming.md) | Streaming state updates, LLM tokens, and custom events |
| 8 | [Advanced Patterns](08-advanced-patterns.md) | Fan-out/fan-in, custom reducers, retries, error handling |
| 9 | [Deployment](09-deployment.md) | Packaging a graph as a service, and deploying it with Bedrock AgentCore |
| 10 | [Best Practices](10-best-practices.md) | Testing, debugging, project structure, LangGraph Studio |

## Prerequisites for running the examples

```bash
python -m venv .venv
source .venv/bin/activate
pip install -r requirements.txt
```

`requirements.txt` in this repo already pins `langgraph`. Some tutorial snippets also use `langchain-openai`
or `langgraph-checkpoint-sqlite` — install those only if you want to run that specific snippet locally.

## Quick orientation: what is LangGraph?

LangGraph models an application as a **graph**:

- **State** — a shared, typed object that flows through the graph and gets updated as it goes.
- **Nodes** — plain Python functions (or callables) that receive the state and return a partial update.
- **Edges** — the connections between nodes, including conditional ("if/else") edges that pick the next
  node at runtime.

Compiling the graph produces a runnable object with the same interface as any LangChain `Runnable`:
`.invoke()`, `.stream()`, `.ainvoke()`, `.astream()`.

Ready? Start with [Chapter 1 — Getting Started](01-getting-started.md).
