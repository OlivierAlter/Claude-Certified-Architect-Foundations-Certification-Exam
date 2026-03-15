# Claude Certified Architect. Foundations: Practice Exam

> 77 questions across 5 domains | Passing score: 720 (scaled 100-1,000)

---

## Exam Format

- **Format:** Multiple choice, 4 options per question (1 correct, 3 distractors)
- **Unanswered questions:** Scored as incorrect. No penalty for guessing.
- **Result:** Pass/fail designation
- **Scoring:** Scaled score 100-1,000. Minimum passing score: **720**

Questions are scenario-based, grounded in realistic use cases: building agentic systems for customer support, designing multi-agent research pipelines, integrating Claude Code into CI/CD workflows, building developer productivity tools, and extracting structured data from unstructured documents. Candidates must demonstrate practical judgment about architecture, configuration, and tradeoffs in production deployments.

---

## Content Domains & Weightings

| Domain | Topic | Weight | Questions |
|--------|-------|--------|-----------|
| 1 | Agentic Architecture & Orchestration | 27% | Q1, Q7-Q9, Q13-Q29 |
| 2 | Tool Design & MCP Integration | 18% | Q2, Q30-Q40 |
| 3 | Claude Code Configuration & Workflows | 20% | Q4-Q6, Q10, Q41-Q54 |
| 4 | Prompt Engineering & Structured Output | 20% | Q11-Q12, Q55-Q68 |
| 5 | Context Management & Reliability | 15% | Q3, Q69-Q77 |

---

## Domain-Task Index

### Domain 1: Agentic Architecture & Orchestration (27%)

| Task | Description | Questions |
|------|-------------|-----------|
| 1.1 | Agentic loops for autonomous task execution | Q13, Q14, Q15 |
| 1.2 | Multi-agent coordinator-subagent patterns | Q7, Q16, Q17 |
| 1.3 | Subagent invocation, context passing, spawning | Q18, Q19, Q20 |
| 1.4 | Multi-step workflows with enforcement and handoff | Q1, Q21, Q22 |
| 1.5 | Agent SDK hooks for tool call interception | Q23, Q24, Q25 |
| 1.6 | Task decomposition strategies | Q26, Q27 |
| 1.7 | Session state, resumption, and forking | Q28, Q29 |

### Domain 2: Tool Design & MCP Integration (18%)

| Task | Description | Questions |
|------|-------------|-----------|
| 2.1 | Tool interface design with clear descriptions | Q2, Q30, Q31 |
| 2.2 | Structured error responses for MCP tools | Q8, Q32, Q33, Q34 |
| 2.3 | Tool distribution across agents and tool_choice | Q9, Q35, Q36 |
| 2.4 | MCP server integration into Claude Code | Q37, Q38 |
| 2.5 | Built-in tools (Read, Write, Edit, Bash, Grep, Glob) | Q39, Q40 |

### Domain 3: Claude Code Configuration & Workflows (20%)

| Task | Description | Questions |
|------|-------------|-----------|
| 3.1 | CLAUDE.md hierarchy, scoping, modular organization | Q41, Q42, Q54 |
| 3.2 | Custom slash commands and skills | Q4, Q43 |
| 3.3 | Path-specific rules for conditional convention loading | Q6, Q44 |
| 3.4 | Plan mode vs direct execution | Q5, Q45, Q46 |
| 3.5 | Iterative refinement techniques | Q47, Q48, Q49, Q51, Q52 |
| 3.6 | Claude Code in CI/CD pipelines | Q10, Q50, Q53 |

### Domain 4: Prompt Engineering & Structured Output (20%)

| Task | Description | Questions |
|------|-------------|-----------|
| 4.1 | Explicit criteria for precision and false positive reduction | Q55, Q56, Q57 |
| 4.2 | Few-shot prompting for consistency and quality | Q58, Q59, Q60 |
| 4.3 | Structured output using tool use and JSON schemas | Q61, Q62 |
| 4.4 | Validation, retry, and feedback loops | Q63, Q64, Q67 |
| 4.5 | Batch processing strategies | Q11, Q65 |
| 4.6 | Multi-instance and multi-pass review architectures | Q12, Q66, Q68 |

### Domain 5: Context Management & Reliability (15%)

| Task | Description | Questions |
|------|-------------|-----------|
| 5.1 | Conversation context preservation | Q69, Q70 |
| 5.2 | Escalation and ambiguity resolution | Q3, Q71 |
| 5.3 | Error propagation across multi-agent systems | Q72 |
| 5.4 | Context management in large codebase exploration | Q73, Q74 |
| 5.5 | Human review workflows and confidence calibration | Q75, Q76 |
| 5.6 | Information provenance and uncertainty | Q77 |

---

## Exam Scenarios

4 of the 6 scenarios below are selected at random for each exam. Each scenario frames a set of questions.

### Scenario 1: Customer Support Resolution Agent
You are building a customer support resolution agent using the Claude Agent SDK. The agent handles high-ambiguity requests like returns, billing disputes, and account issues. It has access to your backend systems through custom MCP tools (`get_customer`, `lookup_order`, `process_refund`, `escalate_to_human`). Target: 80%+ first-contact resolution while knowing when to escalate.

**Primary domains:** Domain 1, Domain 2, Domain 5

---

### Scenario 2: Code Generation with Claude Code
You are using Claude Code to accelerate software development for code generation, refactoring, debugging, and documentation. You need to integrate it with custom slash commands, CLAUDE.md configurations, and understand when to use plan mode vs direct execution.

**Primary domains:** Domain 3, Domain 5

---

### Scenario 3: Multi-Agent Research System
You are building a multi-agent research system using the Claude Agent SDK. A coordinator agent delegates to specialized subagents: web search, document analysis, synthesis, and report generation. The system produces comprehensive cited reports.

**Primary domains:** Domain 1, Domain 2, Domain 5

---

### Scenario 4: Developer Productivity with Claude
You are building developer productivity tools using the Claude Agent SDK. The agent helps engineers explore unfamiliar codebases, understand legacy systems, generate boilerplate, and automate repetitive tasks. Uses built-in tools (Read, Write, Bash, Grep, Glob) and MCP servers.

**Primary domains:** Domain 2, Domain 3, Domain 1

---

### Scenario 5: Claude Code for Continuous Integration
You are integrating Claude Code into CI/CD pipelines. The system runs automated code reviews, generates test cases, and provides pull request feedback. You need prompts that provide actionable feedback and minimize false positives.

**Primary domains:** Domain 3, Domain 4

---

### Scenario 6: Structured Data Extraction
You are building a structured data extraction system using Claude. The system extracts information from unstructured documents, validates output using JSON schemas, and maintains high accuracy. Must handle edge cases gracefully and integrate with downstream systems.

**Primary domains:** Domain 4, Domain 5

---

## Domain 1: Agentic Architecture & Orchestration

### Task 1.1: Design and implement agentic loops for autonomous task execution

**Q1.** Production data shows that in 12% of cases, your agent skips `get_customer` entirely and calls `lookup_order` using only the customer's stated name, occasionally leading to misidentified accounts and incorrect refunds. What change would most effectively address this reliability issue?

A) Add a programmatic prerequisite that blocks `lookup_order` and `process_refund` calls until `get_customer` has returned a verified customer ID.
B) Enhance the system prompt to state that customer verification via `get_customer` is mandatory before any order operations.
C) Add few-shot examples showing the agent always calling `get_customer` first, even when customers volunteer order details.
D) Implement a routing classifier that analyzes each request and enables only the subset of tools appropriate for that request type.

**Correct Answer: A**
When a specific tool sequence is required for critical business logic, programmatic enforcement provides deterministic guarantees that prompt-based approaches cannot. Options B and C rely on probabilistic LLM compliance. Option D addresses tool availability rather than tool ordering.

---

**Q13.** You are building a customer support agent using the Claude Agent SDK. The agent processes billing disputes by calling tools like `lookup_order`, `get_invoice`, and `process_refund`. A code review notes that after each tool call, your loop checks whether Claude's response text contains the phrase "I have completed" to decide whether to stop.

What is the primary problem with this loop termination approach?

A) The agent will never terminate because `process_refund` always returns a success message that prevents "I have completed" from appearing.
B) Relying on natural language signals in the assistant's text is unreliable; the correct approach is to inspect `stop_reason` and only terminate when it equals `"end_turn"`.
C) The loop should terminate as soon as any tool call fails, since continuing after a failure will corrupt the conversation history.
D) Checking response text is only valid in synchronous mode; you must use a callback handler for proper loop control in async contexts.

**Correct Answer: B**
Inspecting `stop_reason` is the canonical method for agentic loop control: continue iterating when `stop_reason` is `"tool_use"`, stop when it is `"end_turn"`. Natural language phrases like "I have completed" are not reliable termination signals because Claude's phrasing varies across responses and prompt updates. Options A and C are based on incorrect assumptions about how tools interact with response text. Option D conflates asynchronous execution patterns with loop control logic.

---

**Q14.** A developer productivity agent investigates bug reports by calling `search_codebase`, `read_file`, and `run_tests`. During a code review, a colleague proposes adding an iteration cap: if the loop has not finished after 15 tool calls, terminate with a generic "investigation incomplete" response.

What is the correct characterization of this design?

A) Iteration caps are the recommended primary stopping mechanism because they prevent runaway costs in production.
B) Iteration caps are a reasonable safety boundary for long-running tasks but should not be the primary termination mechanism; `stop_reason: "end_turn"` remains the authoritative signal.
C) The iteration cap should be replaced with a time-based timeout, since token counts are a more reliable measure of completion than iteration count.
D) Iteration caps are unnecessary if the system prompt instructs the agent to always request only the minimum tools needed.

**Correct Answer: B**
The agentic loop should terminate primarily when `stop_reason` equals `"end_turn"`, which signals that the model has finished its task. An iteration cap can serve as a safety guardrail against runaway loops, but treating it as the primary stopping mechanism means the loop may cut off legitimate multi-step investigations. Options A and C misstate recommended practice. Option D conflates prompt-based guidance with loop control: even a well-prompted agent may legitimately need many tool calls for complex investigations.

---

**Q15.** Your multi-agent research system's agentic loop appends each tool result to the conversation history before sending the next request. A teammate suggests instead storing all tool results in a separate database and providing only a summary to the model at each iteration, rather than the full result.

Under what condition would this change most likely degrade agent performance?

A) When the tool results contain binary data such as images or file attachments.
B) When the model needs to reason across multiple tool results simultaneously to determine its next action, since summaries may omit details required for that reasoning.
C) When the number of tool calls per session exceeds 10, since larger histories slow down the API.
D) When tools return results faster than 200ms, making history appending redundant.

**Correct Answer: B**
The agentic loop depends on tool results being present in conversation history so the model can reason about what it has already discovered before deciding its next action. Summaries may omit field values, error codes, or conditional data the model needs to make correct decisions. Option A is a valid concern but not the primary performance risk for text-based research tasks. Options C and D are not recognized failure modes for this architecture.

---

### Task 1.2: Orchestrate multi-agent systems with coordinator-subagent patterns

**Q7.** After running on "impact of AI on creative industries," each subagent completes successfully but the final reports cover only visual arts, missing music, writing, and film production. The coordinator decomposed the topic into: "AI in digital art creation," "AI in graphic design," and "AI in photography." What is the most likely root cause?

A) The synthesis agent lacks instructions for identifying coverage gaps in the findings it receives from other agents.
B) The coordinator agent's task decomposition is too narrow, resulting in subagent assignments that don't cover all relevant domains.
C) The web search agent's queries are not comprehensive enough and need to be expanded to cover more creative industry sectors.
D) The document analysis agent is filtering out sources related to non-visual creative industries due to overly restrictive relevance criteria.

**Correct Answer: B**
The coordinator's logs reveal the root cause directly: it decomposed "creative industries" into only visual arts subtasks. The subagents executed their assigned tasks correctly. The problem is what they were assigned.

