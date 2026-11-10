# AI Agents — Interview Questions

100 interview practice questions and concise answers. Product and runtime behavior can vary; check current documentation.

## 1. What components make up an AI agent?

Typical components are a model, instructions, tools, state, and a control loop. Production systems also need authorization, observability, evaluation, and explicit termination behavior.

**Remember:** Explain the tradeoff using a concrete example; distinguish guarantees from assumptions.

## 2. What is short-term versus long-term memory?

Short-term memory holds current task context; long-term memory persists information across tasks. Persist only useful, consented data with provenance, expiry, and deletion controls.

**Remember:** Explain the tradeoff using a concrete example; distinguish guarantees from assumptions.

## 3. How do you manage limited context?

Keep relevant recent state, summarize older material with source references, and retrieve details when needed. Preserve constraints and unresolved actions so summarization does not silently change the task.

**Remember:** Explain the tradeoff using a concrete example; distinguish guarantees from assumptions.

## 4. When are multiple agents useful?

They can help when work splits into independent specialties or parallel subtasks. Compare against a single-agent baseline because coordination overhead and conflicting outputs can reduce reliability.

**Remember:** Explain the tradeoff using a concrete example; distinguish guarantees from assumptions.

## 5. What is an orchestrator-worker design?

An orchestrator assigns bounded work to workers and integrates their results. Define ownership, inputs, outputs, and verification so delegation does not create duplicated actions or inconsistent state.

**Remember:** Explain the tradeoff using a concrete example; distinguish guarantees from assumptions.

## 6. How do agents share state safely?

Use explicit structured state with access controls and concurrency rules. Version updates or use transactions where needed, and prevent a worker from overwriting another worker's newer result.

**Remember:** Explain the tradeoff using a concrete example; distinguish guarantees from assumptions.

## 7. What is an agent handoff?

A handoff transfers responsibility along with relevant context and constraints. Include completed actions, remaining work, permissions, and a clear return or escalation path.

**Remember:** Explain the tradeoff using a concrete example; distinguish guarantees from assumptions.

## 8. How do you avoid duplicate tool actions?

Use idempotency keys, persistent execution records, and transaction boundaries. Before retrying an uncertain action, query its status rather than assuming it did not happen.

**Remember:** Explain the tradeoff using a concrete example; distinguish guarantees from assumptions.

## 9. What is a structured output?

It is output constrained to a defined schema rather than free-form prose. Validate it in application code; syntactic validity does not guarantee semantic correctness or permission to execute it.

**Remember:** Explain the tradeoff using a concrete example; distinguish guarantees from assumptions.

## 10. What is a tool allowlist?

It explicitly limits available operations for a given task and identity. Combine it with argument validation and backend access checks; exposing a tool name should not confer unrestricted access.

**Remember:** Explain the tradeoff using a concrete example; distinguish guarantees from assumptions.

## 11. How should an agent use external APIs?

Use server-managed credentials, scoped access, input validation, timeouts, and rate limits. Treat returned content as untrusted and avoid logging tokens or unnecessary personal data.

**Remember:** Explain the tradeoff using a concrete example; distinguish guarantees from assumptions.

## 12. How do you handle API rate limits?

Apply bounded exponential backoff with jitter where safe, respect retry guidance, and queue work within task deadlines. Use concurrency limits and report partial completion if the deadline cannot be met.

**Remember:** Explain the tradeoff using a concrete example; distinguish guarantees from assumptions.

## 13. What is durable execution?

Durable execution preserves state and progress across process failures or long waits. It needs clear replay semantics and side-effect handling; simply saving a chat transcript is insufficient.

**Remember:** Explain the tradeoff using a concrete example; distinguish guarantees from assumptions.

## 14. How do you sandbox code-executing agents?

Use isolated execution with limited filesystem and network access, resource quotas, and short-lived credentials where required. Keep permission enforcement outside the generated code.

**Remember:** Explain the tradeoff using a concrete example; distinguish guarantees from assumptions.

## 15. How do you test a tool-using agent?

Test schema errors, denied permissions, timeouts, repeated calls, malicious results, and successful tasks. Use controlled tools or test environments and verify final state as well as messages.

**Remember:** Explain the tradeoff using a concrete example; distinguish guarantees from assumptions.

## 16. What should happen when agents disagree?

Resolve disagreements using evidence, deterministic checks, or human review according to task risk. Majority vote alone does not establish truth when agents share the same blind spot.

**Remember:** Explain the tradeoff using a concrete example; distinguish guarantees from assumptions.

