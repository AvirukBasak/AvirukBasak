# LLM Model Decision Table
> **One-glance guide** · Standard agent workload (JSON/XML/YAML output) · Prices = input / output per million tokens · March 2026

---

## How to use
Find your **primary constraint** in the left column → check whether cost sensitivity is High / Low → pick the model in the ✅ column.

---

| # | Primary Need | Cost Sensitivity | ✅ Best Pick | 💰 $/M in · out | 🥈 Runner-Up | 💰 $/M in · out | Decisive Factor |
|---|---|:---:|---|:---:|---|:---:|---|
| 1 | **Pure cost minimum** — routing, classification, simple extraction | 🔴 Critical | GPT-4.1 Nano | $0.10 · $0.40 | Gemini 2.5 Flash-Lite | $0.10 · $0.40 | Both tied at $0.10 in; Nano wins on instruction-following accuracy |
| 2 | **Pure cost minimum** — off-hours batch jobs | 🔴 Critical | DeepSeek V3 | $0.07 · $0.55 ¹ | GPT-4.1 Nano (batch) | $0.05 · $0.20 ² | DeepSeek off-peak 50% disc + $0.028/M cache hit; OpenAI batch 50% |
| 3 | **Coding** — production bug fixes, PRs, diffs | 🟡 Medium | Claude Haiku 4.5 | $1.00 · $5.00 | GPT-5.4 Nano | $0.20 · $1.25 | Haiku 73.3% SWE-bench; 5.4 Nano 52.4% at 5× cheaper |
| 4 | **Coding** — budget-constrained pipelines | 🔴 Critical | GPT-5.4 Nano | $0.20 · $1.25 | Gemini 2.5 Flash-Lite | $0.10 · $0.40 | 5.4 Nano leads on actual code gen; Flash-Lite best if cost is hard cap |
| 5 | **Reasoning** — multi-step logic, science, math | 🟡 Medium | DeepSeek V3 | $0.27 · $1.10 | Claude Haiku 4.5 | $1.00 · $5.00 | DeepSeek 80.7% GPQA Diamond; Haiku adds extended thinking |
| 6 | **Reasoning** — cost no object, hardest tasks | 🟢 Low | Claude Sonnet 4.6 | $3.00 · $15.00 | GPT-5 | $1.25 · $10.00 | Sonnet best overall agent quality; GPT-5 closer on reasoning tasks |
| 7 | **Low latency** — real-time chat, streaming UI | 🔴 Critical | Gemini 2.0 Flash | $0.10 · $0.40 | Gemini 2.5 Flash-Lite | $0.10 · $0.40 | Both <0.5s TTFT, 200+ t/s; Flash-Lite adds thinking when needed |
| 8 | **Low latency** — quality matters too | 🟡 Medium | GPT-5.4 Nano | $0.20 · $1.25 | Claude Haiku 4.5 | $1.00 · $5.00 | Sub-1s TTFT, high t/s, strong quality; Haiku if tool use is complex |
| 9 | **Customer support** — scripted FAQ, ticket triage | 🔴 Critical | GPT-4.1 Nano | $0.10 · $0.40 | Gemini 2.5 Flash-Lite | $0.10 · $0.40 | Best instruction-following at floor price; Flash-Lite for multimodal tickets |
| 10 | **Customer support** — nuanced, empathetic replies | 🟡 Medium | Claude Haiku 4.5 | $1.00 · $5.00 | GPT-5.4 Nano | $0.20 · $1.25 | Haiku leads on tone/context coherence across long conversations |
| 11 | **Summarization** — short docs, meeting notes | 🔴 Critical | Gemini 2.5 Flash-Lite | $0.10 · $0.40 | GPT-4.1 Nano | $0.10 · $0.40 | Flash-Lite wins on factual grounding + 64K output ceiling |
| 12 | **Summarization** — long reports, books, codebases | 🟡 Medium | Gemini 2.5 Flash | $0.30 · $2.50 | Claude Haiku 4.5 | $1.00 · $5.00 | Flash handles full 1M context with grounding; Haiku for higher fidelity |
| 13 | **Long context** — RAG, retrieval over large corpora | 🔴 Critical | GPT-4.1 Nano | $0.10 · $0.40 | Gemini 2.0 Flash | $0.10 · $0.40 | Both 1M tokens at floor price; Nano stronger retrieval accuracy |
| 14 | **Long context** — live search + grounding needed | 🟡 Medium | Gemini 2.5 Flash | $0.30 · $2.50 | Gemini 2.5 Pro | $1.25 · $10.00 | Native Google Search grounding; Pro for the most complex retrieval |
| 15 | **Long context** — confidential / on-premises | Any | DeepSeek V3 ³ | self-host | — | — | Only MIT open-weights model in this set; needs 8× H200 GPUs |
| 16 | **Multimodal** — image + text pipelines | 🔴 Critical | Gemini 2.5 Flash-Lite | $0.10 · $0.40 | Gemini 2.0 Flash | $0.10 · $0.40 | Both vision+audio+video at floor price; Flash-Lite has better reasoning |
| 17 | **Multimodal** — video understanding, live audio | 🟡 Medium | Gemini 2.5 Flash | $0.30 · $2.50 | Gemini 2.5 Pro | $1.25 · $10.00 | Best native video/audio; Pro when accuracy is paramount |
| 18 | **Agentic orchestration** — tool chains, sub-agents | 🟡 Medium | Claude Haiku 4.5 | $1.00 · $5.00 | GPT-5.4 Nano | $0.20 · $1.25 | Haiku has deepest tool/computer-use integration; 5.4 Nano 5× cheaper |
| 19 | **Agentic orchestration** — flagship quality | 🟢 Low | Claude Sonnet 4.6 | $3.00 · $15.00 | GPT-5.4 | $2.50 · $15.00 | Sonnet best-in-class agentic loops; GPT-5.4 strong on code-heavy agents |