---

**Q16.** Your multi-agent research system uses a coordinator that always routes every query through all four subagents (web search, document analysis, synthesis, and report generation) regardless of query complexity. For a simple factual question like "What year was the Anthropic API released?", the system takes 45 seconds and incurs unnecessary cost.

What design change most directly addresses this?

A) Replace the coordinator with a static routing table that maps query keywords to specific subagent pipelines.
B) Have each subagent evaluate its own relevance to the current query and self-select into or out of the pipeline.
C) Design the coordinator to dynamically select which subagents to invoke based on query complexity and type, rather than always routing through the full pipeline.
D) Reduce the number of subagents from four to two by merging web search and document analysis into a single "retrieval" agent.

**Correct Answer: C**
A coordinator that always runs the full pipeline regardless of query complexity wastes resources and adds latency for simple requests. The correct design is a coordinator that evaluates the query and selects only the subagents needed for that specific task. Option A replaces adaptive intelligence with a brittle keyword table. Option B distributes coordination logic across subagents, breaking the hub-and-spoke pattern and reducing observability. Option D reduces capability unnecessarily instead of improving routing logic.

---

**Q17.** A coordinator agent in your research system has delegated document analysis to a subagent. After the subagent finishes, the coordinator notices the findings are incomplete: the subagent covered only three of the five specified sources. The coordinator needs to get the remaining two sources analyzed.

What is the correct approach for re-delegating this work?

A) Invoke the synthesis agent with the partial findings and instruct it to infer what the missing sources likely contain based on patterns from the three completed analyses.
B) The coordinator should re-invoke the document analysis subagent with an explicit prompt specifying only the two missing sources, including the previously completed findings as context.
C) Send all five sources again to a new document analysis subagent instance, which will re-analyze the three already-completed sources along with the two missing ones.
D) Let the coordinator generate its own analysis of the remaining two sources directly, rather than spawning another subagent delegation.

**Correct Answer: B**
The coordinator's role includes evaluating output for gaps and re-delegating targeted work to close those gaps. Re-invoking the subagent with only the unfinished sources and providing the completed findings as context is efficient and correct. Option A asks synthesis to fabricate content, which undermines report accuracy. Option C wastes resources by re-processing already-completed sources. Option D bypasses the coordinator-subagent architecture and ignores the subagent's specialization.

---

### Task 1.3: Configure subagent invocation, context passing, and spawning

**Q18.** You are building a coordinator that delegates research tasks to subagents using the `Task` tool. When you test the system, the coordinator cannot invoke any subagents. Reviewing the coordinator's `AgentDefinition`, you notice the `allowedTools` field is set to `["web_search", "read_document"]`.

What is the most likely cause of the failure?

A) The `Task` tool requires an explicit `subagent_endpoint` configuration before it can be invoked.
B) `"Task"` is not included in the coordinator's `allowedTools`, so it cannot spawn subagents.
C) The coordinator's system prompt does not include instructions to use the `Task` tool, so the model never attempts to call it.
D) Subagent invocation requires the coordinator to be running in plan mode rather than direct execution mode.

**Correct Answer: B**
The `Task` tool is the mechanism for spawning subagents in the Claude Agent SDK. For a coordinator to invoke subagents, `"Task"` must be explicitly included in its `allowedTools`. Simply having other tools available does not grant subagent spawning capability. Option A describes a configuration parameter that does not exist. Option C conflates prompt instructions with capability gating: even a well-prompted coordinator cannot call a tool that is not in its allowed set. Option D conflates plan mode with subagent spawning.

---

**Q19.** Your multi-agent research system has a web search subagent that consistently returns findings without identifying which sources correspond to which claims. When the synthesis agent receives these findings, it cannot produce properly cited reports.

What is the correct fix during context passing from the web search subagent to the synthesis agent?

A) Instruct the synthesis agent to run its own web searches to re-locate the original sources.
B) Use structured data formats that separate claim content from metadata (source URLs, publication dates, page numbers) in the subagent's output, and include this structure when passing context to the synthesis agent.
C) Have the coordinator concatenate all subagent outputs into a single text block before forwarding to synthesis, since synthesis will extract citations naturally.
D) Configure the web search subagent to return only source URLs, and have the synthesis agent re-read each source to reconstruct the findings.

**Correct Answer: B**
Structured data formats that separate content from metadata ensure that claim-source mappings survive the handoff between agents. When context is passed as unstructured text, citation information is easily lost. Option A introduces redundant work and potentially different search results. Option C risks losing the claim-source associations during concatenation. Option D is extremely inefficient and requires the synthesis agent to redo retrieval work.

---

**Q20.** A coordinator needs to research three independent subtopics in parallel: market trends, competitor analysis, and regulatory environment. Each requires a separate web search subagent. How should the coordinator spawn these subagents to maximize throughput?

A) Spawn the subtopics sequentially: start the first subagent, wait for its result, then start the second, and so on, to avoid context conflicts.
B) Emit all three `Task` tool calls in a single coordinator response, which allows the subagents to run in parallel.
C) Route all three subtopics through a single subagent sequentially, sharing context between them to reduce total memory usage.
D) Use a single subagent with three separate prompts in sequence, passing prior results as context for each subsequent prompt.

**Correct Answer: B**
The Claude Agent SDK supports parallel subagent execution by emitting multiple `Task` tool calls in a single coordinator response. This maximizes throughput for independent subtopics that do not depend on each other's results. Option A introduces unnecessary serial latency. Option C assumes a dependency that the question does not establish. Option D collapses three specialists into one sequential process, eliminating parallelism.

---

### Task 1.4: Implement multi-step workflows with enforcement and handoff patterns

**Q21.** Your customer support agent handles account closure requests. The workflow requires: (1) verify customer identity via `get_customer`, (2) check for active subscriptions via `check_subscriptions`, (3) process closure via `close_account`. Production logs show the agent occasionally calls `close_account` before completing the identity verification step, resulting in unauthorized account closures.

A colleague suggests adding a system prompt instruction: "Always verify identity before closing accounts." What is the most effective approach?

A) The system prompt instruction is sufficient because it explicitly describes the required order.
B) Add few-shot examples showing the correct three-step sequence alongside the system prompt instruction.
C) Implement a programmatic prerequisite that blocks `close_account` from executing until `get_customer` has returned a verified customer ID.
D) Add a routing classifier that analyzes the request type and pre-selects the appropriate tools before the agent begins.

**Correct Answer: C**
When a tool ordering requirement has serious consequences (unauthorized account closures), programmatic enforcement provides deterministic guarantees. Prompt instructions have a non-zero failure rate even when explicit. Option A relies on probabilistic compliance, which the logs already show is insufficient. Option B improves the odds but still does not guarantee compliance. Option D addresses tool selection rather than ordering enforcement.

---

**Q22.** A customer contacts your support agent about three issues in a single message: a billing charge dispute, a missing order, and a request to update their email address. The agent processes these sequentially, taking 3-4 minutes per request. A senior architect suggests you redesign the handling approach.

What design change would most improve efficiency while maintaining accuracy?

A) Instruct the agent to address only the highest-priority issue per conversation turn and ask the customer to submit separate tickets for the remaining issues.
B) Decompose the three concerns into distinct investigation items and process each in parallel using shared customer context, then compile a unified response.
C) Process the three issues sequentially but cache intermediate results so subsequent issues benefit from data already retrieved.
D) Delegate all three issues to a single specialized "multi-issue" subagent that handles complex requests with multiple concerns.

**Correct Answer: B**
When a customer presents multiple independent concerns, decomposing them into parallel investigation items dramatically reduces latency. Each concern can be investigated simultaneously using the shared customer context already retrieved. Option A creates a poor customer experience and extra work for the customer. Option C improves caching but does not eliminate the serial bottleneck. Option D creates an undifferentiated subagent that doesn't reflect the coordinator-subagent specialization pattern.

---

### Task 1.5: Apply Agent SDK hooks for tool call interception and data normalization

**Q23.** Your customer support agent integrates with three backend MCP tools: a legacy billing system returning Unix timestamps, an order management system returning ISO 8601 dates, and a subscription service returning numeric status codes (1=active, 2=paused, 3=cancelled). The agent frequently misinterprets these heterogeneous formats when reasoning about customer records.

What is the most appropriate architectural fix?

A) Update each backend system to return a uniform date and status format before the agent calls them.
B) Add format conversion instructions to the system prompt explaining how to interpret each tool's output conventions.
C) Implement `PostToolUse` hooks that intercept tool results from each source and normalize timestamps, dates, and status codes into a consistent format before the model processes them.
D) Add a post-processing step after the agent produces its final response to re-format any dates and statuses that appear in the output.

**Correct Answer: C**
`PostToolUse` hooks are the correct mechanism for intercepting and transforming tool results before the model processes them. This ensures the model always sees normalized data regardless of backend heterogeneity. Option A requires backend changes that may not be feasible and introduces coupling. Option B relies on probabilistic compliance and adds token overhead. Option D applies normalization after the model has already reasoned on inconsistent data, which cannot repair any incorrect conclusions already made.

---

**Q24.** Your customer support agent has a policy: refunds above $500 require manager approval and must not be processed autonomously. Your system prompt states "Do not process refunds above $500 without manager approval." Production logs show this rule is violated in approximately 3% of cases.

What is the most effective way to guarantee compliance?

A) Strengthen the system prompt language: "You are strictly forbidden from processing refunds above $500 without explicit manager approval under any circumstances."
B) Add 10 few-shot examples in the system prompt, all demonstrating the agent requesting manager approval for high-value refunds.
C) Implement a hook that intercepts outgoing `process_refund` tool calls, checks the refund amount, and blocks execution or redirects to the manager approval workflow when the amount exceeds $500.
D) Implement a validation step that runs after `process_refund` completes and reverses any refunds that exceeded the threshold.

**Correct Answer: C**
Business rules that require guaranteed compliance must be enforced programmatically, not through prompt instructions alone. A hook that intercepts `process_refund` calls before execution provides deterministic enforcement regardless of how the model interprets the system prompt. Options A and B both improve adherence probabilistically but cannot guarantee zero violations. Option D runs after the action has already been taken, which means the policy violation has already occurred.

---

**Q25.** A developer productivity agent has a `PostToolUse` hook that transforms raw Bash output. Currently the hook appends a formatted summary but also preserves the full raw output in the result passed to the model. Sessions exploring large codebases are hitting context limits faster than expected.

What change would most effectively reduce unnecessary context consumption from tool results?

A) Disable the `PostToolUse` hook entirely and let the model process raw Bash output directly.
B) Modify the hook to return only the formatted summary to the model, trimming the verbose raw output rather than preserving it alongside the summary.
C) Increase the model's `max_tokens` parameter to accommodate the additional context from both raw and formatted output.
D) Switch from `PostToolUse` hooks to pre-processing the Bash commands themselves to produce shorter output.

**Correct Answer: B**
`PostToolUse` hooks can trim verbose tool outputs to only the relevant data before the model processes them. Keeping both raw and summary output doubles the context consumption from each tool call. Modifying the hook to return only the formatted summary addresses the root cause directly. Option A removes normalization benefits. Option C increases output capacity but does not address the growing input context. Option D would require significant changes to tool invocation patterns and may not be feasible for all commands.

---

### Task 1.6: Design task decomposition strategies for complex workflows

**Q26.** You are building an automated code review system using Claude. The review must cover three aspects for every pull request: security vulnerabilities, style compliance, and performance implications. Each aspect has clear, defined criteria documented in your engineering handbook.

Which decomposition strategy is most appropriate?

A) Dynamic adaptive decomposition: have the agent start by scanning the full PR and generate a review plan based on what it finds.
B) Prompt chaining with sequential focused passes: one pass per review aspect (security, style, performance), each with dedicated criteria.
C) A single comprehensive pass that examines all three aspects simultaneously to capture cross-cutting concerns.
D) Spawn three fully independent agents without shared context, then merge their outputs in a final aggregation step.

