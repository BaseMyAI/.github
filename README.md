<p align="center">
  <img src="../assets/img/basemyai.png" alt="BaseMyAI — The private memory database for AI agents" width="100%">
</p>

<h1 align="center">BaseMyAI</h1>

<p align="center">
  <strong>The private memory database for AI agents.</strong>
</p>

<p align="center">
  Local-first · Temporal · Encrypted · Agent-scoped · Hybrid recall
</p>

<p align="center">
  <a href="https://github.com/BaseMyAI/basemyai">Repository</a>
  ·
  <a href="https://github.com/BaseMyAI/basemyai#readme">Documentation</a>
  ·
  <a href="https://github.com/BaseMyAI/basemyai/security/policy">Security</a>
  ·
  <a href="https://crates.io/crates/basemyai">crates.io</a>
  ·
  <a href="https://pypi.org/project/basemyai/">PyPI</a>
</p>

---

<h2>
  <img src="../assets/icon/contents.svg" width="20" height="20" alt="">
  What is BaseMyAI?
</h2>

BaseMyAI is an embedded **Agent Memory Database** for AI agents that need memory they can actually trust.

It stores agent memory inside a local encrypted `.bmai` database and gives agents persistent recall with vector search, temporal validity, memory layers, graph context, adaptive forgetting, and hybrid retrieval.

BaseMyAI is **not another hosted vector database**.

It is built for private assistants, coding agents, internal copilots, local-first tools, and products that cannot leak user memory to a cloud memory store.

---

<h2>
  <img src="../assets/icon/gettingstarted.svg" width="20" height="20" alt="">
  Quick start
</h2>

```bash
basemyai setup --fetch

export BASEMYAI_DB_KEY="change-me-use-a-real-secret-key"

basemyai init ./agent.bmai

basemyai remember ./agent.bmai \
  --agent assistant-42 \
  --layer semantic \
  "User is on the Pro plan."

basemyai recall ./agent.bmai \
  --agent assistant-42 \
  "current billing plan" \
  --hybrid
```

---

<h2>
  <img src="../assets/icon/features.svg" width="20" height="20" alt="">
  Core principles
</h2>

| Principle                   | Description                                                                       |
| --------------------------- | --------------------------------------------------------------------------------- |
| **Local-first by default**  | Memory stays on the user's machine. No hosted memory backend by default.          |
| **Encrypted `.bmai` files** | Agent memory lives in a local encrypted BaseMyAI container.                       |
| **Temporal memory**         | Facts can expire or be invalidated, so stale memories do not silently win recall. |
| **Agent-scoped isolation**  | Each memory operation is scoped by `agent_id` to prevent cross-agent leakage.     |
| **Multi-layer memory**      | Short-term, episodic, procedural, and semantic memories are treated differently.  |
| **Hybrid recall**           | Vector search, BM25, graph context, and RRF fusion work together.                 |
| **Inspectable memory**      | Developers can inspect, export, import, invalidate, and debug memory behavior.    |
| **Rust foundation**         | One engine powers Rust, Python, Node, CLI, MCP, and REST surfaces.                |

---

<h2>
  <img src="../assets/icon/documentation.svg" width="20" height="20" alt="">
  Why BaseMyAI exists
</h2>

AI agents usually fail memory in one of three ways:

1. They forget everything between sessions.
2. They send sensitive memory to a hosted vector database.
3. They recall outdated facts as if they were still true.

BaseMyAI fixes that by giving agents a dedicated memory database that is local, encrypted, temporal, and purpose-built for agent workflows.

A vector database can store embeddings.

BaseMyAI stores **agent memory**.

---

<h2>
  <img src="../assets/icon/features.svg" width="20" height="20" alt="">
  Memory model
</h2>

BaseMyAI separates memory into four layers:

| Layer          | Purpose                                      | Typical lifetime        |
| -------------- | -------------------------------------------- | ----------------------- |
| **short_term** | Active working context                       | Short TTL               |
| **episodic**   | Events, interactions, what happened and when | Time-bounded            |
| **procedural** | Workflows, steps, habits, learned behaviors  | Long-lived              |
| **semantic**   | Facts and knowledge                          | Valid until invalidated |

Every layer supports temporal validity through `valid_from` and `valid_until`.

That means an agent can remember that something **used to be true** without treating it as true forever.

---

<h2>
  <img src="../assets/icon/features.svg" width="20" height="20" alt="">
  Recall system