## 17. How do you build a research agent?

Define scope and source criteria, search and retrieve within bounds, track claim-level provenance, and verify citations. Make uncertainty visible and prevent retrieved pages from changing the agent's instructions.

**Remember:** Explain the tradeoff using a concrete example; distinguish guarantees from assumptions.

## 18. How do you build a coding agent safely?

Provide a constrained repository, clear acceptance criteria, and appropriate test tools. Review diffs and dependencies, protect secrets, and gate production side effects according to policy.

**Remember:** Explain the tradeoff using a concrete example; distinguish guarantees from assumptions.

## 19. How do you personalize an agent responsibly?

Use explicit preferences and minimal relevant history with user controls. Separate preferences from instructions that authorize actions, and avoid inferring sensitive traits without a legitimate need.

**Remember:** Explain the tradeoff using a concrete example; distinguish guarantees from assumptions.

## 20. How would you investigate an agent incident?

Contain further actions, preserve redacted execution evidence, and identify the affected users and side effects. Fix the root policy or implementation issue and add a representative regression before restoring autonomy.

**Remember:** Explain the tradeoff using a concrete example; distinguish guarantees from assumptions.

## 21. Explain session isolation in Agents.

Different users and tasks need separate authorized state. Bind memory, credentials, caches, and execution IDs to identity.

**Remember:** A global chat buffer can leak another user's information.

## 22. How would you apply session isolation in a practical Agents task?

Bind memory, credentials, caches, and execution IDs to identity. Different users and tasks need separate authorized state.

**Remember:** Interleave sessions and verify state never crosses boundaries.

## 23. What mistake should you avoid with session isolation in Agents?

A global chat buffer can leak another user's information. Bind memory, credentials, caches, and execution IDs to identity.

**Remember:** Different users and tasks need separate authorized state.

## 24. How would you verify session isolation in a Agents implementation?

Interleave sessions and verify state never crosses boundaries. A global chat buffer can leak another user's information.

**Remember:** Bind memory, credentials, caches, and execution IDs to identity.

## 25. Explain working-memory summaries in Agents.

Summaries compress context while preserving decisions and constraints. Retain unresolved work, side effects, preferences, and source references.

**Remember:** Omitted restrictions can change resumed behavior.

## 26. How would you apply working-memory summaries in a practical Agents task?

Retain unresolved work, side effects, preferences, and source references. Summaries compress context while preserving decisions and constraints.

**Remember:** Compare resumed tasks with full-context constraint-heavy tasks.

## 27. What mistake should you avoid with working-memory summaries in Agents?

Omitted restrictions can change resumed behavior. Retain unresolved work, side effects, preferences, and source references.

**Remember:** Summaries compress context while preserving decisions and constraints.

## 28. How would you verify working-memory summaries in a Agents implementation?

Compare resumed tasks with full-context constraint-heavy tasks. Omitted restrictions can change resumed behavior.

**Remember:** Retain unresolved work, side effects, preferences, and source references.

## 29. Explain memory provenance in Agents.

Stored facts need source, time, and trust metadata. Separate user instructions from observations and inferred preferences.

**Remember:** Untrusted content can become a persistent instruction.

## 30. How would you apply memory provenance in a practical Agents task?

Separate user instructions from observations and inferred preferences. Stored facts need source, time, and trust metadata.

**Remember:** Test memory poisoning and authority confusion in later runs.

## 31. What mistake should you avoid with memory provenance in Agents?

Untrusted content can become a persistent instruction. Separate user instructions from observations and inferred preferences.

**Remember:** Stored facts need source, time, and trust metadata.

## 32. How would you verify memory provenance in a Agents implementation?

Test memory poisoning and authority confusion in later runs. Untrusted content can become a persistent instruction.

**Remember:** Separate user instructions from observations and inferred preferences.

## 33. Explain memory expiry in Agents.

Stored information can become stale or unnecessary. Apply retention and refresh time-sensitive facts.

**Remember:** Old preferences do not establish current action authorization.

## 34. How would you apply memory expiry in a practical Agents task?

Apply retention and refresh time-sensitive facts. Stored information can become stale or unnecessary.

**Remember:** Test expiry, deletion, and preference changes across sessions.

## 35. What mistake should you avoid with memory expiry in Agents?

Old preferences do not establish current action authorization. Apply retention and refresh time-sensitive facts.

**Remember:** Stored information can become stale or unnecessary.

## 36. How would you verify memory expiry in a Agents implementation?

Test expiry, deletion, and preference changes across sessions. Old preferences do not establish current action authorization.

