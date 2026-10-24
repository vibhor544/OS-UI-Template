# OpenSensei

OpenSensei is a FOSS, local-first desktop app that helps students learn programming through structured, personalized AI tutoring. Our goal is to build independent problem-solving skills through understanding, practice, and real projects. Our goal is to completely replace the need for traditional learning pathways such as paid lectures, YT videos and courses, with the one single app for learning almost everything a programmer needs.

This is not a personalized AI-learning platform - but the agentic harness for learning how to code. This is claude code, but for learning how to code.

# Product

## Required direction

- Help college students learn programming independently through structured, personalized practice.
- Desktop-only application for Windows, macOS, and Linux.
- FOSS & Local-first; free MVP with mandatory Google sign-in.
- Local learning storage and execution; the hosted backend stores account/session data only.
- User-owned AI access: API key, local model, or OpenRouter authorization.
- Shared global learner memory plus Book, Studio & Chats-scoped memory.
- Polished, responsive, enjoyable, warm, UI/UX; efficient model use.
- The UI/UX must indicate the student's brain to go into a calm & focused state.
- Mild gamification of the app. The user must feel rewarded and motivated to continue the journey. They must feel like they're learning a lot of things very fast & easily. 
- The ultimate goal is to make the app addictive such that the user keeps coming back.

## Modules
- Home Page: Warm greeting, current roadmap progress, list of books, studio projects and chat history, & other essential UI elements.
- Books: heart of the product. AI creates structured books for each topic user wants to learn, with chapters, items, notes, and exercies - that follow a roadmap created at the time of book creation.
- Dev Studio: Full, customized, IDE built on Theia, to build projects & code with AI assistance whenever user gets stuck.
- Chats: general chats with AI for quick conversations.


## Learning experience
- Sign in
- Brief onboarding: learn about user's learning style & coding compentence.
- Prompt to enter API keys: plus an option "How to get free API keys" guiding user to use gemini or Nvidia APIs
- Home page -> New Book -> User enters the topic they want to learn -> AI asks few questions -> Creates a roadmap for user + explanation/justification -> user approves or prompts AI to change -> Roadmap created