**Correct Answer: B**
When a workflow has predictable, well-defined aspects that must each be covered, prompt chaining with sequential focused passes is the appropriate pattern. Each pass dedicates full attention to one concern rather than dividing attention across all three. Option A uses dynamic decomposition for a workflow whose structure is already known, adding unnecessary overhead. Option C suffers from the attention dilution problem that prompt chaining is designed to solve. Option D loses cross-file integration context by fully isolating the three agents.

---

**Q27.** An engineering team asks you to design a Claude-based system to investigate a production incident. The system must root-cause a bug that was introduced somewhere in the past two weeks across an unknown set of files and services. The scope of the investigation cannot be known in advance.

Which decomposition approach is most appropriate?

A) Prompt chaining: design a fixed sequence of investigation steps (check logs, read configs, trace service calls) that the agent executes in order.
B) Dynamic adaptive decomposition: the agent first maps the affected services and symptom timeline, then generates and prioritizes investigation subtasks based on what is discovered at each step.
C) Split the investigation between two agents: one agent reads logs while the other reads source code, and they report findings independently to a human operator.
D) Have the agent run a comprehensive search of all changed files in the past two weeks and produce a ranked list of candidates for manual review.

**Correct Answer: B**
Open-ended investigation tasks with unknown scope require dynamic adaptive decomposition, where the agent builds its investigation plan based on intermediate findings rather than following a fixed sequence. A static prompt chain cannot adapt when the investigation reveals unexpected service dependencies or anomalous patterns. Option A is appropriate for predictable multi-aspect reviews, not exploratory investigations. Option C removes the coordinating intelligence and requires human intervention for synthesis. Option D is a single-pass heuristic that does not apply the model's reasoning capability.

---

### Task 1.7: Manage session state, resumption, and forking

**Q28.** A developer has been using Claude Code to investigate a legacy authentication service. After several hours, they have built up a detailed session with findings about the service's token validation logic. They need to step away and return tomorrow. Three core files in the authentication module will be modified overnight by another team.

What is the most reliable approach for resuming the investigation productively the next day?

A) Resume the named session with `--resume <session-name>` and notify the agent about the specific files that were changed, so it can re-analyze those files in the context of its prior understanding.
B) Start a completely new session each time, since stale tool results from the previous session make resumption unreliable for any scenario.
C) Resume the named session without any notification about file changes; the agent will detect modifications automatically when it next reads those files.
D) Use `fork_session` to create a branch of the current session before stepping away, then resume from the fork the next day.

**Correct Answer: A**
When resuming a session after code modifications, the correct approach is to use `--resume <session-name>` to continue the named session and explicitly inform the agent about which files changed so it can target re-analysis appropriately. Option B is overly conservative: starting fresh is appropriate when prior tool results are broadly stale, but when only a few known files changed, resumption with targeted context about those changes is more efficient. Option C is incorrect because the agent does not automatically detect file changes on resume. Option D misuses `fork_session`, which is designed for exploring divergent approaches from a shared baseline, not for session continuity across time gaps.

---

**Q29.** You are leading a research investigation using Claude Code. You have completed an initial analysis of a competitor's public API documentation and want to explore two divergent architectural approaches for your response strategy: one focused on feature parity, one focused on differentiation. You want both explorations to start from the same analysis baseline.

Which session management approach best fits this scenario?

A) Run two separate new sessions, each with a copy of the analysis findings injected as context in the initial prompt.
B) Use `--resume` to resume the current session twice in parallel, once for each exploration direction.
C) Use `fork_session` to create two independent branches from the current session, then explore each approach in its respective branch.
D) Continue in the same session, exploring one approach, then using `/compact` to clear context before exploring the second approach.

**Correct Answer: C**
`fork_session` is designed precisely for this scenario: creating independent branches from a shared analysis baseline to explore divergent approaches. Each branch inherits the common findings and can be explored independently without contaminating the other. Option A requires duplicating context and does not preserve the live session state. Option B describes a mechanism that does not work this way: `--resume` continues a single session sequentially, not in parallel branches. Option D uses `/compact` destructively, losing the baseline context needed for the second exploration.

---

## Domain 2: Tool Design & MCP Integration

### Task 2.1: Design effective tool interfaces with clear descriptions and boundaries

**Q2.** Production logs show the agent frequently calls `get_customer` when users ask about orders, instead of calling `lookup_order`. Both tools have minimal descriptions and accept similar identifier formats. What's the most effective first step to improve tool selection reliability?

A) Add few-shot examples to the system prompt demonstrating correct tool selection patterns, with 5-8 examples.
B) Expand each tool's description to include input formats it handles, example queries, edge cases, and boundaries explaining when to use it versus similar tools.
C) Implement a routing layer that parses user input before each turn and pre-selects the appropriate tool based on detected keywords.
D) Consolidate both tools into a single `lookup_entity` tool that accepts any identifier and internally determines which backend to query.

**Correct Answer: B**
Tool descriptions are the primary mechanism LLMs use for tool selection. Option B directly addresses the root cause. Few-shot examples (A) add token overhead without fixing the underlying issue. A routing layer (C) is over-engineered. Consolidating tools (D) requires more effort than a "first step" warrants.

---

**Q30.** Your customer support agent has a `lookup_order` tool that is called at the right times, but frequently returns errors. Logs show the agent passes free-text descriptions like "order from last Tuesday" instead of the required ISO-8601 timestamp format. The tool description reads: "Retrieves order details given a date or identifier." No examples or format constraints are provided.

What change to the tool definition would most directly reduce these input format errors?

A) Add input format constraints, accepted value formats, and example inputs to the tool description so the model knows exactly how to format its calls.
B) Add a system prompt instruction: "Always use ISO-8601 format when calling lookup_order."
C) Add input schema validation that rejects malformed inputs and returns an error to the agent.
D) Split `lookup_order` into two tools: `lookup_order_by_id` and `lookup_order_by_date` to reduce ambiguity.

**Correct Answer: A**
Tool descriptions are the primary mechanism the model uses to understand how to call a tool. Adding format constraints and examples directly to the description gives the model the information it needs at decision time. Option B adds token overhead in the system prompt but is more fragile than a tool-specific description. Option C adds validation but does not prevent the model from sending malformed inputs in the first place, creating unnecessary error cycles. Option D addresses a different problem (disambiguation) rather than the format guidance issue.

---

**Q31.** Your customer support agent has three tools with overlapping names and descriptions: `get_account_info` ("Get information about the account"), `fetch_account_details` ("Fetch account details"), and `retrieve_customer_record` ("Retrieve customer information"). All three call different backend systems with different data. The agent frequently picks the wrong tool.

Which approach most effectively resolves the misrouting?

A) Add a system prompt instruction listing all three tools and specifying exactly when each should be used based on the request type.
B) Rename the tools to reflect their distinct data sources and rewrite their descriptions to explain what data each returns, what backend it queries, and what use case it serves.
C) Consolidate all three tools into one tool with a `source` parameter that specifies which backend to query.
D) Keep the current tools but randomize which one the agent calls, then merge the responses in a post-processing step.

**Correct Answer: B**
Ambiguous or overlapping tool names and descriptions cause misrouting. Renaming tools to reflect their distinct backends and writing descriptions that explain what each one returns, where its data comes from, and when to use it are the right fixes. Option A may reduce misrouting but does not fix the root problem: the tool descriptions themselves are indistinguishable. Option C collapses three specialized tools into one generic tool with a parameter, which shifts the burden of correct routing back to the model in a less structured way. Option D is not a viable architecture.

---

### Task 2.2: Implement structured error responses for MCP tools

**Q8.** The web search subagent times out while researching a complex topic. You need to design how this failure information flows back to the coordinator agent. Which error propagation approach best enables intelligent recovery?

A) Return structured error context to the coordinator including the failure type, the attempted query, any partial results, and potential alternative approaches.
B) Implement automatic retry logic with exponential backoff within the subagent, returning a generic "search unavailable" status only after all retries are exhausted.
C) Catch the timeout within the subagent and return an empty result set marked as successful.
D) Propagate the timeout exception directly to a top-level handler that terminates the entire research workflow.

**Correct Answer: A**
Structured error context gives the coordinator the information it needs to make intelligent recovery decisions. Option B's generic status hides valuable context. Option C suppresses the error, preventing any recovery. Option D terminates the entire workflow unnecessarily.

---

**Q32.** Your customer support MCP tool `process_refund` returns the same error response for all failures: `{"status": "error", "message": "Operation failed"}`. The agent currently handles all errors by apologizing to the customer and ending the conversation. Logs show this response is triggered by: network timeouts, invalid refund amounts, refunds blocked by fraud detection, and expired order IDs.

What structured error response design would most improve the agent's ability to recover appropriately?

A) Return different HTTP status codes for each failure type and have the agent interpret the status code to determine recovery action.
B) Return structured error metadata including `errorCategory` (transient/validation/permission/business), `isRetryable` boolean, and a human-readable explanation specific to the failure reason.
C) Return a verbose error log with the full stack trace and system state so the agent has maximum information to reason from.
D) Return a numeric error code and have the system prompt map each code to a recovery action.

**Correct Answer: B**
Structured error metadata gives the agent the information it needs to choose the correct recovery path: retry a transient failure, ask the customer for corrected input on a validation failure, or explain a policy block on a business rule violation. Option A relies on HTTP semantics that may not map cleanly to all failure categories and are not as expressive as structured fields. Option C provides excessive detail that consumes context without improving decision quality. Option D encodes recovery logic in the system prompt rather than in a principled error structure, making it harder to maintain.

---

**Q33.** A web search subagent in your research system calls `search_web` and receives the following response: `{"results": [], "status": "success"}`. The subagent reports to the coordinator: "Web search was successful but no relevant results were found." Later you discover the search API was actually down and returning empty results for all queries.

What change to the MCP tool's error handling would prevent this confusion?

A) Always return a non-empty results array by including fallback content when the actual search returns nothing.
B) Distinguish between access failures (where the backend could not be reached or returned an error) and valid empty results (where the search succeeded but found no matches), using the `isError` flag for the former.
C) Add a `confidence` field to the response so the agent can infer whether the empty result is a real outcome or a failure.
D) Implement automatic retry in the MCP tool itself, so the agent never sees an empty result unless all retries were exhausted.

**Correct Answer: B**
Access failures and valid empty results are fundamentally different conditions that require different agent responses. Using the `isError` flag for access failures while returning `{"results": [], "status": "success"}` only for genuine empty-result queries gives the coordinator accurate information to make retry and recovery decisions. Option A masks failures by fabricating content. Option C introduces ambiguity; a confidence score on a genuinely empty result is meaningless. Option D handles retries locally but does not solve the agent's inability to distinguish the two conditions.

---

**Q34.** Your MCP tool `check_fraud_risk` returns `{"isError": true, "message": "Refund blocked"}` when a refund is flagged by fraud detection. The agent interprets this as a transient failure and retries the refund three times before giving up. Each retry generates a separate fraud alert in your compliance system.

What is the missing element in the error response design?

A) The response should include a `retry_after` timestamp so the agent knows when to retry.
B) The response should include `isRetryable: false` and a customer-appropriate explanation distinguishing this business rule block from a transient system error.
C) The tool should suppress the `isError` flag for fraud blocks and instead return the result as a successful response with a `blocked: true` field.
D) The response should include the fraud risk score so the agent can decide whether the score is high enough to justify blocking.

**Correct Answer: B**
A business rule block from fraud detection is a non-retryable error. Including `isRetryable: false` signals to the agent that retrying will not resolve the situation, preventing redundant attempts that trigger compliance alerts. A customer-appropriate explanation helps the agent communicate the block appropriately. Option A implies the block is temporary and retriable, which is the opposite of the intended behavior. Option C hides the error nature of the response and makes recovery logic less clear. Option D provides fraud risk data to the agent that it may not be authorized to act on directly.