**Remember:** Apply retention and refresh time-sensitive facts.

## 37. Explain tool pagination in Agents.

Large results require explicit continuation. Follow returned cursors within task limits and record completeness.

**Remember:** The first page can be mistaken for the full dataset.

## 38. How would you apply tool pagination in a practical Agents task?

Follow returned cursors within task limits and record completeness. Large results require explicit continuation.

**Remember:** Use multi-page fixtures and verify totals and continuation.

## 39. What mistake should you avoid with tool pagination in Agents?

The first page can be mistaken for the full dataset. Follow returned cursors within task limits and record completeness.

**Remember:** Large results require explicit continuation.

## 40. How would you verify tool pagination in a Agents implementation?

Use multi-page fixtures and verify totals and continuation. The first page can be mistaken for the full dataset.

**Remember:** Follow returned cursors within task limits and record completeness.

## 41. Explain tool discovery in Agents.

Discovery identifies available operations and contracts. Read metadata and expose only task-relevant tools.

**Remember:** Similar names can conceal different side effects.

## 42. How would you apply tool discovery in a practical Agents task?

Read metadata and expose only task-relevant tools. Discovery identifies available operations and contracts.

**Remember:** Test ambiguous requests and validate tool selection.

## 43. What mistake should you avoid with tool discovery in Agents?

Similar names can conceal different side effects. Read metadata and expose only task-relevant tools.

**Remember:** Discovery identifies available operations and contracts.

## 44. How would you verify tool discovery in a Agents implementation?

Test ambiguous requests and validate tool selection. Similar names can conceal different side effects.

**Remember:** Read metadata and expose only task-relevant tools.

## 45. Explain dependency scheduling in Agents.

Some steps must wait for prerequisites. Represent dependencies and schedule only ready work.

**Remember:** Early execution may use invented inputs.

## 46. How would you apply dependency scheduling in a practical Agents task?

Represent dependencies and schedule only ready work. Some steps must wait for prerequisites.

**Remember:** Test failed prerequisites and downstream cancellation.

## 47. What mistake should you avoid with dependency scheduling in Agents?

Early execution may use invented inputs. Represent dependencies and schedule only ready work.

**Remember:** Some steps must wait for prerequisites.

## 48. How would you verify dependency scheduling in a Agents implementation?

Test failed prerequisites and downstream cancellation. Early execution may use invented inputs.

**Remember:** Represent dependencies and schedule only ready work.

## 49. Explain artifact ownership in Agents.

Shared output needs clear edit responsibility. Assign files or sections and integrate controlled changes.

**Remember:** Concurrent edits may silently discard another worker's work.

## 50. How would you apply artifact ownership in a practical Agents task?

Assign files or sections and integrate controlled changes. Shared output needs clear edit responsibility.

**Remember:** Verify diffs include all expected contributions.

## 51. What mistake should you avoid with artifact ownership in Agents?

Concurrent edits may silently discard another worker's work. Assign files or sections and integrate controlled changes.

**Remember:** Shared output needs clear edit responsibility.

## 52. How would you verify artifact ownership in a Agents implementation?

Verify diffs include all expected contributions. Concurrent edits may silently discard another worker's work.

**Remember:** Assign files or sections and integrate controlled changes.

## 53. Explain message contracts in Agents.

Structured messages distinguish tasks, results, and errors. Define IDs, schemas, provenance, and terminal statuses.

**Remember:** Tentative suggestions can be confused with completed work.

## 54. How would you apply message contracts in a practical Agents task?

Define IDs, schemas, provenance, and terminal statuses. Structured messages distinguish tasks, results, and errors.

**Remember:** Reject missing fields, mismatched IDs, and duplicate results.

## 55. What mistake should you avoid with message contracts in Agents?

Tentative suggestions can be confused with completed work. Define IDs, schemas, provenance, and terminal statuses.

**Remember:** Structured messages distinguish tasks, results, and errors.

## 56. How would you verify message contracts in a Agents implementation?

Reject missing fields, mismatched IDs, and duplicate results. Tentative suggestions can be confused with completed work.

**Remember:** Define IDs, schemas, provenance, and terminal statuses.

## 57. Explain task leases in Agents.

A lease grants time-limited ownership of work. Use atomic claims, expiry, and idempotent completion.

**Remember:** A stale worker may act after losing its lease.

## 58. How would you apply task leases in a practical Agents task?

Use atomic claims, expiry, and idempotent completion. A lease grants time-limited ownership of work.

