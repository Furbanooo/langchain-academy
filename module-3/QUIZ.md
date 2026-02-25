# Module 3 — Quiz

1. What is the purpose of `NodeInterrupt`?
   Answer: It intentionally pauses a graph at a specific node so you can inspect or change state before continuing. It makes debugging and human-in-the-loop flows safe and explicit instead of relying on ad-hoc logging or guessing where the run went wrong.
2. How do dynamic breakpoints differ from static breakpoints?
   Answer: Static breakpoints are fixed at design time and always trigger at the same location. Dynamic breakpoints are set or changed at runtime based on conditions (for example, only when confidence is low or when a tool call looks suspicious), so they are more flexible for targeted debugging.
3. Why would you edit state during a run?
   Answer: To fix or refine what the graph will do next without restarting the whole run. This can correct a bad tool response, add missing context, adjust a summary, or inject human feedback so downstream nodes act on the right data.
4. What does time travel enable in debugging workflows?
   Answer: It lets you rewind to a prior step, inspect the exact state at that moment, and resume from there with changes. This enables repeatable debugging by exploring alternate choices from a known good checkpoint rather than rerunning the entire workflow.
5. What are the risks of resuming with inconsistent state?
   Answer: It can produce wrong or non-deterministic results because nodes rely on invariants (like required fields, ordering of messages, or tool-call pairing). It can also cause duplicated side effects (e.g., writing to a database twice) or crashes when expected inputs are missing.
6. When is streaming interruption useful?
   Answer: When you want to stop a response mid-generation to inspect partial output, intervene, or adjust state before continuing. It helps you steer or debug long responses without waiting for the entire node to finish.

## Additional Questions

7. What invariants should you check before resuming a paused run?
8. How can you make tool side effects safe when a run is resumed?
9. What is the difference between replaying from a checkpoint and editing state in-place?
10. When would you choose a dynamic breakpoint over a `NodeInterrupt`?
11. What data should be included in a state snapshot to make time travel effective?
12. How does message ordering affect tool-call correctness in a message-based state?
13. What kinds of bugs are hardest to detect after a resume with inconsistent state?
14. How would you design a state schema to minimize invalid transitions?
15. What are common signals that a stream should be interrupted early?
16. How can you validate a run’s state before allowing it to continue?
17. What role does human feedback play in debugging runs with interruptions?
18. How does streaming interruption differ from parallel branching or map-reduce patterns?
