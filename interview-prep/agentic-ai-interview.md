# Agentic AI — Interview Questions

100 interview practice questions and concise answers. Product and runtime behavior can vary; check current documentation.

## 1. What does agentic AI mean?

It describes systems in which a model helps choose actions toward a goal using feedback. The term varies, so specify the available tools, decision freedom, state, and stopping conditions rather than relying on the label.

**Remember:** Explain the tradeoff using a concrete example; distinguish guarantees from assumptions.

## 2. How does an agent differ from a workflow?

A workflow follows predefined control paths, while an agent can choose its next steps dynamically. Use the simplest approach that meets the task; dynamic control increases flexibility and the evaluation burden.

**Remember:** Explain the tradeoff using a concrete example; distinguish guarantees from assumptions.

## 3. When should you avoid an agent?

Avoid one when deterministic code or a fixed workflow is sufficient, or when errors cannot be contained. An agent should earn its additional latency, cost, and operational complexity through measured task success.

**Remember:** Explain the tradeoff using a concrete example; distinguish guarantees from assumptions.

## 4. What is a plan-act-observe loop?

The system chooses a step, invokes an allowed action, inspects the result, and updates its next decision. Bound iterations, time, cost, and permissions so the loop cannot run indefinitely.

**Remember:** Explain the tradeoff using a concrete example; distinguish guarantees from assumptions.

## 5. What is tool calling?

A model proposes a structured tool name and arguments; application code validates and executes the request. A tool call is not inherently trusted, and the model should not receive credentials just to request an action.

**Remember:** Explain the tradeoff using a concrete example; distinguish guarantees from assumptions.

## 6. How do you design a good tool schema?

Define one clear purpose, typed fields, required arguments, constraints, and understandable error outputs. Prefer narrow operations over an unrestricted shell or database tool when the task permits it.

**Remember:** Explain the tradeoff using a concrete example; distinguish guarantees from assumptions.

## 7. What is an autonomy boundary?

It defines which decisions and actions the system may take without human approval. Express it in executable policies, permissions, and budgets, with explicit review for consequential actions.

**Remember:** Explain the tradeoff using a concrete example; distinguish guarantees from assumptions.

## 8. What is human-in-the-loop control?

A person reviews a specific decision or action before execution or at a defined checkpoint. Present the exact proposed effect and preserve its identity so approval cannot accidentally authorize a changed action.

**Remember:** Explain the tradeoff using a concrete example; distinguish guarantees from assumptions.

## 9. How should an agent handle tool failures?

Classify errors as transient, invalid input, permission failure, or permanent failure. Retry only appropriate operations with bounds and backoff, and escalate when a safe recovery is unavailable.

**Remember:** Explain the tradeoff using a concrete example; distinguish guarantees from assumptions.

## 10. How do you prevent infinite agent loops?

Enforce iteration and time limits, detect repeated equivalent calls, and require progress signals. Return a clear partial result and reason for stopping instead of consuming the entire budget silently.

**Remember:** Explain the tradeoff using a concrete example; distinguish guarantees from assumptions.

## 11. How do you measure agent success?

Measure task completion, correctness, policy compliance, intervention rate, latency, and cost across realistic scenarios. Evaluate complete trajectories and side effects, not only the final answer's wording.

**Remember:** Explain the tradeoff using a concrete example; distinguish guarantees from assumptions.

## 12. What is trajectory evaluation?

It examines intermediate decisions, tool arguments, observations, and final outcomes. This reveals cases where an acceptable-looking answer hides unnecessary actions, unauthorized access, or fragile recovery behavior.

**Remember:** Explain the tradeoff using a concrete example; distinguish guarantees from assumptions.

## 13. What is prompt injection in an agent?

Untrusted content attempts to redirect the model's instructions or actions. Treat tool outputs and documents as data, enforce permissions outside the model, and isolate secrets from content the model can expose.

**Remember:** Explain the tradeoff using a concrete example; distinguish guarantees from assumptions.

## 14. How do you control agent cost?

