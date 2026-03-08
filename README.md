# LangGraph Agents Demo

A small, runnable LangGraph example with multiple agents:

- `planner` decides which specialist agents are needed
- `researcher` adds context notes
- `calculator` evaluates arithmetic expressions
- `writer` composes the final response

## Setup

```bash
python -m venv .venv
source .venv/bin/activate
pip install -r requirements.txt
```

## Run

```bash
python langgraph_agents_demo.py "What is LangGraph and what is 17 * 9?"
```

You can also run with no argument to use the default sample question.

## Run with AgentCore Locally

```bash
agentcore configure -e agentcore_app.py
agentcore dev
```

In another terminal:

```bash
curl -X POST http://localhost:8080/invocations \
  -H "Content-Type: application/json" \
  -d '{"prompt":"What is LangGraph and what is 17 * 9?"}'
```

## Deploy with AgentCore

```bash
agentcore launch
agentcore invoke '{"prompt":"What is LangGraph and what is 17 * 9?"}'
```

When you are done:

```bash
agentcore destroy
```