---

### Task 2.3: Distribute tools appropriately across agents and configure tool_choice

**Q9.** The synthesis agent frequently needs to verify specific claims while combining findings. Currently, this creates 2-3 round trips per task, increasing latency by 40%. 85% of verifications are simple fact-checks; 15% require deeper investigation. What's the most effective approach to reduce overhead while maintaining reliability?

A) Give the synthesis agent a scoped `verify_fact` tool for simple lookups, while complex verifications continue delegating to the web search agent through the coordinator.
B) Have the synthesis agent accumulate all verification needs and return them as a batch to the coordinator at the end of its pass.
C) Give the synthesis agent access to all web search tools so it can handle any verification need directly without round-trips.
D) Have the web search agent proactively cache extra context around each source during initial research, anticipating what the synthesis agent might need to verify.

**Correct Answer: A**
Option A applies the principle of least privilege by giving the synthesis agent only what it needs for the 85% common case while preserving the existing coordination pattern for complex cases. Option B creates blocking dependencies. Option C over-provisions the synthesis agent. Option D relies on speculative caching.

---

**Q35.** You are building a multi-agent research system with a synthesis agent whose sole job is combining findings from subagents and producing a structured report. You have given the synthesis agent access to all 18 tools in your system: web search, file reading, database queries, email sending, calendar access, and more, reasoning that more tools provide more flexibility.

What problem does this configuration most likely introduce?

A) The synthesis agent will refuse to call any tools because it is overwhelmed by the number of choices.
B) Having access to tools outside its specialization increases the likelihood the synthesis agent will misuse them, such as initiating new web searches instead of synthesizing the provided findings.
C) 18 tools will exceed the context window limit for tool schemas, causing API errors on every request.
D) The additional tools will slow down the synthesis agent because the model must read all tool descriptions before producing output.

**Correct Answer: B**
Giving an agent access to tools outside its specialization degrades tool selection reliability. A synthesis agent with web search tools will sometimes initiate new searches rather than working with the findings already provided, breaking the intended workflow. Option A overstates the effect: the agent will still call tools, but may call the wrong ones. Option C is not a realistic failure mode for 18 tools with typical schema sizes. Option D mischaracterizes how tool descriptions affect latency.

---

**Q36.** Your customer support system requires that every response from the `draft_response` agent includes a structured JSON summary before the agent returns its output. You want to guarantee the agent calls the `generate_summary` tool on every invocation, not optionally.

Which `tool_choice` configuration achieves this?

A) Set `tool_choice: "auto"` so the model decides when the summary tool is needed.
B) Set `tool_choice: "any"` so the model must call at least one tool, though it may choose a different tool instead.
C) Set `tool_choice: {"type": "tool", "name": "generate_summary"}` to force the model to call `generate_summary` specifically.
D) Remove all other tools from the agent's tool list so `generate_summary` is the only option available.

**Correct Answer: C**
Forced tool selection via `tool_choice: {"type": "tool", "name": "generate_summary"}` guarantees the model calls that specific tool on every invocation. Option A (`"auto"`) allows the model to return text without calling any tool. Option B (`"any"`) guarantees a tool call but does not guarantee which tool, so the model might choose a different one. Option D achieves the same result indirectly but removes legitimate tools the agent may need for its other tasks.

---

### Task 2.4: Integrate MCP servers into Claude Code and agent workflows

**Q37.** Your team is setting up a shared GitHub MCP server for all engineers on a project. The server requires a GitHub API token for authentication. You want every engineer who clones the repository to have the MCP server available without each person having to manually configure it, and you want to avoid committing the actual token to version control.

What is the correct configuration approach?

A) Add the MCP server to `~/.claude.json` on each developer's machine with their personal token hardcoded.
B) Add the MCP server to the project-scoped `.mcp.json` file with the token specified using environment variable expansion (e.g., `${GITHUB_TOKEN}`), and commit `.mcp.json` to the repository.
C) Add the MCP server configuration to the root `CLAUDE.md` file under a `[mcp_servers]` section.
D) Create a setup script that each developer runs once to add the MCP server to their personal `~/.claude.json` with their token.

**Correct Answer: B**
Project-scoped `.mcp.json` with environment variable expansion is the correct pattern for shared MCP servers: it is committed to the repository so all team members get the configuration automatically, and tokens are injected via environment variables at runtime rather than committed as plaintext. Option A requires manual per-person setup and hardcodes tokens. Option C describes a configuration mechanism that does not exist in CLAUDE.md. Option D also requires manual setup and does not solve the commit-to-version-control problem.

---

**Q38.** A developer productivity agent frequently makes multiple exploratory tool calls to discover what data sources are available in your MCP server before it can answer user questions. This pattern increases latency and consumes context for routine requests.

What MCP feature most directly addresses this discovery overhead?

A) Add a `list_tools` meta-tool to the MCP server that returns all available tool names and descriptions.
B) Expose content catalogs as MCP resources, giving the agent visibility into available data at connection time rather than through exploratory tool calls.
C) Reduce the number of tools in the MCP server by merging similar tools together to minimize the discovery surface.
D) Add a caching layer that stores the results of previous exploratory calls and reuses them across sessions.

**Correct Answer: B**
MCP resources are designed to expose content catalogs so agents know what data is available without making exploratory tool calls. This gives the agent upfront visibility at connection time, reducing the need for repeated discovery queries. Option A would still require a tool call to discover available resources. Option C reduces functionality to avoid a structural problem. Option D addresses symptom rather than cause, and cross-session caching of content catalogs may return stale data.

---

### Task 2.5: Select and apply built-in tools (Read, Write, Edit, Bash, Grep, Glob) effectively

**Q39.** A developer productivity agent needs to find all TypeScript files in a project that import from a deprecated module named `legacy-auth`. The project has thousands of files across many directories.

Which combination of built-in tools is most appropriate for this task?

A) Use `Bash` to run `find . -name "*.ts"` and then `Bash` again to run `grep` on each file found.
B) Use `Glob` to find all `.ts` files, then use `Read` to open each file and check whether it contains the import.
C) Use `Grep` to search for the import pattern across all TypeScript files in the codebase.
D) Use `Read` on the project root directory to get a file listing, then recursively `Read` each subdirectory.

**Correct Answer: C**
`Grep` is the correct built-in tool for searching file contents across a codebase. It efficiently searches all TypeScript files for the import pattern without requiring separate file enumeration. Option A uses Bash shell commands that should be replaced by dedicated tools when those tools are available. Option B uses `Glob` for enumeration and then `Read` on each file, which is far less efficient than `Grep` for a content search. Option D uses `Read` for directory traversal, which is not a supported use of that tool.

---

**Q40.** A developer productivity agent needs to update a configuration value in a file. The value appears in a block of code that contains several nearly identical lines. When the agent uses `Edit`, the tool returns an error: "Match not unique: found 3 occurrences of the target text."

What is the correct fallback approach?

A) Use `Bash` to run a `sed` command to replace all occurrences of the target text simultaneously.
B) Use `Read` to load the full file contents, identify the exact surrounding context needed to make the edit unique, and retry `Edit` with a larger `old_string` that uniquely identifies the correct location.
C) Use `Write` to overwrite the entire file with a corrected version, based on the contents loaded by `Read`.
D) Use `Grep` to locate the line number of each occurrence, then use `Edit` with a line number parameter to target the correct one.

**Correct Answer: B**
When `Edit` fails due to non-unique text, the correct first step is to use `Read` to examine the full file and find enough surrounding context to construct a unique `old_string`. This is more surgical than a full `Write` overwrite. Option C using `Read + Write` is a valid fallback but should only be used when `Edit` still cannot find a unique anchor even with additional context. Option A uses Bash shell commands when built-in tools should be preferred, and would replace all occurrences rather than targeting the correct one. Option D describes a line number parameter that `Edit` does not support.

---

## Domain 3: Claude Code Configuration & Workflows

### Task 3.1: Configure CLAUDE.md files with appropriate hierarchy, scoping, and modular organization

**Q41.** A senior engineer adds detailed coding standards and security guidelines to their `~/.claude/CLAUDE.md` file. When a new team member joins and clones the repository, they report that Claude Code behaves differently and does not appear to follow the team's documented standards. What is the most likely cause?

A) The new team member's Claude Code version is outdated and does not support shared configuration files.
B) The `~/.claude/CLAUDE.md` file is user-scoped and not version-controlled, so teammates do not receive it when they clone the repository.
C) CLAUDE.md files must be placed in the `.claude/` subdirectory to be recognized; a root-level `CLAUDE.md` is ignored.
D) The configuration hierarchy requires the project-level file to explicitly import from user-level files using `@import`.

**Correct Answer: B**
User-level configuration in `~/.claude/CLAUDE.md` applies only to the individual developer and is never committed to version control. Teammates will not see it regardless of their setup. To share standards across the team, those instructions must live in the project-level `CLAUDE.md` or `.claude/CLAUDE.md`, which are committed to the repository. Options A and D describe mechanisms that do not exist. Option C is incorrect because a root-level `CLAUDE.md` is a valid project-level location.

---

**Q42.** Your monorepo has a root `CLAUDE.md` that has grown to over 400 lines, covering Python conventions, TypeScript conventions, infrastructure rules, and testing standards. Developers report that Claude sometimes applies the wrong conventions to the wrong files, and the file is difficult to maintain. What is the best approach to reorganize this configuration?

A) Split the content into multiple files in `.claude/rules/`, with each file covering a focused topic, and use path-scoped YAML frontmatter to activate rules only for relevant files.
B) Create a separate `CLAUDE.md` in each top-level package directory and delete the root file entirely.
C) Add inline section headers to the monolithic file and use the `/memory` command to tell Claude which section to prioritize for each task.
D) Break the root `CLAUDE.md` into topic files and use `@import` directives in the root file to pull them all in unconditionally.

**Correct Answer: A**
The `.claude/rules/` directory is designed for exactly this scenario: organizing topic-specific rule files with YAML frontmatter path scoping so each rule set activates only when editing relevant files. This reduces irrelevant context and token usage. Option B would require duplicating shared rules across package directories. Option C relies on manual intervention each session and is not maintainable. Option D with unconditional `@import` addresses the maintenance concern but not the wrong-conventions problem, since all rules would still load regardless of context.

---

**Q54.** You maintain a monorepo with five packages: a Python backend, a TypeScript frontend, a Go service, shared infrastructure Terraform, and a documentation site. Each package has different linting standards, testing conventions, and framework-specific rules. The root `CLAUDE.md` has grown to 600 lines and developers report that rules intended for one package often bleed into sessions working on another. What is the most modular and maintainable solution using CLAUDE.md configuration?

A) Create a `CLAUDE.md` in each package directory with that package's rules, and use `@import` in the root `CLAUDE.md` to include shared conventions that apply to all packages.
B) Keep the 600-line root file but add explicit section headers and instruct developers to tell Claude which section applies at the start of each session.
C) Delete the root `CLAUDE.md` and rely entirely on package-level files, accepting that shared conventions must be duplicated across packages.
D) Move all rules into `.claude/rules/` files and tag each with a `projects:` key in their frontmatter specifying which subdirectory the rule applies to.

**Correct Answer: A**
The `@import` syntax in CLAUDE.md is designed for exactly this modular pattern: shared conventions in the root file, package-specific rules in each package's own `CLAUDE.md`, with the root file importing common standards that apply globally. This keeps each file focused and maintainable while eliminating rule bleed between packages. Option B relies on developer discipline to manually scope rules each session, which is error-prone and does not scale. Option C eliminates the shared baseline and requires duplicating common conventions across five files, creating maintenance drift. Option D is a valid approach for path-scoped rules within a single project but does not address the need for package-level CLAUDE.md isolation.

---

### Task 3.2: Create and configure custom slash commands and skills

