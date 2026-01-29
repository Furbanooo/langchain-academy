# LangGraph Course Resume — Reference Guide ✅

A detailed, module-by-module resume of the entire course, with short links to the exact examples in this repo. Use this as a practical reference guide.

---

## Course Overview 🧭

This course builds from LangGraph fundamentals to production-grade agent systems. You learn:

- Graph-based program structure, state modeling, and state transitions.
- Tool calling patterns, memory design, and persistence via stores/checkpointers.
- Debugging workflows with breakpoints, state inspection, and time-travel.
- Parallelization, map-reduce, and sub-graph composition for scale.
- Human-in-the-loop flows, streaming outputs, and controlled interruptions.
- Deployment-oriented agent architecture and production patterns.

---

## Module 0 — Fundamentals & Setup 🧩

**Goal:** Establish core mental models and environment setup.

**Key concepts:**

- What a graph is, how nodes execute, and how state flows between nodes.
- Basic node definitions and how node outputs update state.
- Notebook-driven learning workflow and how to run/inspect examples.

**What you’ll practice:**

- Running the first graph end-to-end and verifying state transitions.
- Reading example outputs to map graph execution order to state changes.

**Primary reference:**

- [module-0/basics.ipynb](../module-0/basics.ipynb)

**Notebook notes:**

- [module-0/basics.ipynb](../module-0/basics.ipynb) walks through the first graph execution, showing node order and how state updates flow between nodes.

---

## Module 1 — Graph Basics, Routing, Agents 🧱

**Goal:** Build and run simple graphs; introduce routing and agent structure.

**Key concepts:**

- `State` schemas and typed state updates across nodes.
- `StateGraph` creation, node wiring, and linear vs conditional flows.
- Router patterns that pick the next node based on state or user input.
- Intro to agent patterns and how “agent” differs from a simple chain.

**What you’ll practice:**

- Designing minimal states and clean node boundaries.
- Building a router node to branch on intent.
- Running a first agent-like loop with tool calls.

**Primary references:**