**Remember:** Simulate delayed workers and reject stale commits.

## 59. What mistake should you avoid with task leases in Agents?

A stale worker may act after losing its lease. Use atomic claims, expiry, and idempotent completion.

**Remember:** A lease grants time-limited ownership of work.

## 60. How would you verify task leases in a Agents implementation?

Simulate delayed workers and reject stale commits. A stale worker may act after losing its lease.

**Remember:** Use atomic claims, expiry, and idempotent completion.

## 61. Explain tool timeouts in Agents.

Deadlines bound waiting time for tools. Use operation-specific timeouts and status queries.

**Remember:** A timed-out write may still succeed remotely.

## 62. How would you apply tool timeouts in a practical Agents task?

Use operation-specific timeouts and status queries. Deadlines bound waiting time for tools.

**Remember:** Test uncertain outcomes before allowing retries.

## 63. What mistake should you avoid with tool timeouts in Agents?

A timed-out write may still succeed remotely. Use operation-specific timeouts and status queries.

**Remember:** Deadlines bound waiting time for tools.

## 64. How would you verify tool timeouts in a Agents implementation?

Test uncertain outcomes before allowing retries. A timed-out write may still succeed remotely.

**Remember:** Use operation-specific timeouts and status queries.

## 65. Explain compensating actions in Agents.

Compensation corrects completed effects after partial failure. Define domain-specific inverse or corrective actions.

**Remember:** Some effects cannot be fully reversed.

## 66. How would you apply compensating actions in a practical Agents task?

Define domain-specific inverse or corrective actions. Compensation corrects completed effects after partial failure.

**Remember:** Test partial failures and document residual effects requiring review.

## 67. What mistake should you avoid with compensating actions in Agents?

Some effects cannot be fully reversed. Define domain-specific inverse or corrective actions.

**Remember:** Compensation corrects completed effects after partial failure.

## 68. How would you verify compensating actions in a Agents implementation?

Test partial failures and document residual effects requiring review. Some effects cannot be fully reversed.

**Remember:** Define domain-specific inverse or corrective actions.

## 69. Explain identity propagation in Agents.

Downstream tools need trustworthy user and service identity. Pass scoped identity through authenticated server channels.

**Remember:** Model-supplied user IDs can enable impersonation.

## 70. How would you apply identity propagation in a practical Agents task?

Pass scoped identity through authenticated server channels. Downstream tools need trustworthy user and service identity.

**Remember:** Attempt spoofing and verify backend ownership checks.

## 71. What mistake should you avoid with identity propagation in Agents?

Model-supplied user IDs can enable impersonation. Pass scoped identity through authenticated server channels.

**Remember:** Downstream tools need trustworthy user and service identity.

## 72. How would you verify identity propagation in a Agents implementation?

Attempt spoofing and verify backend ownership checks. Model-supplied user IDs can enable impersonation.

**Remember:** Pass scoped identity through authenticated server channels.

## 73. Explain notification policies in Agents.

Notifications require authorized recipients and useful triggers. Enforce channel, recipient, and deduplication rules outside generation.

**Remember:** Retries can send duplicate or speculative messages.

## 74. How would you apply notification policies in a practical Agents task?

Enforce channel, recipient, and deduplication rules outside generation. Notifications require authorized recipients and useful triggers.

**Remember:** Test recipient binding and unauthorized-send prevention.

## 75. What mistake should you avoid with notification policies in Agents?

Retries can send duplicate or speculative messages. Enforce channel, recipient, and deduplication rules outside generation.

**Remember:** Notifications require authorized recipients and useful triggers.

## 76. How would you verify notification policies in a Agents implementation?

Test recipient binding and unauthorized-send prevention. Retries can send duplicate or speculative messages.

**Remember:** Enforce channel, recipient, and deduplication rules outside generation.

## 77. Explain browser reliability in Agents.

Browser actions depend on current observed state. Use semantic targets and verify meaningful results.

**Remember:** Stale controls can trigger the wrong action.

## 78. How would you apply browser reliability in a practical Agents task?

Use semantic targets and verify meaningful results. Browser actions depend on current observed state.

**Remember:** Test delays, navigation changes, and confirmation dialogs.

## 79. What mistake should you avoid with browser reliability in Agents?

Stale controls can trigger the wrong action. Use semantic targets and verify meaningful results.

**Remember:** Browser actions depend on current observed state.

## 80. How would you verify browser reliability in a Agents implementation?

Test delays, navigation changes, and confirmation dialogs. Stale controls can trigger the wrong action.