**Q4.** You want to create a custom `/review` slash command that runs your team's standard code review checklist and should be available to every developer when they clone or pull the repository. Where should you create this command file?

A) In the `.claude/commands/` directory in the project repository
B) In `~/.claude/commands/` in each developer's home directory
C) In the `CLAUDE.md` file at the project root
D) In a `.claude/config.json` file with a `commands` array

**Correct Answer: A**
Project-scoped custom slash commands are stored in `.claude/commands/` within the repository, version-controlled and automatically available to all developers. Option B is for personal, non-shared commands. Option C is for project instructions, not command definitions. Option D describes a mechanism that doesn't exist.

---

**Q43.** A developer wants a `/scaffold` skill that generates boilerplate for a new microservice. The skill runs many exploratory file reads and Bash commands to understand existing patterns before generating output, producing hundreds of lines of intermediate output. Teammates complain this pollutes their main conversation context. Which frontmatter setting resolves this?

A) Set `allowed-tools: []` in the skill's frontmatter to prevent tool use during execution.
B) Set `context: fork` in the skill's frontmatter to run the skill in an isolated sub-agent context that does not affect the main session.
C) Move the skill file from `.claude/skills/` to `.claude/commands/` so it runs as a command rather than a skill.
D) Add `argument-hint: "service-name"` to the frontmatter so the skill receives a clean input without inheriting session context.

**Correct Answer: B**
The `context: fork` frontmatter option runs the skill in an isolated sub-agent context. All exploratory output, intermediate tool calls, and reasoning happen in the fork and do not accumulate in the main conversation context. Only the final output is returned to the parent session. Option A would disable the tool use the skill depends on. Option C does not change execution isolation behavior. Option D is for prompting the user for input parameters, unrelated to output isolation.

---

### Task 3.3: Apply path-specific rules for conditional convention loading

**Q6.** Your codebase has distinct areas with different conventions. Test files are spread throughout the codebase alongside the code they test. You want all tests to follow the same conventions regardless of location. What's the most maintainable way to ensure Claude automatically applies the correct conventions when generating code?

A) Create rule files in `.claude/rules/` with YAML frontmatter specifying glob patterns to conditionally apply conventions based on file paths.
B) Consolidate all conventions in the root `CLAUDE.md` file under headers for each area, relying on Claude to infer which section applies.
C) Create skills in `.claude/skills/` for each code type that include the relevant conventions in their `SKILL.md` files.
D) Place a separate `CLAUDE.md` file in each subdirectory containing that area's specific conventions.

**Correct Answer: A**
`.claude/rules/` with glob patterns (e.g., `**/*.test.tsx`) allows conventions to be automatically applied based on file paths regardless of directory location. Option B relies on inference rather than explicit matching. Option C requires manual invocation. Option D can't easily handle files spread across many directories.

---

**Q44.** Your team uses Terraform for infrastructure but only in the `infra/` directory. You want Claude to automatically apply Terraform naming conventions and module structure rules only when editing `.tf` files, without those rules appearing in unrelated Python or TypeScript sessions. What is the correct approach?

A) Create a `CLAUDE.md` file inside `infra/` that contains the Terraform rules so they apply only within that subdirectory.
B) Create a rules file in `.claude/rules/terraform.md` with YAML frontmatter specifying `paths: ["infra/**/*"]` and listing the Terraform conventions.
C) Add the Terraform rules to the root `CLAUDE.md` under a clearly marked section, and instruct Claude in the system prompt to apply them only to `.tf` files.
D) Create a skill in `.claude/skills/terraform.md` with `allowed-tools` restricted to file operations on the `infra/` directory.

**Correct Answer: B**
The `.claude/rules/` directory with YAML frontmatter path scoping is the correct mechanism for conditionally loading conventions. Setting `paths: ["infra/**/*"]` ensures the Terraform rules load only when editing files in that directory tree. Option A would work for files inside `infra/` but cannot use glob patterns to further filter by file type. Option C relies on Claude's inference rather than explicit path matching, leading to inconsistent behavior. Option D requires manual skill invocation and does not activate automatically.

---

### Task 3.4: Determine when to use plan mode vs direct execution

**Q5.** You've been assigned to restructure a monolithic application into microservices. This will involve changes across dozens of files and requires decisions about service boundaries and module dependencies. Which approach should you take?

A) Enter plan mode to explore the codebase, understand dependencies, and design an implementation approach before making changes.
B) Start with direct execution and make changes incrementally, letting the implementation reveal the natural service boundaries.
C) Use direct execution with comprehensive upfront instructions detailing exactly how each service should be structured.
D) Begin in direct execution mode and only switch to plan mode if you encounter unexpected complexity during implementation.

**Correct Answer: A**
Plan mode is designed for complex tasks involving large-scale changes, multiple valid approaches, and architectural decisions. Option B risks costly rework when dependencies are discovered late. Option C assumes you already know the right structure without exploring the code. Option D ignores that the complexity is already stated.

---

**Q45.** A developer asks Claude Code to add a single null-check to one function in a utility module. The function signature, expected behavior, and fix are all clear. Should they use plan mode or direct execution?

A) Plan mode, because any code change could have unexpected side effects that need exploration before committing.
B) Direct execution, because the task is well-scoped with a clear fix that does not require architectural decisions or multi-file analysis.
C) Plan mode, because exploring the codebase first prevents Claude from making assumptions about dependencies.
D) Use direct execution first, but run a quick plan mode scan afterward to catch any side effects before committing.

**Correct Answer: B**
Direct execution is appropriate for simple, well-understood, single-location changes with clear scope. Plan mode is designed for tasks involving large-scale changes, multiple valid approaches, architectural decisions, or multi-file modifications. A null-check to one function meets none of the criteria for plan mode. Options A and C describe an over-cautious heuristic that does not reflect the intended use of plan mode. Option D inverts the correct workflow: plan mode is used before execution to explore and decide, not after as a post-execution check.

---

**Q46.** A developer is using plan mode to explore a large codebase before deciding how to approach a library migration. During exploration, Claude generates dozens of tool results including full file reads, search outputs, and dependency traces. The developer notices the main conversation context is filling up rapidly and fears context exhaustion before the plan is complete. What is the most appropriate technique to preserve main session context during verbose exploration?

A) Switch to direct execution partway through exploration so that Claude uses fewer tool calls.
B) Use the Explore subagent to isolate verbose discovery output, having it return a structured summary to the main session rather than accumulating raw results.
C) Run `/compact` immediately after each tool call to keep the context window from growing.
D) Restrict Claude to reading only entry point files during plan mode to limit tool call volume.

**Correct Answer: B**
The Explore subagent is specifically designed to isolate verbose discovery work from the main conversation context. It performs the exploration and returns a structured summary, preventing raw tool results from consuming the main session's context budget. Option A abandons the architectural exploration prematurely. Option C helps but running `/compact` after every tool call is operationally cumbersome and loses detail that may still be needed. Option D artificially limits the exploration and would produce an incomplete analysis for complex migrations.

---

### Task 3.5: Apply iterative refinement techniques for progressive improvement

**Q47.** A developer asks Claude Code to reformat date strings in a data pipeline. After the first attempt, the output format is partially correct but inconsistent: some dates are formatted as `YYYY-MM-DD`, others as `MM/DD/YYYY`. Prose instructions like "always use ISO 8601" have been tried twice without improvement. What technique is most likely to resolve the inconsistency?

A) Rewrite the instruction to be more emphatic, using capitalization and repetition to signal importance.
B) Provide 2-3 concrete input/output examples showing the exact transformation expected, including edge cases like two-digit years and ambiguous formats.
C) Switch to plan mode so Claude can explore the codebase before formatting dates.
D) Ask Claude to generate a formatting function first, then apply it in a second pass.

**Correct Answer: B**
Concrete input/output examples are the most effective way to communicate expected transformations when prose instructions are interpreted inconsistently. Showing `"3/15/2024" -> "2024-03-15"` is unambiguous in a way that "use ISO 8601" is not. Option A is unlikely to improve results; emphasis does not resolve ambiguity. Option C is for architectural decisions, not formatting refinement. Option D adds complexity and still does not clarify what the correct transformation looks like.

---

**Q48.** A development team is using Claude Code to implement a new authentication module. Before any implementation begins, the team lead wants to ensure Claude surfaces potential security considerations, edge cases, and design tradeoffs that the team may not have anticipated. Which iterative refinement technique is most appropriate here?

A) Write a detailed specification document and pass it to Claude for direct implementation.
B) Use the interview pattern: ask Claude to question the team about their requirements, constraints, and assumptions before proposing a design.
C) Start with a minimal implementation and iterate by describing issues found during code review.
D) Provide a complete test suite first and ask Claude to write code that passes all tests.

**Correct Answer: B**
The interview pattern is designed to surface design considerations and uncover assumptions the developer may not have anticipated before any implementation begins. It is particularly valuable in domains like security where overlooked edge cases carry high risk. Option A bypasses the opportunity to surface gaps before implementation is locked in. Option C defers the discovery of design issues until after implementation, when the cost of changes is higher. Option D (test-driven iteration) is effective for well-defined behavior but cannot surface considerations the team has not yet thought of.

---

**Q49.** Claude Code generated a data transformation function that has three separate issues: an off-by-one error in a loop, a missing null check for an optional field, and an incorrect sort order. Each issue is in a completely different part of the function and none of them interact. What is the recommended approach for addressing these issues?

A) Report all three issues in a single detailed message so Claude has full context for all fixes at once.
B) Fix them sequentially: address each issue in a separate message and verify the fix before moving to the next.
C) Ask Claude to regenerate the entire function from scratch rather than patching the existing code.
D) Address the off-by-one error and null check together since they are in loops, then fix the sort order separately.

**Correct Answer: B**
When issues are independent, sequential iteration is appropriate: fixing each one separately and verifying the fix before moving on reduces the chance of fixes interfering with each other and makes each change easier to review. The guidance for sending all issues in a single message applies when the issues interact and Claude needs full context to resolve them together. Option A is suited to interacting problems, not independent ones. Option C discards working code unnecessarily. Option D creates an arbitrary grouping not based on actual interaction.

---

**Q51.** A developer has identified three issues in a data processing module: two logic bugs that interact because they both affect the same intermediate result, and a set of five inconsistent variable names scattered across multiple files. The logic bugs produce incorrect output only when both are present; the naming violations are independent style issues. How should these issues be addressed using iterative refinement?

A) Report all eight issues in a single message so Claude can resolve them together with full context.
B) Send the two interacting logic bugs in one message so Claude can resolve them together, then address the naming violations sequentially in separate follow-up messages after verifying the bug fixes.
C) Fix all naming violations first since they are simpler, then tackle the two logic bugs in a single message.
D) Fix each of the eight issues in eight separate sequential messages, verifying each before proceeding.

**Correct Answer: B**
The guidance for batching issues is based on whether they interact. The two logic bugs interact and Claude needs full context on both to resolve them correctly, so they should be reported together. The naming violations are independent and do not affect correctness, so sequential iteration is appropriate: fix each one and verify before moving to the next. Option A lumps all issues together, which adds noise when Claude is resolving the interacting bugs. Option C addresses ordering by complexity rather than by interaction. Option D applies sequential iteration to interacting bugs, which risks an incomplete fix.

---

**Q52.** A team is adding a caching layer to an existing microservice. The service was written two years ago by engineers who are no longer on the team, and its internal patterns for dependency injection and lifecycle management are unfamiliar to the current developer. Before writing any code, the developer wants to ensure Claude surfaces all relevant design considerations. Which iterative refinement technique is most appropriate?

A) Ask Claude to implement a generic Redis-based caching layer using standard patterns for the framework, then review its output for compatibility issues.
B) Use the interview pattern: ask Claude to question you about the service's architecture, existing lifecycle hooks, and caching requirements before proposing any design.
C) Provide the service's entry point files to Claude and ask it to generate a caching design document for review.
D) Start with a minimal proof-of-concept cache for one endpoint and iterate by describing any failures encountered during testing.