---

## Full price reference

| Model | Provider | Input $/M | Output $/M | Context | Tier |
|---|---|:---:|:---:|:---:|:---:|
| GPT-4.1 Nano | OpenAI | $0.10 | $0.40 | 1M | Budget |
| Gemini 2.0 Flash | Google | $0.10 | $0.40 | 1M | Budget |
| Gemini 2.5 Flash-Lite | Google | $0.10 | $0.40 | 1M | Budget |
| GPT-5.4 Nano | OpenAI | $0.20 | $1.25 | 400K | Budget |
| DeepSeek V3 | DeepSeek | $0.27 | $1.10 | 128K | Budget |
| Gemini 2.5 Flash | Google | $0.30 | $2.50 | 1M | Mid |
| Claude Haiku 4.5 | Anthropic | $1.00 | $5.00 | 200K | Mid |
| GPT-5 | OpenAI | $1.25 | $10.00 | 1M | Mid |
| Gemini 2.5 Pro | Google | $1.25 | $10.00 | 1M | Mid |
| GPT-5.4 | OpenAI | $2.50 | $15.00 | 1.05M | Flagship |
| Claude Sonnet 4.6 | Anthropic | $3.00 | $15.00 | 1M | Flagship |
| Claude Opus 4.6 | Anthropic | $5.00 | $25.00 | 1M | Flagship |

---

## Footnotes
¹ DeepSeek V3 off-peak discount (50%); standard price $0.27 · $1.10  
² OpenAI Batch API 50% discount on GPT-4.1 Nano  
³ DeepSeek V3 MIT open weights; self-host on 8× H200 for zero API cost at scale  

> Prices exclude prompt caching discounts (up to 90% on cache hits for Anthropic; $0.028/M for DeepSeek).  
> Context pricing surcharges: Gemini 2.5 Pro and Claude models 2× after 200K tokens.