- Simple graph: [module-1/studio/simple.py](../module-1/studio/simple.py#L7-L45)
- Agent basics: [module-1/agent.ipynb](../module-1/agent.ipynb)
- Agent memory intro: [module-1/agent-memory.ipynb](../module-1/agent-memory.ipynb)
- Routing: [module-1/router.ipynb](../module-1/router.ipynb)
- Chains: [module-1/chain.ipynb](../module-1/chain.ipynb)
- Deployment intro: [module-1/deployment.ipynb](../module-1/deployment.ipynb)

**Notebook notes:**

- [module-1/agent.ipynb](../module-1/agent.ipynb) introduces an agent loop and shows how tool calls are integrated into graph execution.
- [module-1/agent-memory.ipynb](../module-1/agent-memory.ipynb) extends the agent with memory to persist useful context between turns.
- [module-1/router.ipynb](../module-1/router.ipynb) demonstrates conditional routing based on state or intent.
- [module-1/chain.ipynb](../module-1/chain.ipynb) contrasts linear chains with graph-based flows.
- [module-1/deployment.ipynb](../module-1/deployment.ipynb) introduces basic deployment-oriented patterns and configuration.

---

## Module 2 — State, Schemas, Summarization, Memory 🧠

**Goal:** Master message-based state and schema design, and introduce memory patterns.

**Key concepts:**

- `MessagesState` for chat-like flows and standardized message handling.
- State schemas, typed fields, and reducer functions for safe updates.
- Summarization and trimming strategies to manage context windows.
- External memory via checkpointers and persistent stores.

**What you’ll practice:**

- Designing schemas that separate short-term and long-term state.
- Building reducers to merge messages safely and predictably.
- Adding summarization to keep long conversations manageable.
- Persisting state to SQLite for cross-session continuity.

**Primary references:**

- Messages and chatbot state: [module-2/studio/chatbot.py](../module-2/studio/chatbot.py#L11-L50)
- State schemas: [module-2/state-schema.ipynb](../module-2/state-schema.ipynb)
- Multiple schemas: [module-2/multiple-schemas.ipynb](../module-2/multiple-schemas.ipynb)
- State reducers: [module-2/state-reducers.ipynb](../module-2/state-reducers.ipynb)
- Summarization chatbot: [module-2/chatbot-summarization.ipynb](../module-2/chatbot-summarization.ipynb)
- Trim/filter messages: [module-2/trim-filter-messages.ipynb](../module-2/trim-filter-messages.ipynb)
- External memory with SQLite: [module-2/chatbot-external-memory.ipynb](../module-2/chatbot-external-memory.ipynb)

**Notebook notes:**

- [module-2/state-schema.ipynb](../module-2/state-schema.ipynb) focuses on designing typed state fields and consistent update rules.
- [module-2/multiple-schemas.ipynb](../module-2/multiple-schemas.ipynb) shows how to split state for complex flows.
- [module-2/state-reducers.ipynb](../module-2/state-reducers.ipynb) introduces reducer patterns for safe message merging.
- [module-2/chatbot-summarization.ipynb](../module-2/chatbot-summarization.ipynb) implements summarization to control context growth.
- [module-2/trim-filter-messages.ipynb](../module-2/trim-filter-messages.ipynb) demonstrates trimming and filtering strategies for long chats.
- [module-2/chatbot-external-memory.ipynb](../module-2/chatbot-external-memory.ipynb) adds persistence via SQLite checkpointers.

---

## Module 3 — Debugging, Breakpoints, Time-Travel 🛠️

**Goal:** Build confidence debugging complex graphs.

**Key concepts:**

- Breakpoints and `NodeInterrupt` for controlled stops.
- Dynamic breakpoints that depend on state or runtime conditions.
- Editing state with human feedback to correct or guide execution.
- Streaming interruption and time-travel for stepping through runs.

**What you’ll practice:**

- Inserting a breakpoint and resuming with updated state.
- Adding a dynamic breakpoint that triggers on a state value.
- Replaying a run from a prior checkpoint to validate fixes.

**Primary references:**

- Dynamic breakpoints: [module-3/studio/dynamic_breakpoints.py](../module-3/studio/dynamic_breakpoints.py#L10-L33)
- Breakpoints notebook: [module-3/breakpoints.ipynb](../module-3/breakpoints.ipynb)
- Dynamic breakpoints notebook: [module-3/dynamic-breakpoints.ipynb](../module-3/dynamic-breakpoints.ipynb)
- Edit state with feedback: [module-3/edit-state-human-feedback.ipynb](../module-3/edit-state-human-feedback.ipynb)
- Streaming interruption: [module-3/streaming-interruption.ipynb](../module-3/streaming-interruption.ipynb)
- Time travel: [module-3/time-travel.ipynb](../module-3/time-travel.ipynb)

**Notebook notes:**

- [module-3/breakpoints.ipynb](../module-3/breakpoints.ipynb) demonstrates manual interruption and resume flows.
- [module-3/dynamic-breakpoints.ipynb](../module-3/dynamic-breakpoints.ipynb) shows state-driven breakpoints for conditional stopping.
- [module-3/edit-state-human-feedback.ipynb](../module-3/edit-state-human-feedback.ipynb) adds a human-in-the-loop edit step.
- [module-3/streaming-interruption.ipynb](../module-3/streaming-interruption.ipynb) covers streaming output and mid-stream control.
- [module-3/time-travel.ipynb](../module-3/time-travel.ipynb) walks through replaying and inspecting prior runs.

---

## Module 4 — Parallelization, Map-Reduce, Sub-Graphs ⚡

**Goal:** Scale graphs and compose workflows for higher throughput.

**Key concepts:**

- Parallel execution of independent nodes.
- Map-reduce patterns for large or multi-step tasks.
- Sub-graph orchestration and compositional design.

**What you’ll practice:**

- Splitting work across multiple nodes and merging results.
- Implementing a map-reduce flow to handle batch inputs.
- Encapsulating a workflow as a reusable sub-graph.

**Primary references:**

- Parallelization notebook: [module-4/parallelization.ipynb](../module-4/parallelization.ipynb)
- Map-reduce notebook: [module-4/map-reduce.ipynb](../module-4/map-reduce.ipynb)
- Sub-graph notebook: [module-4/sub-graph.ipynb](../module-4/sub-graph.ipynb)
- Research assistant example: [module-4/research-assistant.ipynb](../module-4/research-assistant.ipynb)
- Studio examples: [module-4/studio/parallelization.py](../module-4/studio/parallelization.py), [module-4/studio/map_reduce.py](../module-4/studio/map_reduce.py)

**Notebook notes:**

- [module-4/parallelization.ipynb](../module-4/parallelization.ipynb) shows how to fan out work and merge results.
- [module-4/map-reduce.ipynb](../module-4/map-reduce.ipynb) applies map-reduce to structured batch tasks.
- [module-4/sub-graph.ipynb](../module-4/sub-graph.ipynb) demonstrates reusable graph composition.
- [module-4/research-assistant.ipynb](../module-4/research-assistant.ipynb) combines several patterns into a realistic workflow.

---

## Module 5 — Memory Systems & Schemas 📚

**Goal:** Design memory and schema strategies for long-lived agents.

**Key concepts:**

- Memory stores, retrieval patterns, and persistence strategy.
- Memory schema design for user profiles and collections.
- Separating ephemeral conversation state from durable memory.

**What you’ll practice:**

- Designing a memory schema for a specific domain.
- Retrieving and updating memory based on user input.
- Building a memory-aware agent that evolves over time.

**Primary references:**

- Memory agent: [module-5/memory_agent.ipynb](../module-5/memory_agent.ipynb)
- Memory store: [module-5/memory_store.ipynb](../module-5/memory_store.ipynb)
- Memory schema collection: [module-5/memoryschema_collection.ipynb](../module-5/memoryschema_collection.ipynb)
- Memory schema profile: [module-5/memoryschema_profile.ipynb](../module-5/memoryschema_profile.ipynb)

**Notebook notes:**

- [module-5/memory_agent.ipynb](../module-5/memory_agent.ipynb) integrates memory retrieval into agent decisions.
- [module-5/memory_store.ipynb](../module-5/memory_store.ipynb) focuses on store configuration and retrieval strategies.
- [module-5/memoryschema_collection.ipynb](../module-5/memoryschema_collection.ipynb) designs collection schemas for domain memories.
- [module-5/memoryschema_profile.ipynb](../module-5/memoryschema_profile.ipynb) builds user profile schemas for personalization.

---

## Module 6 — Advanced Agents & Deployment 🧑‍💻

**Goal:** Production-minded agent design with memory, tools, and deployment.

**Key concepts:**

- Multi-step assistant architecture with explicit tool invocation.
- Tool calling and structured updates for reliable state changes.
- Persistence via `Store` and checkpointers for durable agents.
- Real deployment patterns and operational considerations.

**What you’ll practice:**

- Connecting multiple tools into a single workflow.
- Building an assistant that tracks tasks and user context.
- Reading a full production-grade agent implementation.

**Primary references:**

- Task mAIstro (end-to-end agent): [module-6/deployment/task_maistro.py](../module-6/deployment/task_maistro.py#L136-L390)
- Assistant notebook: [module-6/assistant.ipynb](../module-6/assistant.ipynb)
- Connecting & creating agents: [module-6/connecting.ipynb](../module-6/connecting.ipynb), [module-6/creating.ipynb](../module-6/creating.ipynb)
- Double-texting patterns: [module-6/double-texting.ipynb](../module-6/double-texting.ipynb)

**Notebook notes:**

- [module-6/assistant.ipynb](../module-6/assistant.ipynb) builds a multi-step assistant that coordinates tools and memory.
- [module-6/connecting.ipynb](../module-6/connecting.ipynb) explains how to wire tools and data sources into an agent.
- [module-6/creating.ipynb](../module-6/creating.ipynb) focuses on constructing agents with structured state and tool routing.
- [module-6/double-texting.ipynb](../module-6/double-texting.ipynb) covers patterns for safe multi-turn tool usage.

---

## Cross-Cutting Reference Map 🗺️

Use this when you need fast entry points for specific concepts:

- **State + StateGraph:** [module-1/studio/simple.py](../module-1/studio/simple.py#L7-L45)
- **MessagesState + chat flow:** [module-2/studio/chatbot.py](../module-2/studio/chatbot.py#L11-L50)
- **External memory (SQLite checkpointer):** [module-2/chatbot-external-memory.ipynb](../module-2/chatbot-external-memory.ipynb)
- **Breakpoints / NodeInterrupt:** [module-3/studio/dynamic_breakpoints.py](../module-3/studio/dynamic_breakpoints.py#L10-L33)
- **Parallelization & map-reduce:** [module-4/parallelization.ipynb](../module-4/parallelization.ipynb), [module-4/map-reduce.ipynb](../module-4/map-reduce.ipynb)
- **Memory schema strategies:** [module-5/memoryschema_collection.ipynb](../module-5/memoryschema_collection.ipynb), [module-5/memoryschema_profile.ipynb](../module-5/memoryschema_profile.ipynb)
- **Production-grade agent + store:** [module-6/deployment/task_maistro.py](../module-6/deployment/task_maistro.py#L136-L390)

---

## Suggested Learning Path ✅

1. Start with [module-0/basics.ipynb](../module-0/basics.ipynb).
2. Build simple graphs in [module-1/studio/simple.py](../module-1/studio/simple.py#L7-L45).
3. Move to state schemas and message flows in [module-2/state-schema.ipynb](../module-2/state-schema.ipynb) and [module-2/studio/chatbot.py](../module-2/studio/chatbot.py#L11-L50).
4. Learn debugging in [module-3/breakpoints.ipynb](../module-3/breakpoints.ipynb) and [module-3/time-travel.ipynb](../module-3/time-travel.ipynb).
5. Scale patterns in [module-4/parallelization.ipynb](../module-4/parallelization.ipynb) and [module-4/map-reduce.ipynb](../module-4/map-reduce.ipynb).
6. Master memory with [module-5/memory_store.ipynb](../module-5/memory_store.ipynb).
7. End with deployment patterns in [module-6/assistant.ipynb](../module-6/assistant.ipynb) and [module-6/deployment/task_maistro.py](../module-6/deployment/task_maistro.py#L136-L390).