**Correct Answer: B**
The interview pattern is specifically designed for situations where the developer may not have anticipated all relevant design considerations. By asking Claude to question the developer about the service's patterns and constraints before implementing, it surfaces assumptions about lifecycle management, cache invalidation strategy, and dependency injection that the developer may not have known to specify upfront. Option A proceeds with generic patterns that may be incompatible with the unfamiliar service. Option C produces a design document but does not interactively surface considerations the developer has not yet thought of. Option D defers discovery to runtime failures rather than surfacing design issues before any code is written.

---

### Task 3.6: Integrate Claude Code into CI/CD pipelines

**Q10.** Your pipeline script runs `claude "Analyze this pull request for security issues"` but the job hangs indefinitely. Logs indicate Claude Code is waiting for interactive input. What's the correct approach?

A) Add the `-p` flag: `claude -p "Analyze this pull request for security issues"`
B) Set the environment variable `CLAUDE_HEADLESS=true` before running the command
C) Redirect stdin from `/dev/null`: `claude "Analyze this pull request for security issues" < /dev/null`
D) Add the `--batch` flag: `claude --batch "Analyze this pull request for security issues"`

**Correct Answer: A**
The `-p` (or `--print`) flag is the documented way to run Claude Code in non-interactive mode. Options B and D reference non-existent features. Option C is a Unix workaround that doesn't properly address Claude Code's command syntax.

---

**Q50.** A CI pipeline runs Claude Code to generate test cases for each pull request. The team discovers that Claude is consistently suggesting test scenarios that already exist in the existing test files, wasting review time. Which approach in the CLAUDE.md configuration most directly addresses this problem?

A) Add the `-p` flag to the CI invocation command to prevent interactive prompts.
B) Use `--output-format json` with `--json-schema` so that test suggestions are machine-parseable for deduplication.
C) Document in `CLAUDE.md` the testing standards, available fixtures, and instruct Claude to review existing test files before suggesting new scenarios.
D) Add a post-processing script to the pipeline that compares Claude's suggestions against the existing test files and filters duplicates.

**Correct Answer: C**
Providing existing test files in context and documenting testing standards in `CLAUDE.md` directly instructs Claude to avoid duplicate suggestions at generation time. This is the most efficient fix because it addresses the root cause: Claude does not know what tests already exist. Option A prevents interactive hangs but does not affect test content. Option B improves parseability but does not prevent duplicate suggestions. Option D is a workaround that adds pipeline complexity without fixing the underlying issue.

---

**Q53.** A CI pipeline uses Claude Code to review pull requests and needs to post inline comments on specific lines in GitHub. The pipeline currently receives Claude's output as unstructured text, which requires a fragile regex parser to extract file paths, line numbers, and comment text. The parser breaks regularly as Claude's output format drifts between runs. What is the most robust solution?

A) Add stricter formatting instructions to the system prompt specifying the exact text structure expected, and add validation to reject any response that does not match.
B) Use `--output-format json` combined with `--json-schema` to define a schema with `file`, `line`, and `comment` fields, so each finding is machine-parseable by construction.
C) Add a post-processing step that uses a second Claude call to normalize the first response into a consistent structured format.
D) Switch from inline comments to a single summary comment, which is easier to extract since it does not require line-level parsing.

**Correct Answer: B**
Using `--output-format json` with `--json-schema` produces structured output that conforms to the defined schema by construction, eliminating format drift entirely. The pipeline can parse the JSON directly without a regex layer. Option A makes prompt instructions more rigid but still relies on Claude maintaining format consistency across runs, which is the root cause of the breakage. Option C adds latency and cost by introducing a second API call for normalization. Option D changes the feature behavior to work around the parsing problem rather than solving it.

---

## Domain 4: Prompt Engineering & Structured Output

### Task 4.1: Design prompts with explicit criteria to improve precision and reduce false positives

**Q55.** A CI code review prompt flags 60% of pull requests for "potential security vulnerabilities." Developers have stopped reading the reports because nearly all flags are false positives on standard input validation patterns they consider acceptable. Adding "only report high-confidence findings" to the prompt has had no measurable effect. What is the most effective next step?

A) Replace the security review prompt with a rule-based static analysis tool that has zero false positives.
B) Temporarily disable the security category and add explicit criteria defining which patterns constitute a reportable vulnerability versus acceptable practice, with concrete code examples for each.
C) Increase the review model to a larger tier to improve its judgment on security issues.
D) Add a post-processing confidence threshold: discard any finding where Claude rates its own confidence below 80%.

**Correct Answer: B**
General instructions like "only report high-confidence findings" fail to reduce false positives because they do not define what counts as a positive. Temporarily disabling the noisy category restores developer trust immediately while explicit criteria with examples give Claude the specificity needed to distinguish real issues from acceptable patterns. Option A abandons the AI-based review entirely rather than fixing it. Option C is unlikely to change false positive rates when the root cause is imprecise criteria. Option D relies on self-reported confidence scores, which are poorly calibrated for LLMs.

---

**Q56.** A Claude-based pull request reviewer raises "magic number" warnings on every numeric literal in the codebase, including well-understood constants like HTTP status codes and standard buffer sizes. Developers want magic numbers flagged only when they appear in business logic with no explanation. How should the prompt be updated?

A) Add an instruction to "use good judgment about whether numbers are truly magic numbers."
B) Define explicit criteria: flag numeric literals that appear in business logic calculations with no accompanying comment or named constant; exclude HTTP status codes, standard buffer sizes, and any value documented in a comment.
C) Add a severity field to findings and instruct Claude to omit any finding with severity "low."
D) Provide a list of allowed numeric values that should never be flagged.

**Correct Answer: B**
Explicit, specific criteria that define what to report and what to exclude are far more effective than general guidance or exclusion lists. Describing the precise conditions that make a number "magic" gives Claude a clear decision rule rather than requiring inference. Option A is the kind of vague instruction that causes the problem in the first place. Option C introduces a severity layer that does not address the underlying definitional problem. Option D would require maintaining an incomplete and fragile list that does not generalize to new values.

---

**Q57.** A Claude-based code reviewer is generating inconsistent feedback on documentation quality: sometimes flagging missing docstrings for private helper functions, sometimes not; sometimes requiring full parameter descriptions, sometimes accepting one-line summaries. The team wants consistent, predictable documentation feedback on public API functions only. Which change most directly addresses the inconsistency?

A) Instruct Claude to "apply documentation standards consistently and carefully."
B) Define explicit documentation criteria: public API functions must have a docstring with a one-sentence summary, parameter descriptions, and return value description; private functions are excluded from documentation checks.
C) Run three parallel review instances and accept feedback that appears in at least two of the three.
D) Restrict the review prompt to only one concern at a time, alternating between security, documentation, and style in separate runs.

**Correct Answer: B**
Explicit criteria that specify exactly what is required, for which functions, and at what level of detail eliminate the ambiguity that causes inconsistency. Without a clear definition of "documented," Claude must infer the threshold each time, leading to variable results. Option A is the type of general instruction that already produces the problem. Option C adds overhead and suppresses legitimate feedback that may only appear in one instance. Option D separates concerns but does not fix the definition of what counts as adequate documentation.

---

### Task 4.2: Apply few-shot prompting to improve output consistency and quality

**Q58.** A team uses Claude to generate code review comments for pull requests. The comments are technically accurate but vary widely in format: some include file paths and line numbers, others are vague summaries, some use bullet points, and others write prose paragraphs. Developers want a consistent, actionable format: file path, line number, issue description, suggested fix. What is the most effective way to achieve this?

A) Add a format specification to the system prompt listing the required fields.
B) Provide 2-4 few-shot examples in the prompt showing the exact desired output format for different types of issues, including file path, line number, issue description, and suggested fix.
C) Use `--output-format json` and parse the results in a post-processing step to normalize format.
D) Ask Claude to self-review its output and reformat any comment that does not match the required structure.

**Correct Answer: B**
Few-shot examples demonstrating the exact desired output format are the most effective technique for achieving consistently formatted output when detailed instructions alone produce inconsistent results. Seeing concrete examples of the format makes the requirement unambiguous. Option A is a format specification that has likely already been tried given the problem description. Option C introduces parsing complexity and does not ensure consistent generation. Option D adds a round-trip that may still produce inconsistent intermediate output.

---

**Q59.** A structured data extraction system is extracting contract clauses from legal documents. The model handles standard clauses well but consistently misclassifies ambiguous clauses that could fit two or more categories, such as a clause that contains both termination conditions and force majeure language. What few-shot prompting approach is most effective for improving accuracy on these edge cases?

A) Add more few-shot examples of standard, unambiguous clauses to reinforce the classification schema overall.
B) Create targeted few-shot examples that specifically demonstrate ambiguous-case handling: showing the reasoning for why a clause with both termination and force majeure language belongs to one category and not the other.
C) Switch from classification to extraction: ask Claude to extract the clause text without categorizing it, then apply a rule-based classifier.
D) Add a confidence score field and route all low-confidence classifications to human review without attempting to improve the model's judgment.

**Correct Answer: B**
Targeted few-shot examples for ambiguous scenarios that show the reasoning behind the classification decision are the most effective technique for improving handling of edge cases. Standard examples do not teach the model how to handle cases that span category boundaries. Option A reinforces behavior that already works rather than addressing the gap. Option C sidesteps the classification problem rather than solving it. Option D is a reasonable operational safeguard but does not improve model accuracy.

---

**Q60.** A document extraction system uses Claude to pull financial figures from quarterly earnings reports. The reports have varied formats: some use tables, some use inline prose, some use both. Extraction accuracy for tabular data is high (94%) but prose-only documents show only 72% accuracy. What is the most targeted approach to improve prose extraction accuracy?

A) Increase the system prompt's emphasis on accuracy with stronger language and more detailed instructions.
B) Add few-shot examples specifically showing correct extraction from prose-formatted documents, including cases where numbers appear in sentence form rather than tables.
C) Pre-process all documents to convert prose financial data into table format before sending to Claude.
D) Use a separate prompt for prose documents that instructs Claude to first identify all sentences containing numbers, then extract figures from those sentences only.

**Correct Answer: B**
Few-shot examples demonstrating correct extraction from documents with varied formats directly address the accuracy gap on prose documents. The model already generalizes well to tabular data; the gap is in prose, and targeted examples for that format close the gap most efficiently. Option A relies on emphasis, which does not resolve structural pattern differences. Option C requires reliable pre-processing of arbitrarily structured prose, which is non-trivial. Option D adds complexity and may miss numbers that are discussed without appearing in sentences Claude isolates.

---

### Task 4.3: Enforce structured output using tool use and JSON schemas

**Q61.** Your extraction pipeline uses a prompt that requests JSON output with a code block. In production, approximately 3% of responses have JSON syntax errors: missing commas, unescaped characters, or truncated objects. These errors break your downstream parser and require manual reprocessing. What is the most reliable way to eliminate JSON syntax errors?

A) Add a validation step that re-runs the prompt if the output fails JSON parsing, up to 3 retries.
B) Switch to tool use with a defined JSON schema as the input parameter; extract structured data from the `tool_use` response block.
C) Add an instruction to the prompt: "Your response must be valid JSON. Double-check for syntax errors before responding."
D) Use a regex post-processor to fix the most common syntax errors before passing output to the parser.

**Correct Answer: B**
Tool use with a JSON schema guarantees schema-compliant structured output by construction, eliminating syntax errors entirely. The model populates the tool call's input parameters according to the schema rather than generating free-text JSON. Option A reduces the frequency of failures but does not eliminate syntax errors. Option C relies on model self-checking, which does not provide the deterministic guarantee that tool use provides. Option D is a fragile workaround that cannot handle all syntax error patterns.

---