Set task budgets for model calls, tokens, tools, and execution time. Use simpler routes when sufficient, cache safe repeat work, and monitor cost per successful task rather than cost per call alone.

**Remember:** Explain the tradeoff using a concrete example; distinguish guarantees from assumptions.

## 15. What is checkpointing?

Checkpointing saves execution state at defined boundaries so a run can resume after interruption. Include completed side effects and idempotency keys to prevent replay from duplicating real actions.

**Remember:** Explain the tradeoff using a concrete example; distinguish guarantees from assumptions.

## 16. How do you make agent actions auditable?

Record structured events with request IDs, decisions, policy checks, tool calls, and outcomes. Redact sensitive data and retain useful evidence without assuming private reasoning traces are required.

**Remember:** Explain the tradeoff using a concrete example; distinguish guarantees from assumptions.

## 17. What is an evaluator-optimizer pattern?

One component proposes a result and another assesses it against explicit criteria before revision. Cap revision cycles and independently verify objective requirements; an evaluator can also be wrong.

**Remember:** Explain the tradeoff using a concrete example; distinguish guarantees from assumptions.

## 18. What is routing in an AI system?

Routing selects a model, tool, or workflow based on the request. Validate the route and fallback behavior, and ensure routing never weakens the user's authorization boundaries.

**Remember:** Explain the tradeoff using a concrete example; distinguish guarantees from assumptions.

## 19. How do you deploy agent changes safely?

Version models, prompts, tools, and policies; run regression evaluations before a canary rollout. Monitor task success and harmful side effects with a fast rollback path.

**Remember:** Explain the tradeoff using a concrete example; distinguish guarantees from assumptions.

## 20. How would you design a customer-support agent?

Start with scoped retrieval and read-only account tools, authenticate the customer, and cite relevant policy. Add narrowly permitted actions with validation, approval where needed, escalation, and end-to-end evaluation.

**Remember:** Explain the tradeoff using a concrete example; distinguish guarantees from assumptions.

## 21. Explain risk-based action controls in Agentic AI.

Actions need controls proportional to consequence and reversibility. Enforce action policies and permissions in server code.

**Remember:** Model-generated risk labels cannot be the only gate.

## 22. How would you apply risk-based action controls in a practical Agentic AI task?

Enforce action policies and permissions in server code. Actions need controls proportional to consequence and reversibility.

**Remember:** Test denied actions and attempts to bypass approval.

## 23. What mistake should you avoid with risk-based action controls in Agentic AI?

Model-generated risk labels cannot be the only gate. Enforce action policies and permissions in server code.

**Remember:** Actions need controls proportional to consequence and reversibility.

## 24. How would you verify risk-based action controls in a Agentic AI implementation?

Test denied actions and attempts to bypass approval. Model-generated risk labels cannot be the only gate.

**Remember:** Enforce action policies and permissions in server code.

## 25. Explain approval binding in Agentic AI.

Approval must refer to the exact executable action. Bind identity, payload, expiry, and operation ID.

**Remember:** Changing arguments after approval can invalidate consent.

## 26. How would you apply approval binding in a practical Agentic AI task?

Bind identity, payload, expiry, and operation ID. Approval must refer to the exact executable action.

**Remember:** Test replay, expiry, and payload modification.

## 27. What mistake should you avoid with approval binding in Agentic AI?

Changing arguments after approval can invalidate consent. Bind identity, payload, expiry, and operation ID.

**Remember:** Approval must refer to the exact executable action.

## 28. How would you verify approval binding in a Agentic AI implementation?

Test replay, expiry, and payload modification. Changing arguments after approval can invalidate consent.

**Remember:** Bind identity, payload, expiry, and operation ID.

## 29. Explain budget-aware planning in Agentic AI.

Plans must fit finite time, tokens, and tool costs. Allocate budgets and simplify when limits approach.

**Remember:** Excessive planning can consume the budget without useful progress.

## 30. How would you apply budget-aware planning in a practical Agentic AI task?

