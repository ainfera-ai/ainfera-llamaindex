# ainfera-llamaindex — LlamaIndex + Ainfera Routing

**LlamaIndex integration + Ainfera Routing.** RAG pipelines, agents, and workflows — inference routed through Ainfera with signed audit per turn.

**GTM publish-only** companion repo (minimal SDK sample + curl). Production LlamaIndex apps point `OpenAI`-compatible settings at Ainfera the same way.

## Quickstart (curl only)

```bash
git clone https://github.com/ainfera-ai/ainfera-llamaindex
cd ainfera-llamaindex
./curl-example.sh   # signup → inference → audit verify
```

## Quickstart (OpenAI SDK — same transport LlamaIndex uses)

```bash
pip install -r requirements.txt
export AINFERA_API_KEY=ai_infera_...  # https://app.ainfera.ai/signup
python main.py
```

## LlamaIndex + Ainfera

Point LlamaIndex’s OpenAI-compatible LLM at Ainfera (exact class names vary by LlamaIndex release). The reliable pattern is environment variables consumed by LlamaIndex and the upstream OpenAI client:

```bash
export OPENAI_API_KEY="$AINFERA_API_KEY"
export OPENAI_BASE_URL="https://api.ainfera.ai/v1"
```

Alternatively set `api_key` and base URL (`api_base` / `azure_endpoint` equivalents depend on version) on your chosen `OpenAI` LLM wrapper from `llama_index.*` — mirror `python main.py`, which uses the official OpenAI SDK with `base_url="https://api.ainfera.ai/v1"`.

## What this shows

- One Agent Card across providers (L1)
- Routed inference with per-call budget caps (L3)
- Hash-chained receipts per LLM turn (L4)

## Other frameworks

- [ainfera-letta](https://github.com/ainfera-ai/ainfera-letta) — Letta + memory blocks
- [ainfera-langgraph](https://github.com/ainfera-ai/ainfera-langgraph) — LangGraph
- [ainfera-mcp](https://github.com/ainfera-ai/ainfera-mcp) — Claude Desktop + Cursor
- [ainfera-openai-compatible](https://github.com/ainfera-ai/ainfera-openai-compatible) — universal wedge

Apache 2.0. © Ainfera Inc. 2026.