### Books
- Each roadmap can have the following elements: 
- - Child books/Nested books: if user asked for a huge topic, like full stack app, roadmap will have nested books such as Frontend, Backend, & DevOps books, instead of an entire giant roadmap
- - Chapters: like learning modules
- - Items: like folders
- - Notes: Where the actual content sits
- - Exercise: Exercises can be embeded in Notes itself or individually
- - Boss fight: Hands-on programming/project building challenge, Ideally one every 2-3 chapters (end), but not necessarily.
- - Optional side quests (can have chapters, items, notes etc.)
- Roadmap includes the complete structure. This structure can be flexibly changed anytime in between the lecture.
- Notes are generated on-the-fly, instead of all at once.
- Rich pages support manual edits, visuals, quizzes, and questions. Tutor chat accepts explicit selected/current-item context chips. Users can request additions or rewrites of lessons and assessments.
- Upon completing each book, the user receives a badge (like frontend - Gold). exercise score 75%: Bronze, 85%: Silver, 90% Gold, 100%: Platinum.
- User can only proceed to the next note/item/chapter after answering 75% questions correctly. However, users can teleport by clicking on a future note, after answering a prompt: "jumping to future notes without clearing previous exercises will reduce the quality of the notes & make you inelligible to win badges or certificates for this book. Do you still wish to proceed?"
- Exercises can contain AI generated MCQs with 4 options, subjective questions with text input box (pass/fail), console to write code and produce some output (Monaco/shared runner). // Todo: What other creative exercises can we have?
- Repository-sized challenges (mostly boss fights) can open a linked Studio workspace. Books retains the assessment record. 
- User can rectify their answer if they answered incorrectly, and still score 100%. Forgiving excercise system.
- Adapt from demonstrated work as well as self-report. Track reading, assisted practice, independent performance, and transfer separately. Explanation preferences remain editable.
- UI: left - contents, middle: notes, right: AI chat. Panels collapse for focused work. 
- AI will have full context, can dynamically change any line or element inside the notes, rewrite it, and flexibly change anything. The AI adapts to user's learning style. Has in-built skills, eg, if user asks a "why" about something, it uses the explain skill.
- For Boss fights, question statement in leetcode style will be given with test cases, input, outputs, etc. and the test itself will be attempted in a new instance of Dev Studio. After writing code, user can verify. AI writes test cases in the codebase and whatever else to confirm all the required functionalities pass. Boss fights can have multiple stages (1-8) - AI can say: "great you passed this. now add implement this feature in stage 2". User can see the number of stages before starting the boss fight. Dev studio & Books module will have to communicate pass/not passed state.
- Also sprinkle in mini boss fights wherever due/needed: quick coding challenges that can be done with either integrated console or Dev Studio.
- Implementation challenges always have separate exercise items; code-prediction questions may appear inside notes.
- Final boss fight at the end of every roadmap.
- Before a boss, offer exactly four distinct project themes with comparable skill coverage/difficulty. Persist the choice, then author the project SPEC, starters, rubric, and checks. Reject unintroduced required prerequisites. Mini-bosses cover the chapter; bosses combine several chapters.
- Exercises, notes, examples, boss fights etc. must include references to user's interests wherever appropriate. Don't forcefully add it at every place.
- For each book, users also have the option to create their TIL.md, concepts.md, mistakes.md & questions.md
- Resolve an existing item revision or claim an idempotent generation job.
- Build bounded context; generate only the needed document/assessment.
- Validate blocks, objectives, references, and assessment definitions.
- Validate executable challenges against reference solutions/tests.
- Commit atomically; keep recoverable state on failure.
- AI chat modes: Ask (help, Explain, guide - default), Plan (Material follow-ups, outlines, evidence-driven roadmap patches).
- Model questions are validated JSON forms rendered by registered React controls
- Trigger planning at reviewed exercises/checkpoints, repeated misconceptions, or explicit requests. Send an evidence delta and affected outline window; request a minimal insert/move/update/archive patch.
- Validate expected revision, hierarchy, prerequisites/cycles, required coverage, checkpoint placement, optional branches, and preserved history.
- **Default:** safe unstarted-future changes may auto-apply with explanation. Changes to goals, active assessments, or completed evidence require preview/acceptance.
- Use block-level document patches. Text edits do not change answer keys or gates. Assessment rewrites create new revisions; preserve historical attempts and reject stale reviews. Represent new remediation as new work.
- // Todo: define every react component that AI can generate inside notes aside plain text & mermaid charts, to explain the topic to the student. Support rich editable notes, code, diagrams, questions etc.
- For v2: currency/reward system? each exercise gives you 'will' currency, you level up. Bronze 3 -> Bronze 2 -> Bronze 1 | Silver | Gold | Diamond | Platinum | Obsidian | Immortal | Englightened (not 3, 2, 1 here, only the title itself.) Will collected is based on attempts. First try correct answer: high will (random number so a luck factor is instated), 2nd + attempts: default will. Ladder must be like: upon completing one average length chapter like Python, they go from Bronze 3 to somewhere in Bronze 1. Upon going from html to complete devops, student earns Diamond. If they score 100% (first tries mostly), then Platinum. Whenever student's title upgrades, a beauitful, rewarding animation of ascension should suddenly show up on screen, right after they answered a question. 

### Roadmap
- Render the initial query form without a model call. Ask questions like:
- - What do you want to learn? (textbox)
- - What can you already do? (textbox)
- - How technical do you want? And a slider: technical - balanced (default) - simple - baby mode (you can change this later)
- - Anything else you'd like to add? (optional) - like preferred tech stack, college curriculum, course references, constraints, inclusions/exclusions (changeable later)
- Next, loading screen, render follow-up AI generated questions. At-most 2 follow up rounds. 
- Show the personalized roadmap and a short rationale grounded in answers/evidence. Persist it; after acceptance, generate the first available note/item.


### Dev Studio
- Very minimal theme - left: files, middle: code editor with tabs, right: AI chat. Panels collapse for focused work. 
- Studio provides persistent projects, editor, terminal, runtime, tests, debugger, Git, and previews.
- AI modes: Help (/hint, /debug), Examination (/code-review, /arch), Ask (for asking general concepts - AI will just tell the answer, not question user) and auto (default).
- User can invoke commands in chat like /hint, /code-review. UI suggests commands as hints in blank chats.
- When user creates a new project, a brief overview of all features and how to use it are shown, along with the option to never show it again
- Each project is created in a folder custom allocated by the user. By default, select a safe location in user's computer.
- // TODO: exact skills & commands from Toolkit

