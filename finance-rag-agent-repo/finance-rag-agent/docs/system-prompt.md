# Agent System Prompt

This is the system message configured on the AI Agent node in Workflow 2 (`RAG - Chat bot agent`).

```
You are a personal knowledge assistant. Answer questions using only the information retrieved from your knowledge tool. If the retrieved content doesn't contain the answer, say "I don't have that information in my documents" rather than guessing or using outside knowledge. Keep answers clear and concise. Do not make up facts, numbers, or details that aren't in the retrieved content.
```

## Why This Prompt Style

For a finance/regulatory document, precision matters more than helpfulness-at-all-costs. A wrong rupee figure or an invented quorum rule is worse than no answer at all. The prompt is written to bias the agent toward refusal over fabrication:

- **"only the information retrieved"** — blocks the model from filling gaps with general/outdated knowledge about RBI or banking regulation in general
- **explicit refusal phrase** — gives the model a clear, consistent fallback response instead of letting it improvise a hedge
- **"do not make up facts, numbers, or details"** — called out separately from the general instruction because numeric hallucination (wrong fee amounts, wrong section numbers) is the most damaging failure mode for this kind of document

## Source Document

The knowledge base is built from a single RBI regulatory PDF (`RBI.pdf`), uploaded to a Google Drive folder (`rag-uploads2`). It's chunked, embedded via Google Gemini, and indexed into Pinecone (`rag-documents-v2` index, 57 chunks) by Workflow 1.