**Q62.** Your structured data extraction pipeline processes invoices. You have two extraction tools: `extract_invoice_schema` and `extract_receipt_schema`. For each document, you do not know in advance which type it is. After switching to `tool_choice: "auto"`, you observe that 30% of the time the model returns a text description of what it found rather than calling either tool. What is the correct fix?

A) Set `tool_choice: "any"` to guarantee the model calls one of the available extraction tools without specifying which one.
B) Set `tool_choice: {"type": "tool", "name": "extract_invoice_schema"}` to always call a specific tool.
C) Add a system prompt instruction: "Always call one of the extraction tools and never return text."
D) Merge both schemas into a single `extract_document_schema` tool with an optional `document_type` field.

**Correct Answer: A**
`tool_choice: "any"` guarantees the model calls a tool rather than returning conversational text, without requiring you to specify which tool. This is exactly the documented use case when you have multiple valid tools and want to ensure one is called. Option B forces a specific tool, which defeats the purpose when you do not know the document type in advance. Option C is a prompt-based approach with probabilistic compliance, which already failed as evidenced by the 30% text response rate. Option D is a valid architectural change but requires more engineering effort than a single configuration change.

---

### Task 4.4: Implement validation, retry, and feedback loops for extraction quality

**Q63.** An invoice extraction pipeline uses tool use with a strict JSON schema. After validation, 8% of extracted invoices fail a business rule check: the sum of line item amounts does not equal the `total_amount` field. These are semantic errors, not schema syntax errors. The invoices are well-formed documents with no missing data. How should you implement the retry loop?

A) Retry up to 3 times with the same prompt; schema-compliant extraction will converge on a valid answer with additional attempts.
B) On failure, append the original document, the failed extraction, and the specific validation error ("line items sum to X but total_amount is Y") to the follow-up prompt for model self-correction.
C) Flag all invoices with this error as missing data and route them directly to human review without retry.
D) Add a `calculated_total` field to the schema and populate it with the sum of line items in post-processing, then use the calculated total as the canonical value.

**Correct Answer: B**
Retry-with-error-feedback works by giving the model the specific discrepancy it needs to self-correct. Since the invoices are well-formed and the data is present, the model has the information it needs to fix the arithmetic alignment on retry. Option A retries without feedback and is unlikely to improve results since the model will reproduce the same error. Option C routes to human review prematurely when a retry with feedback could resolve the issue. Option D silently replaces the model's extracted total with a calculated value, which could propagate errors if the line items themselves were extracted incorrectly.

---

**Q64.** A CI code review pipeline is generating false positive findings at a high rate. The team wants to understand which specific code constructs are being flagged incorrectly so they can refine the prompt. The current findings output only includes `file`, `line`, and `description`. What schema change would best enable systematic false positive analysis?

A) Add a `confidence` field (0-100) to each finding so the team can filter by confidence threshold.
B) Add a `detected_pattern` field to each finding that records the specific code construct or pattern that triggered the finding.
C) Add a `category` field so findings can be grouped by issue type for aggregate analysis.
D) Add an `is_false_positive` boolean field and instruct Claude to self-label its own false positives.

**Correct Answer: B**
The `detected_pattern` field directly captures what code construct triggered each finding, enabling the team to identify which patterns produce the most false positives and update prompt criteria accordingly. Option A provides confidence scores but does not identify what prompted the finding. Option C allows grouping but not pattern-level debugging. Option D asks Claude to self-identify its own false positives, which is unreliable since the model cannot accurately distinguish true from false positives without ground truth.

---

**Q67.** A financial document extraction pipeline is failing on the "guarantor address" field for a set of loan summaries. After 3 retry attempts with error feedback, the field still extracts as null. Each retry prompt includes the original document and the validation error. What should you investigate before scheduling further retries?

A) Increase the retry limit from 3 to 5, since complex field extraction may require more attempts to converge.
B) Check whether the guarantor address is actually present in the loan summary document, or whether the document only references it by directing the reader to an external exhibit.
C) Switch to a larger model tier for the retry attempts, since the current model may lack the reasoning capacity for this field.
D) Restructure the schema to make the guarantor address field optional, allowing the pipeline to proceed when the field cannot be extracted.

**Correct Answer: B**
Retries are only effective when the information needed to satisfy the validation is present in the document. A loan summary that references guarantor details in an external exhibit does not contain the address. No number of retries will extract information that is not in the input. Before adding retry cycles, validate that the target field is actually present in the source document. Option A adds more retries without diagnosing why the existing retries are failing. Option C may improve performance on difficult extractions but does not address absence of data. Option D removes the validation rather than diagnosing the root cause.

---

### Task 4.5: Design efficient batch processing strategies

**Q11.** Your team wants to reduce API costs. Two workflows: (1) a blocking pre-merge check that must complete before developers can merge, and (2) a technical debt report generated overnight for review the next morning. Your manager proposes switching both to the Message Batches API for 50% cost savings. How should you evaluate this proposal?

A) Use batch processing for the technical debt reports only; keep real-time calls for pre-merge checks.
B) Switch both workflows to batch processing with status polling to check for completion.
C) Keep real-time calls for both workflows to avoid batch result ordering issues.
D) Switch both to batch processing with a timeout fallback to real-time if batches take too long.

**Correct Answer: A**
The Message Batches API has up to 24-hour processing times with no guaranteed latency SLA. This makes it unsuitable for blocking pre-merge checks but ideal for overnight batch jobs. Option B is wrong because relying on "often faster" completion isn't acceptable for blocking workflows. Option C reflects a misconception: batch results can be correlated using `custom_id` fields.

---

**Q65.** A compliance team runs a weekly audit that analyzes 50,000 contract documents for regulatory clauses. The audit results are reviewed by a compliance analyst every Monday morning. The team is considering the Message Batches API. A colleague raises a concern: "What if a batch fails partway through the 50,000 documents?" How should partial batch failures be handled?

A) Always resubmit the entire batch; tracking partial failures adds implementation complexity.
B) Use the `custom_id` field to correlate each request with its response, identify which documents returned error responses, and resubmit only those documents in a new batch.
C) Set a shorter processing window timeout to force faster completion and reduce the risk of partial failures.
D) Switch to real-time API calls with retry logic; the batch API is not suitable for mission-critical compliance workloads.

**Correct Answer: B**
The `custom_id` field is specifically designed for correlating batch request and response pairs, enabling teams to identify which documents failed and resubmit only those, avoiding the cost of reprocessing the entire batch. Option A wastes 50% cost savings by reprocessing successful documents. Option C misunderstands the batch API; processing windows are managed by Anthropic and cannot be shortened on demand. Option D is overly conservative: the batch API is appropriate for non-blocking, latency-tolerant compliance audits, which this workflow is.

---

### Task 4.6: Design multi-instance and multi-pass review architectures

**Q12.** A pull request modifies 14 files across the stock tracking module. Your single-pass review produces inconsistent results: detailed feedback for some files, superficial comments for others, obvious bugs missed, and contradictory feedback. How should you restructure the review?

A) Split into focused passes: analyze each file individually for local issues, then run a separate integration-focused pass examining cross-file data flow.
B) Require developers to split large PRs into smaller submissions of 3-4 files before the automated review runs.
C) Switch to a higher-tier model with a larger context window to give all 14 files adequate attention in one pass.
D) Run three independent review passes on the full PR and only flag issues that appear in at least two of the three runs.

**Correct Answer: A**
Splitting reviews into focused passes directly addresses attention dilution. Option B shifts burden to developers without improving the system. Option C misunderstands that larger context windows don't solve attention quality issues. Option D would suppress detection of real bugs by requiring consensus on issues that may only be caught intermittently.

---

**Q66.** A developer generates a 300-line module using Claude Code in one session, then asks the same session to review the code for bugs. The review returns "looks good" with minor style suggestions but misses two logic errors that a colleague catches in manual review. What is the most likely cause, and what architectural change addresses it?

A) The context window was too large; the fix is to limit code generation to smaller chunks so the review has less to process.
B) The reviewing instance retains reasoning context from generation, making it less likely to question its own decisions. Use a second independent Claude instance without the generation context to perform the review.
C) The review prompt was too vague; adding more explicit review criteria to the same session would catch the missed errors.
D) The model tier used for generation is more capable than the one used for review; switching both to the same tier resolves the quality gap.

**Correct Answer: B**
Self-review limitation is a known pattern: when a model retains the reasoning context from code generation, it is less likely to identify errors in its own output. An independent review instance without the generator's context approaches the code without prior assumptions and catches issues the generating instance would overlook. Option A addresses context length, not reasoning context bias. Option C might improve detection of certain categories of issues but does not address the fundamental self-review limitation. Option D addresses model selection, not the structural problem of reviewing one's own output.

---

**Q68.** A developer builds a code generation pipeline where Claude generates a 200-line module, and then the same session reviews the generated code for correctness. The review returns only minor style suggestions and misses a logic error in the error handling path. A second developer reviewing the code manually finds the bug immediately. What architectural change would make the review phase more effective?

A) Add more explicit review criteria to the generation session's system prompt to help it catch logic errors.
B) Use a second independent Claude instance without the generation context to perform the review, since the generating instance retains reasoning context that makes it less likely to question its own decisions.
C) Run the review immediately after generation before any other tool calls accumulate in the context window.
D) Switch to a larger model tier for the review step to improve reasoning quality.

**Correct Answer: B**
When a model reviews code it generated in the same session, it retains the reasoning context from generation and is less likely to identify errors in its own output. An independent review instance approaches the code without prior assumptions and catches issues the generating instance overlooks. This is the documented rationale for multi-instance review architectures. Option A improves the review prompt but does not address the fundamental self-review limitation. Option C manages context length but does not remove the generator's retained reasoning bias. Option D improves general capability but does not change the structural problem of a model reviewing its own work.

---

## Domain 5: Context Management & Reliability

### Task 5.1: Manage conversation context to preserve critical information across long interactions

**Q69.** A customer support agent is handling a complex billing dispute that spans 20+ turns. A customer mentioned early in the conversation that they were charged $847.50 on March 3rd for a service they cancelled on February 28th. Midway through the conversation, the agent references the charge as "the overcharge from last month" without the specific amount. The customer disputes the agent's understanding of the case. What context management technique would prevent this?

A) Use `/compact` at the start of each conversation to summarize prior turns into a shorter representation.
B) Extract transactional facts (amounts, dates, order numbers, statuses) into a persistent "case facts" block that is included at the beginning of every subsequent prompt in the conversation.
C) Increase the model's context window by switching to a larger tier to retain the full conversation without summarization.
D) Instruct the agent to re-read the full conversation history before each response.

**Correct Answer: B**
Extracting precise transactional facts into a persistent "case facts" block ensures that specific numerical values, dates, and customer-stated details are explicitly available in every prompt turn rather than buried in growing conversation history. Progressive summarization risks condensing these details into vague references like "overcharge from last month." Option A's compaction is useful for context length management but can lose precision on transactional facts. Option C does not prevent progressive summarization and is not a reliable solution. Option D is not practical for long conversations and still does not prevent facts from being lost as context grows.

---

**Q70.** A multi-agent research pipeline aggregates findings from six subagents, each returning 800-1,200 tokens of raw tool output and reasoning. The synthesis agent receives all results in a single large message. The final report consistently omits or contradicts findings that appeared in the middle sections of the aggregated input. What is the most likely cause and the most effective mitigation?

A) The subagents are returning conflicting information; add a deduplication step before synthesis.
B) The synthesis agent is hitting its output token limit; increase `max_tokens` to allow a longer response.
C) The "lost in the middle" effect causes models to reliably process content at the beginning and end of long inputs but miss middle sections. Mitigate by placing key findings summaries at the beginning of aggregated inputs and organizing sections with explicit headers.
D) The synthesis agent's context window is exhausted; route some subagent outputs through a secondary summarization agent before passing to synthesis.