### Chats
- Just like any basic chat app, with history, uses global shared memory, reasoning, etc.

### Misc
- Each new book/studio/chat opens as a new workspace with visible navigation at top. Home page icon is always pinned. Workspaces show as: 1 • • • / • 2 • • / alongwith home icon
- Profile pfp pinned on top right. Clicking opens a menu with:
- - Customize profile (including editing of preferences)
- - App settings
- - Report bug 
- - Request feature

## MVP priorities

1. Local shell/storage, Google sign-in, AI connections, export/recovery.
2. Early Theia integration and packaged-platform spike.
3. Complete Books loop: plan -> generate -> attempt -> review -> update evidence -> adapt.
4. Studio with selected working toolchains; Chats with shared AI/memory services.

---

# Planned stack


| Layer | Choice |
|---|---|
| Language/runtime | Strict TypeScript; supported Node.js LTS |
| Desktop/build | Electron, electron-vite, electron-builder |
| UI | React, Vite, Tailwind CSS, shadcn/ui |
| Motion/layout | Motion for React; resizable panels; shared design tokens |
| Navigation/data/UI state | TanStack Router, TanStack Query, Zustand |
| Forms/contracts | React Hook Form, Zod |
| Large lists | TanStack Virtual |
| Books editor | Tiptap with registered learning blocks |
| Roadmaps | React Flow; add automatic layout only when needed |
| Rendering | Shiki, KaTeX, Mermaid; Markdown/GFM rendering where appropriate |
| Full Studio | Customized Eclipse Theia |
| Small exercises | Monaco plus the shared local runner |
| Local persistence | SQLite, better-sqlite3, Drizzle; native filesystem and Git |
| Search | SQLite FTS5; local embeddings only if justified |
| AI | AI SDK Core in local services; provider adapters |
| Local model connection | Ollama initially |
| Identity service | Hono, Better Auth including Electron integration, SQLite/Drizzle |
| Workspace/testing | pnpm workspaces, Vitest, Playwright, platform CI |

UI polish comes from a consistent visual system, accessible components, thoughtful motion, and explicit loading/error states.

Strictly don't keep any paid external dependencies or services.


## Decisions and tradeoffs

| Choice | Reason / boundary |
|---|---|
| Electron over Tauri initially | Node-based tooling and consistent Chromium fit Studio; larger shell footprint |
| Vite application | Local application does not require a server-rendered UI |
| Theia over a Code-OSS fork | Custom IDE framework with build-time extensions; validate required VS Code API coverage |
| Monaco for small exercises | Editor library only; it does not supply a complete IDE or general extension host |
| code-server/OpenVSCode deferred | Useful browser workbenches; the product is a local desktop application |
| SQLite over a hosted learning DB | Local ownership, transactions, straightforward device persistence |
| Direct internal tools before MCP | Small typed interfaces; add protocol interoperability when needed |

Use selected Open VSX extensions; audit individual licenses and compatibility. Do not assume access to Microsoft's extension marketplace or proprietary extensions. Choose FOSS editor features rather than mandatory paid extensions.

WebContainers is not the core runtime: browser execution is outside the current product direction and its terms impose additional constraints.

## Validation before committing implementation

- Prove local Theia startup, context bridge, diagnostics, tests, and shutdown.
- Package native modules against the selected Electron runtime on each supported OS/architecture.
- Initially propose Python and JavaScript/TypeScript; exact versions and distribution strategy remain open.
- Benchmark startup, idle memory, UI latency, and inference on student hardware.
- Pick the repository license, runtime sandbox strategy, release signing/updating, and version matrix before distribution.

