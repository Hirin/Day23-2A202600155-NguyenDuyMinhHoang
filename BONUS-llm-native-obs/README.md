# BONUS B2: LLM Native Observability with Langfuse (+10 pts)

## Architecture

```
Qwen3.5-0.8B (base) + LoRA adapter
        |
   LangChain pipeline
        |
   Langfuse callback → Langfuse self-hosted (Docker)
```

## Setup

```bash
make up   # starts langfuse-web + langfuse-db

# Install deps (in venv)
uv pip install langchain langchain-huggingface langfuse peft transformers torch
```

## Run

```bash
# From BONUS-llm-native-obs/
python trace_router.py
```

This script:
1. Loads `unsloth/Qwen3.5-0.8B` base + your LoRA adapter from `../adapter/`
2. Creates a LangChain pipeline with the guardrail router system prompt
3. Runs 5 test queries (SAFE + HARMFUL + jailbreak)
4. Sends all traces to Langfuse via callback

## View Traces

1. Open http://localhost:3030
2. First run: sign up with any email (local, no verification needed)
3. Go to **Traces** — you will see 5 LLM traces
4. Click any trace to see full input/output/metadata

## What to screenshot

- Langfuse UI showing at least 1 LangChain LLM trace with input query + router output

## Langfuse credentials (local lab)

The script uses default `pk-lab` / `sk-lab` keys. These are auto-created on first request.
