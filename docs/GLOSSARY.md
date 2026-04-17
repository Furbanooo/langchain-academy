# LangGraph Course Glossary — Quick Reference ✅

A concise one-page glossary of key terms used in this course, plus deep-dive examples showing where they appear in the repo.

---

## Core Concepts 🔧

### State 🧾

**What:** The in-memory snapshot that flows between nodes (usually a `dict` / `TypedDict`).
**Purpose:** Holds variables, messages, and intermediate results used to decide next steps.
**Example:** `module-1/studio/simple.py` — `class State(TypedDict)` and node functions that read/return `state`.

```python
# module-1/studio/simple.py
class State(TypedDict):
    graph_state: str

def node_1(state):
    return {"graph_state": state['graph_state'] + " I am"}
```

---

### StateGraph 🔁

**What:** Builder/runtime that wires nodes and executes the graph with a `State` schema.
**Example:** `module-1/studio/simple.py` — `builder = StateGraph(State)`.

```python
builder = StateGraph(State)
builder.add_node("node_1", node_1)
```

---

### MessagesState & Messages 💬

**What:** A state variant for chat message flows (contains `messages` list of `HumanMessage`/`SystemMessage`/`AIMessage`).
**Example:** `module-2/studio/chatbot.py` uses `MessagesState` and `State(MessagesState)`.

```python
from langchain_core.messages import HumanMessage, SystemMessage
from langgraph.graph import MessagesState

class State(MessagesState):
    summary: str
```

---

### Thread 🧵

**What:** An independent execution / conversation instance (a separate run through the graph).
**Purpose:** Isolate concurrent flows—each thread has its own `state` and can have its own checkpoints and stores for persistence.
**Example:** Multiple users interacting concurrently → separate threads; see `module-6/deployment/task_maistro.py` where `user_id` namespaces stored memories.

---

### Checkpoint / Checkpointer / MemorySaver 💾

**What:** Persisted snapshot of state for resume/rollback/auditing.
**Examples:** SQLite checkpointer in `module-2/chatbot-external-memory.ipynb` (SqliteSaver); `MemorySaver` import in `module-6/deployment/task_maistro.py`.

```python
# module-2/chatbot-external-memory.ipynb
from langgraph.checkpoint.sqlite import SqliteSaver
memory = SqliteSaver(conn)

# compile graph with checkpointer
graph = workflow.compile(checkpointer=memory)
```

---

### Store / BaseStore / InMemoryStore 🗄️

**What:** Abstractions/implementations for storing long-term data (memories, checkpoints).
**Example:** `module-6/deployment/task_maistro.py` imports `BaseStore` and `InMemoryStore` and uses `store.put` / `store.search`.

```python
namespace = ("todo", todo_category, user_id)
store.put(namespace, key, {"memory": new_memory.content})
memories = store.search(namespace)
```

---

## Memory & Tooling 🧠

### UpdateMemory / Tool Calls 🔧

**What:** Structured tool arguments (TypedDict) models use to call external tools (e.g., to update memory).
**Example:** `UpdateMemory` TypedDict in `module-6/deployment/task_maistro.py`, and `message.tool_calls` inspected there.

```python
class UpdateMemory(TypedDict):
    update_type: Literal['user', 'todo', 'instructions']

# Accessing tool calls
tool_calls = state['messages'][-1].tool_calls
```

---

### merge_message_runs 🔀

**What:** Utility to combine fragmented message runs into a coherent history before calling extractors or tools.
**Example:** Used in `module-6/deployment/task_maistro.py` when preparing messages for Trustcall extractors.

```python
updated_messages = list(merge_message_runs(messages=[SystemMessage(content=TRUSTCALL_INSTRUCTION_FORMATTED)] + state["messages"][:-1]))
```

---

## Execution Control & Debugging 🛠️

### NodeInterrupt & Breakpoints ⛔

**What:** NodeInterrupt is an exception used to pause/interrupt a node (useful for dynamic breakpoints / human-in-the-loop).
**Example:** `module-3/studio/dynamic_breakpoints.py` demonstrates raising `NodeInterrupt`.

```python
from langgraph.errors import NodeInterrupt
if len(state['input']) > 5:
    raise NodeInterrupt("Received input that is longer than 5 characters")
```

---

## Agents, Tools & Models 🤖

### Agent / Tool / RunnableConfig ⚙️

**What:** Agents orchestrate graphs, call tools (structured `tool_calls`), and use `RunnableConfig` to pass runtime config.
**Example:** Task mAIstro (`module-6/deployment/task_maistro.py`) shows `RunnableConfig` usage and tool-backed extractors.

```python
def task_mAIstro(state: MessagesState, config: RunnableConfig, store: BaseStore):
    configurable = configuration.Configuration.from_runnable_config(config)
```

---

## Where to look for more examples 🔎

- Chat & message flows: `module-1/studio/simple.py`, `module-2/studio/chatbot.py`, `module-2/chatbot-external-memory.ipynb`.
- Persistent memory & checkpointers: `module-2/chatbot-external-memory.ipynb`, `module-6/deployment/task_maistro.py`.
- Breakpoints & NodeInterrupt: `module-3/studio/dynamic_breakpoints.py`.

---

If you'd like, I can:

1. Add short links (file:line ranges) per item for quick navigation, or
2. Create a printable PDF from this Markdown.

Pick one and I’ll proceed. ✨