References: [Electron](https://www.electronjs.org/docs/latest/), [Theia architecture](https://theia-ide.org/docs/architecture/), [Theia extensions](https://theia-ide.org/docs/extensions/), [Monaco](https://github.com/microsoft/monaco-editor), [Drizzle SQLite](https://orm.drizzle.team/docs/sqlite/get-started-sqlite).

# Rough Architecture

## Local process boundary

~~~text
React: Books / Studio / Chats
  -> narrow validated IPC
Local services:
  learning + storage + memory/context + AI orchestration
  Studio backend + toolchain/process manager
  -> SQLite / files / Git / local model
  -> selected AI provider, directly when configured

Account service:
  Google identity + application sessions
  no learning-content endpoints
~~~

One desktop product with modular services. Keep Theia as an isolated, separately built integration with a supervised local backend. Share learning/AI logic across all three parts.

## Ownership

| Location | Owns |
|---|---|
| React renderer | Presentation, interaction state, safe context previews |
| Local services | Domain rules, credentials, files, DB, AI requests, process execution |
| SQLite | Rich documents, roadmap, attempts, memory, conversations, jobs |
| Filesystem | Source repositories, assets, imported/learner-authored files |
| OS secret store | Provider keys and authentication secrets |
| Hosted account service | Identity, provider association, necessary session records |

Rich-document JSON is canonical; Markdown export is a projection. Learner-authored Markdown can be canonical and indexed. Imported edits to projections require reconciliation. See [data model](DATA_MODEL.md).

## Authentication and AI connections

- Google sign-in and AI-provider authorization are independent.
- Default: authenticate during first setup, then support ordinary local usage offline. Session expiry/revalidation policy remains open.
- Use the system browser for authorization; the application UI remains desktop.
- OpenRouter: fresh PKCE S256 + state -> temporary loopback callback -> validate response -> exchange code locally for user-controlled key -> secure storage -> close listener.
- Direct-key and local-model connections also run through the local AI service.
- Cloud providers receive submitted context; only local-model inference keeps it on-device.
- No learning-content telemetry, remote secret logs, or account-service inference proxy.
- On Linux, detect unavailable secure secret storage; never silently treat plaintext fallback as secure.
- Account login recovers identity. Device migration requires export/import until a separately designed sync feature exists.
- Future billing/entitlements belong to the account service; learning persistence remains local.

## Runtime and safety

- Typed IPC with Zod, sender validation, scoped capabilities, context isolation; no raw Node/Electron bridge.
- Treat imported/generated content as data. Render validated blocks; never execute model-supplied application JSX.
- Discover installed toolchains initially; manage environments, terminals, tests, debuggers, previews, and shutdown locally.
- Running student code is a distinct trust boundary from Electron renderer sandboxing. Decide isolation before arbitrary-repository support; Docker is an optional future environment.
- Preserve learner edits using revisions, transactions, migrations, snapshots, idempotency, and backups.
- Keep slow work off the UI thread. Lazy-load Studio; cancel tasks and recover saved workflows.

Suggested organization: desktop features/books|studio|chats; separate studio-ide and auth-service applications; shared contracts, domain, local-core, AI, and UI packages.

References: [Electron security](https://www.electronjs.org/docs/latest/tutorial/security), [Better Auth Electron](https://better-auth.com/docs/integrations/electron), [OpenRouter authorization](https://openrouter.ai/docs/guides/overview/auth/oauth).

# AI runtime

Use resumable explicit workflows and bounded calls. Persist pending forms/jobs/submissions. Validate schema output and references; default to one repair attempt. A model failure never implies successful assessment.

For executable challenges, check the reference implementation/tests before release. At submission, run checks locally and send compact results to one review call. Cache immutable code snapshots. Do not call a model per MCQ or after every memory update.

Application skills: roadmap-design, lesson-authoring, exercise-design, assessment-review, challenge-themes, targeted-revision, scoped-memory. Load only the selected skill; these are versioned app instructions, not continuously running agents or installed Codex skills.


## Token efficiency

Avoid calls first: deterministic defaults/projections, lazy item generation, persisted rationale/content, local exact grading, batched reviews, bundled memory candidates, checkpoint-only adaptation, scoped excerpts, minimal patches, bounded tools/retries.

Starting targets to benchmark:

| Task | Input tokens | Output tokens |
|---|---:|---:|
| Onboarding follow-up | 1,000-2,000 | 200-600 |
| Course outline | 2,000-4,000 | 1,000-2,500 |
| Ordinary item | 2,500-4,500 | 800-2,000 |
| Tutor reply | 1,500-3,000 | 250-700 |
| Small exercise review | 2,000-4,000 | 300-800 |
| Five themes | 800-1,500 | 150-350 |
| Roadmap patch | 1,500-3,000 | 200-700 |

Boss/code tasks may need more. Reuse validated project templates. Count schemas/tool results and reserve output capacity; use model-aware tokenizers or calibrated estimates. Choose models by measured total cost and learning quality.

## Caches

Local caches: generated documents, context projections, scoped retrieval, pure transformations. Invalidate by source revision/deletion. Exact model-result keys include task, provider/model, prompt/skill/schema versions, source/assessment revisions, and input/submission hashes. Never reuse a stale review.

Provider KV caching is separate: retain eligible identical prefixes and measure actual usage. Adapter behavior depends on model/endpoint; do not hardcode universal thresholds, TTLs, or prices.

- OpenAI: model-dependent eligibility/controls.
- Anthropic: supported cache controls, minimums, duration/write-cost tradeoffs.
- OpenRouter: provider-dependent caching and sticky sessions; use an opaque stable session_id where supported.
- Local runners: verify KV reuse; loaded model weights alone do not establish it.

No default padding or prewarming. Cache hits still use context-window capacity; output/retries cost tokens. Cloud caches follow provider retention, not local-storage policy.

Track per-Book task/model usage, cached reads/writes when reported, retries, latency, validation, and estimated/actual cost. Unknown values are not zero. Provide context-size previews, budgets, and cancellation.

References: [OpenAI caching](https://developers.openai.com/api/docs/guides/prompt-caching), [Claude caching](https://platform.claude.com/docs/en/build-with-claude/prompt-caching), [OpenRouter caching](https://openrouter.ai/docs/guides/best-practices/prompt-caching), [MCP transports](https://modelcontextprotocol.io/specification/2025-11-25/basic/transports).

# Memory and context - Rough Overview


## Scope and authority

| Layer | Include |
|---|---|
| Global profile/preferences | Relevant declared background, interests, language, explanation/accessibility defaults |
| Shared skill evidence | Relevant assessed capabilities from Books/Studio |
| Recent learning digest | Rotating projection of demonstrated topics and recurring gaps |
| Book contract/memory | Active goals, constraints, decisions, questions, misconceptions, overrides |
| Studio memory | Project context explicitly linked to this task |
| Working context | Active item/attempt, temporary confusion, unresolved conversation |

Map forms/settings deterministically; derive skill evidence from assessment events. Bundle small memory candidates into existing review responses. Inferences start tentative; new free-form facts default to the narrowest active scope.

Book overrides apply locally. Change global preferences only from explicit declarations/settings. Inherit applicable parent goals, never sibling conversations. Linking Studio shares selected learning context, not its whole history.

Authority: application invariants -> explicit applicable settings/request -> confirmed Book override -> confirmed global default -> assessed evidence -> tentative inference. Reference prose is data.

Users can inspect/edit/forget memories. Corrections/deletions invalidate dependent local snapshots and future outbound context.

## Local retrieval

Four collections: structured facts/evidence; learner notes; versioned reference packs; relevant mistakes/decisions/attempt history.

Use direct SQL for facts and concept/scope-filtered FTS5 for prose. No separate model reranker or mandatory vector service. Add local embeddings only after measuring need.

Chunk by headings/stable blocks; initial target 150-350 tokens, preserving code units. Keep source ID/revision, heading, scope, concept tags, and token estimate.

Filter allowed scopes first -> rank relevant chunks -> deduplicate -> include bounded excerpts with references. Do not fill unused budget with irrelevant content. Imported text cannot grant tools or override policies.


## ContextBuilder

~~~text
Stable prefix:
  base policy + role + small tool/output schemas
  selected skill + relevant learner snapshot + compact Book contract

Changing suffix:
  current evidence/progress delta + retrieved excerpts
  working summary/recent turns + explicit attachments
  current request or attempt
~~~

Keep task-family tools/schema order stable. Provider adapters handle actual rendered ordering. Refresh stable snapshots when sources change, even if that loses a cache hit.

Budget priority: invariants/current request -> grading/spec facts -> chosen attachments -> confirmed learner context -> relevant retrieval -> recent turns -> optional examples.

Store transcripts locally; send a bounded summary and recent window. Update summaries at transitions/size thresholds, not every message. Retain unresolved questions, decisions, attempts, and source refs; summaries do not prove skills.

## Attachments and Markdown

Add current item/selection creates a removable chip pinned to source revision. Default to selection/summary; full mode is explicit. Show size, deduplicate, and offer an update after source edits.

Never silently truncate required criteria or explicit full attachments; request narrower scope or a suitable model.

Read selected SPEC/note sections rather than entire memory files. Persist context manifests: source/chunk revisions, omissions, token estimates, provider/model, prompt/skill/schema versions, snapshot hash. No random IDs/timestamps in stable prefixes.