**Correct Answer: C**
The "lost in the middle" effect is a well-documented limitation where models attend less reliably to content in the middle of long inputs. Placing key findings at the beginning and using explicit section headers to organize the aggregated input significantly mitigates this effect. Option A addresses data consistency but not the positional attention problem. Option B addresses output length, not input attention. Option D adds pipeline complexity and may help with context length, but does not address the positional attention issue on its own.

---

### Task 5.2: Design effective escalation and ambiguity resolution patterns

**Q3.** Your agent achieves 55% first-contact resolution, well below the 80% target. Logs show it escalates straightforward cases while attempting to autonomously handle complex situations requiring policy exceptions. What's the most effective way to improve escalation calibration?

A) Add explicit escalation criteria to your system prompt with few-shot examples demonstrating when to escalate versus resolve autonomously.
B) Have the agent self-report a confidence score (1-10) before each response and automatically route requests to humans when confidence falls below a threshold.
C) Deploy a separate classifier model trained on historical tickets to predict which requests need escalation before the main agent begins processing.
D) Implement sentiment analysis to detect customer frustration levels and automatically escalate when negative sentiment exceeds a threshold.

**Correct Answer: A**
Adding explicit escalation criteria with few-shot examples directly addresses the root cause: unclear decision boundaries. Option B fails because LLM self-reported confidence is poorly calibrated. Option C is over-engineered. Option D solves a different problem entirely.

---

**Q71.** A customer opens a support chat saying "I'd like to speak to a human please. I've been dealing with this billing issue for three weeks and I'm frustrated." The agent has already identified this as a standard billing adjustment that it can resolve in 2 steps using its available tools. Your agent responds by saying "I can help with that right away, let me pull up your account." and proceeds to investigate. The customer repeats their request for a human. What is wrong with this behavior and what should be corrected?

A) The agent should honor an explicit customer request for a human agent immediately on first request, without attempting investigation first.
B) The agent should detect negative sentiment and escalate once the frustration score exceeds a defined threshold.
C) The agent should complete its investigation, present the proposed solution, and escalate only if the customer still insists afterward.
D) The agent should apologize for the wait, then proceed with automated resolution since the case is within its capability.

**Correct Answer: A**
When a customer explicitly requests a human agent, that request must be honored immediately regardless of whether the agent believes it can resolve the issue. Proceeding with investigation after a clear escalation request violates the design principle documented in Task 5.2. Option B introduces sentiment scoring as a proxy, but the customer has already expressed an explicit preference. Sentiment analysis is irrelevant here. Option C delays honoring the request while investigation proceeds, which further frustrates the customer. Option D is the agent's current incorrect behavior: capability is not the deciding factor when a customer has made an explicit request.

---

### Task 5.3: Implement error propagation strategies across multi-agent systems

**Q72.** Your web search subagent encounters a timeout while fetching results for a competitor analysis. The engineering team implements a change so the subagent catches the timeout internally and returns an empty result set with `status: "success"` and `results: []`. The coordinator receives this and the synthesis agent produces a report that is missing the competitive section entirely, with no indication anything went wrong. What is the problem with this approach?

A) Silently returning an empty success result prevents the coordinator from making any recovery decision and allows incomplete work to pass as complete output.
B) The synthesis agent should be responsible for detecting empty sections and re-triggering the search subagent directly.
C) The coordinator should always validate that each subagent returned non-empty results before proceeding to synthesis.
D) The timeout threshold should be increased so that the subagent does not time out before returning real results.

**Correct Answer: A**
Silently suppressing errors by returning empty results as success is an explicitly documented anti-pattern. It removes the coordinator's ability to recover, retry, or annotate output with coverage gaps. Option B incorrectly shifts the recovery responsibility to the synthesis agent, which lacks the tools and context to re-run searches. Option C adds coordinator-level validation as a safeguard, but it does not address the root cause: the subagent is misrepresenting failure as success. Option D addresses the symptom (timeout threshold) rather than the error propagation design flaw.

---

### Task 5.4: Manage context effectively in large codebase exploration

**Q73.** An agent is performing a deep exploration of a 200,000-line legacy codebase to understand its payment processing flow. After approximately 90 minutes and dozens of file reads, the agent begins referencing "standard patterns in payment systems" rather than the specific classes and flows it found earlier, and its answers become inconsistent with findings from the first hour. What is the most likely cause and the best mitigation strategy?

A) The agent has reached a rate limit; the fix is to add delays between tool calls to stay within limits.
B) Context degradation: as the session grows, specific findings from early in the session compete with general knowledge and the agent's position-attention effects. Mitigate by having the agent maintain a scratchpad file recording key findings throughout the session.
C) The legacy codebase's file structure is too complex for a single agent; break it into independent subsystems and run separate agents on each subsystem simultaneously.
D) The agent is using the wrong tools; switching from `Read` to `Grep` for file exploration would reduce context consumption.

**Correct Answer: B**
Context degradation in extended sessions is a known pattern: models start giving inconsistent answers and referencing general knowledge rather than specific findings discovered earlier. Having the agent maintain a scratchpad file that records key findings creates a persistent, explicit record that can be referenced and included in subsequent prompts, preventing specific details from being lost to context pressure. Option A misidentifies the cause as a rate limit. Option C adds parallelism but does not address the single-session degradation problem. Option D changes tooling but does not address context growth or degradation.

---

**Q74.** You are running a multi-phase codebase investigation using the Claude Agent SDK. After 45 minutes of exploration (reading files, tracing call chains, building a dependency map) you move into the second phase: identifying security vulnerabilities in the authentication module. You notice the agent is now describing the authentication module as "using standard JWT patterns" when earlier in the session it had found a custom token signing implementation. What technique would most effectively preserve key findings across these phase boundaries?

A) Have the agent maintain a scratchpad file that records key findings after each phase, and reference that file at the start of subsequent phases rather than relying on conversation history.
B) Use `/compact` before starting the second phase to free up context space and allow the agent to re-read files as needed.
C) Restart the session with a fresh context at the start of each phase, passing a manual summary of what you found.
D) Increase the `max_tokens` parameter so the model can hold more context without compressing earlier findings.

**Correct Answer: A**
Scratchpad files are the recommended technique for persisting key findings across context boundaries when context degradation becomes apparent. The agent can write structured notes during exploration and read them back at phase boundaries, ensuring critical findings, like the custom token signing implementation, are not lost to context compression. Option B uses `/compact` to free up space, but this compresses conversation history and may lose the specific finding about the custom token signing. Option C is a valid but costly approach: restarting sessions loses the accumulated understanding and requires manual intervention. Option D is incorrect because `max_tokens` controls output length, not context window size, and would not prevent the degradation.

---

### Task 5.5: Design human review workflows and confidence calibration

**Q75.** A structured data extraction system for insurance claims achieves 97% overall accuracy on a validation set. The team proposes automating the full workflow without human review. A colleague argues this aggregate metric masks important risks. What is the most important concern?

A) 97% accuracy means 3% of claims will have errors, which could create legal liability if unchecked.
B) Aggregate accuracy metrics can mask poor performance on specific document types or fields. A claim type or field category with 85% accuracy would be hidden by strong performance elsewhere, and stratified analysis is needed before automating.
C) The validation set may not be representative of production data volumes, so the 97% figure cannot be trusted.
D) Human review should always be retained regardless of accuracy metrics because automation of insurance decisions creates regulatory risk.

**Correct Answer: B**
The core risk is that aggregate metrics can hide poor performance on specific segments. A document type with 85% accuracy on a critical field like `claim_amount` would be masked by strong performance across other document types. Before automating, accuracy should be validated by document type and field segment to confirm consistent performance across all dimensions. Option A is a valid concern but describes the error rate, not the masking risk. Option C raises a data quality concern but is not the most important concern about the specific 97% figure. Option D makes a policy argument that does not engage with the analytical gap identified.

---

**Q76.** An extraction pipeline achieves high accuracy on average but the team wants to implement confidence-based routing: high-confidence extractions proceed automatically while low-confidence ones go to human review. A developer proposes using the model's stated confidence scores directly as the routing threshold. What is the critical flaw in this approach?

A) Confidence scores add tokens to every response, increasing API costs unnecessarily.
B) Model confidence scores must be calibrated against a labeled validation set to determine what score threshold actually corresponds to acceptable accuracy. Uncalibrated raw scores are not reliable predictors of extraction correctness.
C) Confidence scores only work when the model outputs a single extraction; multi-field documents require a different approach.
D) Routing on confidence scores creates two separate code paths that are harder to maintain than a single uniform review workflow.

**Correct Answer: B**
A model's raw confidence scores need calibration: without comparing stated confidence against actual correctness on a labeled validation set, there is no reliable mapping between a score of "0.85" and an acceptable error rate. Calibrating the threshold ensures that the routing cut-off corresponds to a known accuracy level. Option A is a minor operational concern, not a critical flaw. Option C is incorrect; confidence scores can be applied at the field level for multi-field documents. Option D is an engineering tradeoff, not a flaw in the confidence approach itself.

---

### Task 5.6: Preserve information provenance and handle uncertainty in multi-source synthesis

**Q77.** A research synthesis agent is combining findings from five subagents that searched different sources. The final report states that "AI adoption in healthcare reached 45% in 2024" but does not cite which source this came from. A reviewer cannot verify the claim because the subagents' individual outputs were not preserved. What structural change to the pipeline would prevent this provenance loss?

A) Require the synthesis agent to add a generic "Sources consulted" section at the end of the report listing all sources accessed.
B) Require subagents to output structured claim-source mappings (claim text, source URL, document name, relevant excerpt) and instruct the synthesis agent to preserve and merge these mappings into the final report rather than summarizing them away.
C) Store all raw subagent outputs in a separate log file so they can be consulted if a claim needs verification.
D) Add a post-synthesis review step where a separate agent checks each claim in the report against the raw subagent outputs.

**Correct Answer: B**
The root cause of provenance loss is that summarization steps compress findings without preserving claim-to-source mappings. Requiring subagents to output structured mappings and instructing the synthesis agent to preserve and merge them ensures that each claim in the final report carries its source attribution through the pipeline. Option A produces a list of sources consulted but does not link individual claims to specific sources. Option C stores raw data as a fallback but does not integrate provenance into the report itself. Option D adds a verification step after the fact but does not prevent the structural provenance loss.

---

## Answer Key

| Q | Answer | | Q | Answer | | Q | Answer | | Q | Answer |
|---|--------|-|---|--------|-|---|--------|-|---|--------|
| 1 | A | | 21 | C | | 41 | B | | 61 | B |
| 2 | B | | 22 | B | | 42 | A | | 62 | A |
| 3 | A | | 23 | C | | 43 | B | | 63 | B |
| 4 | A | | 24 | C | | 44 | B | | 64 | B |
| 5 | A | | 25 | B | | 45 | B | | 65 | B |
| 6 | A | | 26 | B | | 46 | B | | 66 | B |
| 7 | B | | 27 | B | | 47 | B | | 67 | B |
| 8 | A | | 28 | A | | 48 | B | | 68 | B |
| 9 | A | | 29 | C | | 49 | B | | 69 | B |
| 10 | A | | 30 | A | | 50 | C | | 70 | C |
| 11 | A | | 31 | B | | 51 | B | | 71 | A |
| 12 | A | | 32 | B | | 52 | B | | 72 | A |
| 13 | B | | 33 | B | | 53 | B | | 73 | B |
| 14 | B | | 34 | B | | 54 | A | | 74 | A |
| 15 | B | | 35 | B | | 55 | B | | 75 | B |
| 16 | C | | 36 | C | | 56 | B | | 76 | B |
| 17 | B | | 37 | B | | 57 | B | | 77 | B |
| 18 | B | | 38 | B | | 58 | B | | | |
| 19 | B | | 39 | C | | 59 | B | | | |
| 20 | B | | 40 | B | | 60 | B | | | |

---

*Retro-engineered practice exam based on the Claude Certified Architect. Foundations Exam Guide (v0.1, Feb 2025). 77 questions across 5 domains. Not an official Anthropic product.*