**Remember:** Use semantic targets and verify meaningful results.

## 81. Explain repository boundaries in Agents.

Coding tasks require a defined workspace and write scope. Resolve paths and restrict filesystem access.

**Remember:** Traversal or incorrect roots can affect unrelated files.

## 82. How would you apply repository boundaries in a practical Agents task?

Resolve paths and restrict filesystem access. Coding tasks require a defined workspace and write scope.

**Remember:** Verify modified paths and test traversal rejection.

## 83. What mistake should you avoid with repository boundaries in Agents?

Traversal or incorrect roots can affect unrelated files. Resolve paths and restrict filesystem access.

**Remember:** Coding tasks require a defined workspace and write scope.

## 84. How would you verify repository boundaries in a Agents implementation?

Verify modified paths and test traversal rejection. Traversal or incorrect roots can affect unrelated files.

**Remember:** Resolve paths and restrict filesystem access.

## 85. Explain reproducibility in Agents.

Replay needs inputs, configuration, and relevant execution metadata. Version tools, models, prompts, and data fixtures.

**Remember:** External services may prevent exact token-for-token replay.

## 86. How would you apply reproducibility in a practical Agents task?

Version tools, models, prompts, and data fixtures. Replay needs inputs, configuration, and relevant execution metadata.

**Remember:** Use deterministic fixtures and compare semantic outcomes in live trials.

## 87. What mistake should you avoid with reproducibility in Agents?

External services may prevent exact token-for-token replay. Version tools, models, prompts, and data fixtures.

**Remember:** Replay needs inputs, configuration, and relevant execution metadata.

## 88. How would you verify reproducibility in a Agents implementation?

Use deterministic fixtures and compare semantic outcomes in live trials. External services may prevent exact token-for-token replay.

**Remember:** Version tools, models, prompts, and data fixtures.

## 89. Explain benchmark contamination in Agents.

A holdout loses value when used during tuning. Track test provenance and maintain independent cases.

**Remember:** Fixing only known examples may not improve general tasks.

## 90. How would you apply benchmark contamination in a practical Agents task?

Track test provenance and maintain independent cases. A holdout loses value when used during tuning.

**Remember:** Evaluate fresh tasks after freezing configuration.

## 91. What mistake should you avoid with benchmark contamination in Agents?

Fixing only known examples may not improve general tasks. Track test provenance and maintain independent cases.

**Remember:** A holdout loses value when used during tuning.

## 92. How would you verify benchmark contamination in a Agents implementation?

Evaluate fresh tasks after freezing configuration. Fixing only known examples may not improve general tasks.

**Remember:** Track test provenance and maintain independent cases.

## 93. Explain accessible interaction in Agents.

Agent status and controls must support diverse users. Provide keyboard access, readable errors, and concise status updates.

**Remember:** Announcing every streamed token can overwhelm assistive technology.

## 94. How would you apply accessible interaction in a practical Agents task?

Provide keyboard access, readable errors, and concise status updates. Agent status and controls must support diverse users.

**Remember:** Test focus, announcements, and action review controls.

## 95. What mistake should you avoid with accessible interaction in Agents?

Announcing every streamed token can overwhelm assistive technology. Provide keyboard access, readable errors, and concise status updates.

**Remember:** Agent status and controls must support diverse users.

## 96. How would you verify accessible interaction in a Agents implementation?

Test focus, announcements, and action review controls. Announcing every streamed token can overwhelm assistive technology.

**Remember:** Provide keyboard access, readable errors, and concise status updates.

## 97. Explain decommissioning in Agents.

Retirement includes credentials, workers, schedules, and retained state. Revoke access, stop jobs, and apply retention policies.

**Remember:** Removing the UI leaves background capabilities active.

## 98. How would you apply decommissioning in a practical Agents task?

Revoke access, stop jobs, and apply retention policies. Retirement includes credentials, workers, schedules, and retained state.

**Remember:** Verify no scheduled or tool action succeeds after shutdown.

## 99. What mistake should you avoid with decommissioning in Agents?

Removing the UI leaves background capabilities active. Revoke access, stop jobs, and apply retention policies.

**Remember:** Retirement includes credentials, workers, schedules, and retained state.

## 100. How would you verify decommissioning in a Agents implementation?

Verify no scheduled or tool action succeeds after shutdown. Removing the UI leaves background capabilities active.

**Remember:** Revoke access, stop jobs, and apply retention policies.

## Further reading

- [Agent patterns](https://www.anthropic.com/research/building-effective-agents)