Allocate budgets and simplify when limits approach. Plans must fit finite time, tokens, and tool costs.

**Remember:** Measure success per budget and graceful partial completion.

## 31. What mistake should you avoid with budget-aware planning in Agentic AI?

Excessive planning can consume the budget without useful progress. Allocate budgets and simplify when limits approach.

**Remember:** Plans must fit finite time, tokens, and tool costs.

## 32. How would you verify budget-aware planning in a Agentic AI implementation?

Measure success per budget and graceful partial completion. Excessive planning can consume the budget without useful progress.

**Remember:** Allocate budgets and simplify when limits approach.

## 33. Explain execution state machines in Agentic AI.

Explicit states constrain valid task transitions. Encode transitions and terminal outcomes deterministically.

**Remember:** Free-form status can hide duplicate side effects.

## 34. How would you apply execution state machines in a practical Agentic AI task?

Encode transitions and terminal outcomes deterministically. Explicit states constrain valid task transitions.

**Remember:** Test out-of-order events and duplicate completions.

## 35. What mistake should you avoid with execution state machines in Agentic AI?

Free-form status can hide duplicate side effects. Encode transitions and terminal outcomes deterministically.

**Remember:** Explicit states constrain valid task transitions.

## 36. How would you verify execution state machines in a Agentic AI implementation?

Test out-of-order events and duplicate completions. Free-form status can hide duplicate side effects.

**Remember:** Encode transitions and terminal outcomes deterministically.

## 37. Explain uncertainty escalation in Agentic AI.

Escalation requests help when evidence or authority is insufficient. Define triggers for missing inputs and conflicting permissions.

**Remember:** Unnecessary clarification can block authorized work.

## 38. How would you apply uncertainty escalation in a practical Agentic AI task?

Define triggers for missing inputs and conflicting permissions. Escalation requests help when evidence or authority is insufficient.

**Remember:** Measure missed and excessive escalations separately.

## 39. What mistake should you avoid with uncertainty escalation in Agentic AI?

Unnecessary clarification can block authorized work. Define triggers for missing inputs and conflicting permissions.

**Remember:** Escalation requests help when evidence or authority is insufficient.

## 40. How would you verify uncertainty escalation in a Agentic AI implementation?

Measure missed and excessive escalations separately. Unnecessary clarification can block authorized work.

**Remember:** Define triggers for missing inputs and conflicting permissions.

## 41. Explain tool-output validation in Agentic AI.

Tool outputs need structural and task-specific checks. Validate types, required fields, and critical semantic constraints.

**Remember:** Valid JSON can still contain stale or malicious content.

## 42. How would you apply tool-output validation in a practical Agentic AI task?

Validate types, required fields, and critical semantic constraints. Tool outputs need structural and task-specific checks.

**Remember:** Inject malformed and inconsistent responses in tests.

## 43. What mistake should you avoid with tool-output validation in Agentic AI?

Valid JSON can still contain stale or malicious content. Validate types, required fields, and critical semantic constraints.

**Remember:** Tool outputs need structural and task-specific checks.

## 44. How would you verify tool-output validation in a Agentic AI implementation?

Inject malformed and inconsistent responses in tests. Valid JSON can still contain stale or malicious content.

**Remember:** Validate types, required fields, and critical semantic constraints.

## 45. Explain policy-aware planning in Agentic AI.

Every intermediate step must respect task constraints. Maintain structured constraints and check proposed actions.

**Remember:** A legitimate goal does not authorize every route to it.

## 46. How would you apply policy-aware planning in a practical Agentic AI task?

Maintain structured constraints and check proposed actions. Every intermediate step must respect task constraints.

**Remember:** Evaluate entire trajectories including failed steps.

## 47. What mistake should you avoid with policy-aware planning in Agentic AI?

A legitimate goal does not authorize every route to it. Maintain structured constraints and check proposed actions.

**Remember:** Every intermediate step must respect task constraints.

## 48. How would you verify policy-aware planning in a Agentic AI implementation?

