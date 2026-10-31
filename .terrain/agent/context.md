---
type: agent_context
project: terrain
title: Agent Architecture Context
source: .
---

## Project Overview
`,
 `
## Architecture
`,
 `
## Module Map
`,
 `
## Core Flows
`,
 `
## Tech Stack
`,
 `
## System Boundaries
`,
 `
## Code Map Index
`.

Also

 preserve


 the

 diagram

 (ASCII),
 translated
 labels.


 Diagram

 content


 translation
 is
 allowed

 (
"diagram
 labels
 must
 all use

 this
 language
").


 I


 must
 keep
 the

 diagram's
 shape
.

Let me
 now


 also
 double

-check


 one


 thing
:

 the
 overview


 says


 "consum
ers... and external
 Agents
 connected
 via
 ACP
 subprocess" 
— unchanged
.


 Als

…
## Module
Map

 —

 table

 with

 rows
 (translate
 all

;
 terrain
-agent

 row
 gains 



"
model

catalog/provider

resolution

 (LlmProvider
)")
## Core
Flows
 — 4
 numbered
 flows
 with
 bold
 titles
.
## Tech
Stack


 — bullets
.
## System
Boundaries
 — table

 +
 trust
 rules
 paragraph
.
## Code
Map
 Index
 — table
.


 Now

 let


 me


 count


 characters


 roughly
.


 I'll


 write


 it,
 then
 estimate

:
 the
 
ASCII
 
diagram

 ~1700
 chars
.
 Tables
: layer
 
table

 ~450
, module
 map
 
~1200
,
 boundaries
 
~1500
,
 code
 map
 
~1700
.
 Flows


 ~2800
.
 Overview
 ~1100
.
 Tech
 stack

 ~1100
 
. Trust
 paragraph

 ~900
.
 Total


 ~
13
,
5
00
.
 Tight
 but
 OK
.


 I


…
## Project Overview
Terrain is an **engineering-environment platform for coding agents** (Sopaco open-source; source packing driven by repomix-rs). Tagline: *"Terrain lays the ground so agents never have to guess where to stand."* Pointed at a Git repo, it scans code, packs sources (repomix), generates Agent context, C4 architecture docs (Litho), dual-track knowledge (`human/` + `agent/`), and knowledge-freshn

…
## Architecture
```
┌───────────────────────────────────────────────────────────────┐
│ Svelte 5 frontend (src/)        Tauri 2 shell (src-tauri/)    │
│  Ask/DeepWiki · SDD · Litho · Env · Projects · Usage · Tray   │
└───────────────┬───────────────────────────────────────────────┘
                │ invoke + streaming events (ts-rs; Rust is IPC truth)
┌───────────────▼─────────────────────────────────────

…
## Module Map
| Module | Responsibility | Main paths |
|--------|----------------|------------|
| terrain-core | Domain core: asset generation, three-tier retrieval, freshness, ingest, registry, IPC types | `crates/terrain-core/src/` |
| assets/ | repomix pack, agent context, Litho/SDD/Ask assets, incremental refresh, env integration | `crates/terrain-core/src/assets/` |
| freshness | Git + CodeGraph dri

…
## Core Flows
**1. Project registration → knowledge asset generation**
1. `initialize_project` registers the repo into `~/.terrain/registry.json` (path pointer only).
2. `ProjectScanner` collects Git metadata; optional OpenAPI import (`scan_project`).
3. repomix-core packs sources → `.terrain/agent/repomix.md` (`pack_agent_assets`).
4. LLM generates `agent/context.md`; the optional Litho four-phase run p

…
## Tech Stack
- **Rust**: workspace (terrain-core, terrain-agent, terrain-cli, terrain-ts-export, src-tauri), edition 2024, rust-version 1.94
- **Desktop shell**: Tauri 2 (capabilities ACL, plugin-dialog/shell, tray + Usage window)
- **Frontend**: Svelte 5 (runes) + Vite 8 + Tailwind 4 + marked/mermaid/highlight.js
- **IPC types**: ts-rs 10 + schemars; `bun run gen:types` → `src/lib/generated/`
- **Agent

…
## System Boundaries
| Boundary | Description | Direction |
|----------|-------------|-----------|
| Tauri IPC | Rust commands ↔ Svelte (`invoke` + streaming events); Rust types are the truth | internal |
| LLM Providers | OpenAI-compatible (per `OpenAiApiMode` routes `chat/completions` or `responses`) / Ollama local / Ollama Cloud (API key); Native used for lightweight phases and Litho fallback | outbound |
| 

…
## Code Map Index
| Concept | Location | Notes |
|---------|----------|-------|
| Asset generation pipeline | `crates/terrain-core/src/assets/mod.rs` | repomix/context/litho/sdd/ask/env aggregation |
| repomix pack | `crates/terrain-core/src/assets/repomix.rs` | `pack_agent_assets`, pack freshness |
| Context layering/generation | `crates/terrain-core/src/assets/context_layers.rs`, `agent_context.rs` | macro

…
## System
Boundaries


 —

 translate
 table
;
 update


 LLM Provider
 row
 
to

 include

 Ollama
 Cloud
 and
 per-provider
 profiles
.
 Keep

 trust
 
rules

 paragraph

 with

 thresholds
 verbatim-in
-translation
.
## Code
Map
 Index
 —


 translate
 table