</h2>

BaseMyAI recall is multi-signal by design.

| Signal                    | Role                                                           |
| ------------------------- | -------------------------------------------------------------- |
| **Vector search**         | Finds semantically similar memories.                           |
| **BM25 full-text search** | Catches exact terms, IDs, names, filenames, and rare keywords. |
| **Graph context**         | Connects entities and relationships across memories.           |
| **Temporal filtering**    | Removes expired or invalidated facts from active recall.       |
| **RRF fusion**            | Merges ranking signals without brittle manual weights.         |

This makes recall more reliable than cosine similarity alone.

---

<h2>
  <img src="../assets/icon/security.svg" width="20" height="20" alt="">
  Security and privacy
</h2>

BaseMyAI is built for developers who need memory they can control.

- encrypted local `.bmai` files
- no hosted memory backend by default
- no silent model downloads
- explicit setup for model provisioning
- per-agent memory isolation
- local-first operation
- key supplied by the application or environment
- designed for privacy-sensitive agents and internal tools

See the full security policy:

[Security Policy](https://github.com/BaseMyAI/basemyai/security/policy)

---

<h2>
  <img src="../assets/icon/installation.svg" width="20" height="20" alt="">
  Supported environments
</h2>

<p>
  <img src="../assets/icon/apple.svg" width="18" height="18" alt="macOS"> macOS
  &nbsp;&nbsp;
  <img src="../assets/icon/linux.svg" width="18" height="18" alt="Linux"> Linux
  &nbsp;&nbsp;
  <img src="../assets/icon/windows.svg" width="18" height="18" alt="Windows"> Windows
</p>

BaseMyAI is built in Rust and designed for cross-platform local deployment.

---

<h2>
  <img src="../assets/icon/documentation.svg" width="20" height="20" alt="">
  Main repository
</h2>

[`BaseMyAI/basemyai`](https://github.com/BaseMyAI/basemyai)

The main repository contains:

- Rust workspace
- memory engine
- CLI
- MCP server
- REST sidecar
- Python binding
- Node binding
- architecture decisions
- benchmarks
- security policy
- technical proofs

---

<h2>
  <img src="../assets/icon/features.svg" width="20" height="20" alt="">
  Consumption surfaces
</h2>

| Surface          |                            Status | Use case                                   |
| ---------------- | --------------------------------: | ------------------------------------------ |
| **Rust crate**   |                         Available | Native Rust agents and embedded engines    |
| **Python SDK**   |                         Available | Python agent builders                      |
| **Node SDK**     | In progress / verify package name | JavaScript and TypeScript agents           |
| **CLI**          |                         Available | Local inspection, scripting, automation    |
| **MCP server**   |                         Available | Claude Code and agent-tool integrations    |
| **REST sidecar** |                         Available | Local HTTP integration for other languages |

---

<h2>
  <img src="../assets/icon/cloud.svg" width="20" height="20" alt="">
  Product direction
</h2>

BaseMyAI starts with a reliable **libSQL-backed `.bmai` V1**, then moves toward a native BaseMyAI engine while preserving the public memory database contract.

The long-term direction is full ownership over:

- storage
- indexing
- vector search
- graph traversal
- memory events
- future sync primitives
- query language possibilities

The public contract stays simple:

> a private memory database for AI agents.

The internal engine can evolve without turning BaseMyAI into a wrapper around someone else's database.

---

<h2>
  <img src="../assets/icon/contributing.svg" width="20" height="20" alt="">
  Contributing
</h2>

BaseMyAI is being built as serious local AI memory infrastructure.

Useful places to start:

- explore the main repository
- read the architecture decisions
- run the CLI locally
- inspect the benchmark docs
- open issues or discussions
- test SDK and MCP workflows

<p>
  <a href="https://github.com/BaseMyAI/basemyai">Open the repository</a>
</p>

---

<h2>
  <img src="../assets/icon/community.svg" width="20" height="20" alt="">
  Useful links
</h2>

- [Repository](https://github.com/BaseMyAI/basemyai)
- [Documentation](https://github.com/BaseMyAI/basemyai#readme)
- [Security Policy](https://github.com/BaseMyAI/basemyai/security/policy)
- [crates.io package](https://crates.io/crates/basemyai)
- [PyPI package](https://pypi.org/project/basemyai/)

---

<p align="center">
  <strong>Built for developers and enterprise who want AI agents with memory they can actually trust.</strong>
</p>