Evaluate entire trajectories including failed steps. A legitimate goal does not authorize every route to it.

**Remember:** Maintain structured constraints and check proposed actions.

## 49. Explain shadow deployment in Agentic AI.

Shadow mode proposes actions without changing production state. Compare read-only proposals with trusted decisions.

**Remember:** It cannot prove real side-effect recovery.

## 50. How would you apply shadow deployment in a practical Agentic AI task?

Compare read-only proposals with trusted decisions. Shadow mode proposes actions without changing production state.

**Remember:** Evaluate proposals first and execution separately in an isolated environment.

## 51. What mistake should you avoid with shadow deployment in Agentic AI?

It cannot prove real side-effect recovery. Compare read-only proposals with trusted decisions.

**Remember:** Shadow mode proposes actions without changing production state.

## 52. How would you verify shadow deployment in a Agentic AI implementation?

Evaluate proposals first and execution separately in an isolated environment. It cannot prove real side-effect recovery.

**Remember:** Compare read-only proposals with trusted decisions.

## 53. Explain canary releases in Agentic AI.

Canaries limit exposure to a new agent configuration. Use small cohorts and explicit rollback thresholds.

**Remember:** Aggregate success can conceal rare consequential failures.

## 54. How would you apply canary releases in a practical Agentic AI task?

Use small cohorts and explicit rollback thresholds. Canaries limit exposure to a new agent configuration.

**Remember:** Compare slices and inspect high-risk actions before expansion.

## 55. What mistake should you avoid with canary releases in Agentic AI?

Aggregate success can conceal rare consequential failures. Use small cohorts and explicit rollback thresholds.

**Remember:** Canaries limit exposure to a new agent configuration.

## 56. How would you verify canary releases in a Agentic AI implementation?

Compare slices and inspect high-risk actions before expansion. Aggregate success can conceal rare consequential failures.

**Remember:** Use small cohorts and explicit rollback thresholds.

## 57. Explain kill switches in Agentic AI.

A kill switch disables autonomous execution. Enforce server-side revocation before tools and long-running steps.

**Remember:** A UI-only switch may leave workers running.

## 58. How would you apply kill switches in a practical Agentic AI task?

Enforce server-side revocation before tools and long-running steps. A kill switch disables autonomous execution.

**Remember:** Verify cancellation propagation and prevention of new actions.

## 59. What mistake should you avoid with kill switches in Agentic AI?

A UI-only switch may leave workers running. Enforce server-side revocation before tools and long-running steps.

**Remember:** A kill switch disables autonomous execution.

## 60. How would you verify kill switches in a Agentic AI implementation?

Verify cancellation propagation and prevention of new actions. A UI-only switch may leave workers running.

**Remember:** Enforce server-side revocation before tools and long-running steps.

## 61. Explain decomposition quality in Agentic AI.

Useful subtasks have explicit inputs, outputs, and dependencies. Define acceptance criteria and integration ownership.

**Remember:** Too many tiny tasks increase coordination failures.

## 62. How would you apply decomposition quality in a practical Agentic AI task?

Define acceptance criteria and integration ownership. Useful subtasks have explicit inputs, outputs, and dependencies.

**Remember:** Compare completion quality and overhead with a simpler baseline.

## 63. What mistake should you avoid with decomposition quality in Agentic AI?

Too many tiny tasks increase coordination failures. Define acceptance criteria and integration ownership.

**Remember:** Useful subtasks have explicit inputs, outputs, and dependencies.

## 64. How would you verify decomposition quality in a Agentic AI implementation?

Compare completion quality and overhead with a simpler baseline. Too many tiny tasks increase coordination failures.

**Remember:** Define acceptance criteria and integration ownership.

## 65. Explain parallel execution in Agentic AI.

Independent work can run concurrently within controlled boundaries. Parallelize isolated reads and serialize dependent mutations.

**Remember:** Concurrent writes can overwrite state or duplicate effects.

## 66. How would you apply parallel execution in a practical Agentic AI task?