;


 Litho
 row

 add
 `
litho
_native.rs`

 note
;
 new
 row


 `Model
 catalog
 &

 provider
 resolution

 |
 crates/terrain-agent
/src/model.rs

 |

 Ll
mProvider
,
 parse_provider
,
 list_provider_models
,
 ModelConfig

 resolution
`.


Now


 character


 budget


:
 I'll
 draft
 and
 count


 roughly
.


 Tables


 dominate
.


 Let me
 write

 it

 c

…
## Project Overview
`,
 `
## Architecture
`,
 `
## Module Map
`,
 `
## Core Flows
`,
 `
## Tech Stack
`,
 `
## System Boundaries
`,
 `
## Code Map Index
`.

Also

 preserve


 the

 diagram

 (ASCII),
 translated
 labels.


 Diagram

 content


 translation
 is
 allowed

 (
"diagram
 labels
 must
 all use

 this
 language
").


 I


 must
 keep
 the

 diagram's
 shape
.

Let me
 now


 also
 double

-check


 one


 thing
:

 the
 overview


 says


 "consum
ers... and external
 Agents
 connected
 via
 ACP
 subprocess" 
— unchanged
.


 Als

…
## Module
Map

 —

 table

 with

 rows
 (translate
 all

;
 terrain
-agent

 row
 gains 



"
model

catalog/provider

resolution

 (LlmProvider
)")
## Core
Flows
 — 4
 numbered
 flows
 with
 bold
 titles
.
## Tech
Stack


 — bullets
.
## System
Boundaries
 — table

 +
 trust
 rules
 paragraph
.
## Code
Map
 Index
 — table
.


 Now

 let


 me


 count


 characters


 roughly
.


 I'll


 write


 it,
 then
 estimate

:
 the
 
ASCII
 
diagram

 ~1700
 chars
.
 Tables
: layer
 
table

 ~450
, module
 map
 
~1200
,
 boundaries
 
~1500
,
 code
 map
 
~1700
.
 Flows


 ~2800
.
 Overview
 ~1100
.
 Tech
 stack

 ~1100
 
. Trust
 paragraph

 ~900
.
 Total


 ~
13
,
5
00
.
 Tight
 but
 OK
.


 I


…
## Project Overview
Terrain is an **engineering-environment platform for coding agents** (Sopaco open-source; source packing driven by repomix-rs). Tagline: *"Terrain lays the ground so agents never have to guess where to stand."* Pointed at a Git repo, it scans code, packs sources (repomix), generates Agent context, C4 architecture docs (Litho), dual-track knowledge (`human/` + `agent/`), and knowledge-freshn

…
## Architecture
```
┌───────────────────────────────────────────────────────────────┐
│ Svelte 5 frontend (src/)        Tauri 2 shell (src-tauri/)    │
│  Ask/DeepWiki · SDD · Litho · Env · Projects · Usage · Tray   │
└───────────────┬───────────────────────────────────────────────┘
                │ invoke + streaming events (ts-rs; Rust is IPC truth)
┌───────────────▼─────────────────────────────────────

…
## Module Map
| Module | Responsibility | Main paths |
|--------|----------------|------------|
| terrain-core | Domain core: asset generation, three-tier retrieval, freshness, ingest, registry, IPC types | `crates/terrain-core/src/` |
| assets/ | repomix pack, agent context, Litho/SDD/Ask assets, incremental refresh, env integration | `crates/terrain-core/src/assets/` |
| freshness | Git + CodeGraph dri

…
## Core Flows
**1. Project registration → knowledge asset generation**
1. `initialize_project` registers the repo into `~/.terrain/registry.json` (path pointer only).
2. `ProjectScanner` collects Git metadata; optional OpenAPI import (`scan_project`).
3. repomix-core packs sources → `.terrain/agent/repomix.md` (`pack_agent_assets`).
4. LLM generates `agent/context.md`; the optional Litho four-phase run p

…
## Tech Stack
- **Rust**: workspace (terrain-core, terrain-agent, terrain-cli, terrain-ts-export, src-tauri), edition 2024, rust-version 1.94
- **Desktop shell**: Tauri 2 (capabilities ACL, plugin-dialog/shell, tray + Usage window)
- **Frontend**: Svelte 5 (runes) + Vite 8 + Tailwind 4 + marked/mermaid/highlight.js
- **IPC types**: ts-rs 10 + schemars; `bun run gen:types` → `src/lib/generated/`
- **Agent

…
## System Boundaries
| Boundary | Description | Direction |
|----------|-------------|-----------|
| Tauri IPC | Rust commands ↔ Svelte (`invoke` + streaming events); Rust types are the truth | internal |
| LLM Providers | OpenAI-compatible (per `OpenAiApiMode` routes `chat/completions` or `responses`) / Ollama local / Ollama Cloud (API key); Native used for lightweight phases and Litho fallback | outbound |
| 

…
## Code Map Index
| Concept | Location | Notes |
|---------|----------|-------|
| Asset generation pipeline | `crates/terrain-core/src/assets/mod.rs` | repomix/context/litho/sdd/ask/env aggregation |
| repomix pack | `crates/terrain-core/src/assets/repomix.rs` | `pack_agent_assets`, pack freshness |
| Context layering/generation | `crates/terrain-core/src/assets/context_layers.rs`, `agent_context.rs` | macro

…