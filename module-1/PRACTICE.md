# Module 1 — Practice

1. Design a mini “routing assistant” project: define the user roles, the intents you will support, and the criteria for routing between nodes. Sketch the graph and explain the decision logic in words.
2. Extend the agent in [module-1/agent.ipynb](../module-1/agent.ipynb) by planning a new capability (tool or sub-flow). Describe the input/output contract, where it should be called, and how it changes the user experience.
3. Create a conceptual comparison project: take a real-world flow (e.g., onboarding, support triage, or order tracking) and map it once as a linear chain and once as a graph. Explain the tradeoffs and why each design would be chosen.
4. Add a state field to represent “decision rationale.” Define what data it should hold, when it updates, and how it helps debugging or observability.
5. Use the memory example in [module-1/agent-memory.ipynb](../module-1/agent-memory.ipynb) to articulate a memory policy: what should persist, for how long, and why. Document at least two failure modes if the policy is wrong.