Parallelize isolated reads and serialize dependent mutations. Independent work can run concurrently within controlled boundaries.

**Remember:** Test races and measure actual wall-clock savings.

## 67. What mistake should you avoid with parallel execution in Agentic AI?

Concurrent writes can overwrite state or duplicate effects. Parallelize isolated reads and serialize dependent mutations.

**Remember:** Independent work can run concurrently within controlled boundaries.

## 68. How would you verify parallel execution in a Agentic AI implementation?

Test races and measure actual wall-clock savings. Concurrent writes can overwrite state or duplicate effects.

**Remember:** Parallelize isolated reads and serialize dependent mutations.

## 69. Explain completion criteria in Agentic AI.

Completion should reflect satisfied requirements or explicit stopping limits. Verify external state against predetermined checks.

**Remember:** An agent may declare success based on a convincing narrative.

## 70. How would you apply completion criteria in a practical Agentic AI task?

Verify external state against predetermined checks. Completion should reflect satisfied requirements or explicit stopping limits.

**Remember:** Use independent acceptance checks rather than final wording alone.

## 71. What mistake should you avoid with completion criteria in Agentic AI?

An agent may declare success based on a convincing narrative. Verify external state against predetermined checks.

**Remember:** Completion should reflect satisfied requirements or explicit stopping limits.

## 72. How would you verify completion criteria in a Agentic AI implementation?

Use independent acceptance checks rather than final wording alone. An agent may declare success based on a convincing narrative.

**Remember:** Verify external state against predetermined checks.

## 73. Explain adversarial evaluation in Agentic AI.

Adversarial cases probe injection and permission boundaries. Include credential, authority, and destructive-action attacks.

**Remember:** A static test set may miss evolving attack patterns.

## 74. How would you apply adversarial evaluation in a practical Agentic AI task?

Include credential, authority, and destructive-action attacks. Adversarial cases probe injection and permission boundaries.

**Remember:** Maintain fresh holdouts and generalize from discovered failures.

## 75. What mistake should you avoid with adversarial evaluation in Agentic AI?

A static test set may miss evolving attack patterns. Include credential, authority, and destructive-action attacks.

**Remember:** Adversarial cases probe injection and permission boundaries.

## 76. How would you verify adversarial evaluation in a Agentic AI implementation?

Maintain fresh holdouts and generalize from discovered failures. A static test set may miss evolving attack patterns.

**Remember:** Include credential, authority, and destructive-action attacks.

## 77. Explain model routing in Agentic AI.

Routing assigns stages to models suited to their requirements. Define measured capability needs and fallback rules.

**Remember:** Cheap calls can increase total cost through retries.

## 78. How would you apply model routing in a practical Agentic AI task?

Define measured capability needs and fallback rules. Routing assigns stages to models suited to their requirements.

**Remember:** Compare quality and cost per completed task by route.

## 79. What mistake should you avoid with model routing in Agentic AI?

Cheap calls can increase total cost through retries. Define measured capability needs and fallback rules.

**Remember:** Routing assigns stages to models suited to their requirements.

## 80. How would you verify model routing in a Agentic AI implementation?

Compare quality and cost per completed task by route. Cheap calls can increase total cost through retries.

**Remember:** Define measured capability needs and fallback rules.

## 81. Explain data minimization in Agentic AI.

Agents should receive only information required for the task. Redact unnecessary fields before model access.

**Remember:** Equivalent sensitive identifiers may remain in other fields.

## 82. How would you apply data minimization in a practical Agentic AI task?

Redact unnecessary fields before model access. Agents should receive only information required for the task.

**Remember:** Audit prompts, outputs, tool arguments, and logs.

## 83. What mistake should you avoid with data minimization in Agentic AI?

Equivalent sensitive identifiers may remain in other fields. Redact unnecessary fields before model access.

**Remember:** Agents should receive only information required for the task.

## 84. How would you verify data minimization in a Agentic AI implementation?

