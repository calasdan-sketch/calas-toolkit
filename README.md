# Calas Toolkit — every repo on github.com/calasdan-sketch, and what it's for

Updated 2026-09-15. 46 repos: 4 built by Calas, 42 forks of open-source tools.
ALL 46 repos are now on Dan's PC (synced 2026-09-15): the 12 core ones under C:\Users\danie\my-agent\<name>, the other 34 as shallow copies under C:\Users\danie\my-agent\toolkit\<name>. Re-run C:\Users\danie\my-agent\toolkit-sync.cmd any time to pull new repos. Exception: searxng cannot be checked out on Windows (a filename with a colon) - run it in Docker from GitHub directly.
Rule for agents (Claude, Hermes, Jarvis): check this list BEFORE building anything new.
If a tool below already does the job, use it. Use the fork (calasdan-sketch/<name>) so
patches stay ours; run `git pull upstream` to pick up the original's updates.

## A. Calas products (ours)
| Repo | What it is | Status |
|---|---|---|
| calas-site | calasautomations.com — marketing site + On File demos (GitHub Pages) | LIVE |
| calas-reception | Cara, the AI phone receptionist: multi-tenant backend + ElevenLabs phone bridge | Code done; bridge not hosted yet |
| claude-bridge | Jarvis's brain — shared notes store all Claude surfaces read/write | Running on Dan's PC |
| shopify-autods-app | Dropship agent (Shopify + AutoDS + Claude) with mock mode | Waiting on AutoDS API |

## B. Agent brains & memory (run our bots)
| Repo | Plain-language purpose | Installed | Use it when |
|---|---|---|---|
| hermes-agent | The Hermes agent framework Calas ops run on (local Ollama) | yes (%LOCALAPPDATA%\hermes) | always — this is the ops runner |
| fullstack-agent | Jarvis's body: memory + voice + face + hands in one launcher | yes | starting Jarvis |
| backtalk | Jarvis's voice (speech in/out) | yes | Jarvis voice issues |
| barehands | Jarvis's "hands" (controls the PC) | yes | Jarvis needs to click/type |
| ai-visualizer | Jarvis's face/visual | yes | Jarvis GUI |
| mem0 | Long-term memory layer for agents | yes (not enabled) | when Hermes' built-in memory isn't enough |
| ai-memory-vault | Obsidian-style memory notes for AI | no | memory templates |
| OpenHands | Autonomous coding agent (does dev tasks itself) | no | offloading big code tasks locally |
| ruflo | Multi-agent swarm harness | no | orchestrating many agents at once |
| OpenBot | Agents that each get their own computer/browser | no | parallel browser workers |
| deepseek-harness | DeepSeek agent harness, plugin-based | no | alt agent runtime |
| glm-acp-agent | Agent using Zhipu GLM models | no | cheap alt model |
| claude-code-everything | Claude Code configs/skills collection | no | Claude Code tips |
| superpowers | Skills framework + dev methodology for agents | no | structuring agent skills |
| skills (Browserbase) | Web-access skills for agents | no | agents browsing the web |
| claude-skills | 200+ ready Claude skills (sales, marketing, eng) | no | need a skill fast |
| agent-prompts-library | Prompt library | no | writing agent prompts |
| i-have-adhd | Skill that keeps agent answers short and clear | no | Dan's "keep it short" rule |
| headroom | Compresses tool output before it hits the model (saves tokens) | no | cutting token spend |
| repomix | Packs a whole repo into one file for an AI to read | no | feeding a repo to a model |
| Local models: colibri, airllm | Run big models on small hardware | no | when 16GB VRAM is the limit |

## C. Customer-facing business tools (things we could host for clients)
| Repo | Plain-language purpose | Installed | Use it when |
|---|---|---|---|
| AIReceptionist | Self-hosted AI phone receptionist (OpenAI Realtime) | no | alt to ElevenLabs if we self-host Cara |
| agents (LiveKit) | Framework for realtime voice agents | no | building our own voice stack |
| chatwoot | Live chat + email support desk (like Intercom) | no | a client needs a support inbox/chat widget |
| libredesk | Lighter self-hosted support desk (single file) | yes | small client help desk |
| relaticle | Open-source CRM with AI agent hooks | no | replacing the artifact CRM with a real one |
| activepieces | Zapier-style automation builder (~400 connectors) | yes | client workflow automations without code |
| documenso | DocuSign alternative (e-sign) — AGPL, licence caveat | yes | On File needs signatures (check licence first) |
| uptime-kuma | Uptime monitor with alerts | yes | monitoring client sites/Cara |
| video-creator-agent (MoneyPrinterTurbo) | Auto-makes short videos from a topic | no | UGC/short-form content |
| PersonaLive | Animated talking portrait for live streams | no | avatar presenter |
| humanizer-agent / avoid-ai-writing | Make AI text sound human | no | outreach copy |
| ai-marketing-skills | Marketing skill pack | no | campaigns |
| MuMuAINovel | AI novel-writing assistant (Chinese) | no | — (low relevance) |

## D. Data, research & utilities
| Repo | Plain-language purpose | Installed | Use it when |
|---|---|---|---|
| crawl4ai | Web crawler/scraper built for LLMs | no (lib in ~/.crawl4ai) | scraping prospect sites |
| D4Vinci-Scrapling | Adaptive scraper that survives site changes | no | scraping that keeps breaking |
| searxng | Private meta-search engine | no | agents need search without API keys |
| markitdown | Converts PDFs/Office docs to Markdown | no | reading client documents |
| OpenSandbox | Secure sandbox runtime for agent code | no | running untrusted agent code |
| ShareX | Screenshots/screen recording | no | demo videos |
| timesfm | Google time-series forecasting model | no | trading/forecast experiments |
| daily_stock_analysis | LLM stock analysis dashboard w/ push alerts | no | trading desk |

## How to "wire in" a tool when needed
1. Clone the fork: `git clone https://github.com/calasdan-sketch/<name>` into C:\Users\danie\my-agent\
2. Read its README; most run with `docker compose up` or `npm/uv run`.
3. Add a line to Hermes' CLAUDE-CONTEXT.md saying it's installed and what it's for.
4. Never expose a client-facing tool without: uptime monitor (uptime-kuma), a backup, and a licence check (AGPL tools like documenso/backtalk need care when clients use them directly).