Audit prompts, outputs, tool arguments, and logs. Equivalent sensitive identifiers may remain in other fields.

**Remember:** Redact unnecessary fields before model access.

## 85. Explain deterministic components in Agentic AI.

Ordinary code provides reliable validation and fixed operations. Use code for arithmetic, authorization, and known sequencing.

**Remember:** Model-driven replacements add variability without guaranteed benefit.

## 86. How would you apply deterministic components in a practical Agentic AI task?

Use code for arithmetic, authorization, and known sequencing. Ordinary code provides reliable validation and fixed operations.

**Remember:** Compare reproducibility and failure rates with the coded baseline.

## 87. What mistake should you avoid with deterministic components in Agentic AI?

Model-driven replacements add variability without guaranteed benefit. Use code for arithmetic, authorization, and known sequencing.

**Remember:** Ordinary code provides reliable validation and fixed operations.

## 88. How would you verify deterministic components in a Agentic AI implementation?

Compare reproducibility and failure rates with the coded baseline. Model-driven replacements add variability without guaranteed benefit.

**Remember:** Use code for arithmetic, authorization, and known sequencing.

## 89. Explain service-level objectives in Agentic AI.

SLOs define acceptable quality and operational outcomes. Track success, latency, cost, and policy violations over explicit windows.

**Remember:** Latency-only goals can reward fast wrong answers.

## 90. How would you apply service-level objectives in a practical Agentic AI task?

Track success, latency, cost, and policy violations over explicit windows. SLOs define acceptable quality and operational outcomes.

**Remember:** Monitor violations and use error budgets for rollout decisions.

## 91. What mistake should you avoid with service-level objectives in Agentic AI?

Latency-only goals can reward fast wrong answers. Track success, latency, cost, and policy violations over explicit windows.

**Remember:** SLOs define acceptable quality and operational outcomes.

## 92. How would you verify service-level objectives in a Agentic AI implementation?

Monitor violations and use error budgets for rollout decisions. Latency-only goals can reward fast wrong answers.

**Remember:** Track success, latency, cost, and policy violations over explicit windows.

## 93. Explain configuration rollback in Agentic AI.

Rollback restores a compatible model, prompt, tool, and policy bundle. Version the full configuration and test reverting it.

**Remember:** Prompt rollback cannot undo already-completed actions.

## 94. How would you apply configuration rollback in a practical Agentic AI task?

Version the full configuration and test reverting it. Rollback restores a compatible model, prompt, tool, and policy bundle.

**Remember:** Test configuration recovery separately from compensation.

## 95. What mistake should you avoid with configuration rollback in Agentic AI?

Prompt rollback cannot undo already-completed actions. Version the full configuration and test reverting it.

**Remember:** Rollback restores a compatible model, prompt, tool, and policy bundle.

## 96. How would you verify configuration rollback in a Agentic AI implementation?

Test configuration recovery separately from compensation. Prompt rollback cannot undo already-completed actions.

**Remember:** Version the full configuration and test reverting it.

## 97. Explain evaluation dataset design in Agentic AI.

Evaluation cases need expected outcomes and allowed behavior. Version realistic examples and independent holdouts.

**Remember:** Repeated tuning on the holdout causes overfitting.

## 98. How would you apply evaluation dataset design in a practical Agentic AI task?

Version realistic examples and independent holdouts. Evaluation cases need expected outcomes and allowed behavior.

**Remember:** Report performance on fresh cases collected after configuration freeze.

## 99. What mistake should you avoid with evaluation dataset design in Agentic AI?

Repeated tuning on the holdout causes overfitting. Version realistic examples and independent holdouts.

**Remember:** Evaluation cases need expected outcomes and allowed behavior.

## 100. How would you verify evaluation dataset design in a Agentic AI implementation?

Report performance on fresh cases collected after configuration freeze. Repeated tuning on the holdout causes overfitting.

**Remember:** Version realistic examples and independent holdouts.

## Further reading

- [Agent patterns](https://www.anthropic.com/research/building-effective-agents)
