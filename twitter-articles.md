[Prompt Caching Is Everything](https://x.com/trq212/status/2024574133011673516)
- <strong>Prompt caching</strong> works by prefix matching — the API caches everything from the start of the request up to each cache_control breakpoint. This means the order you put things in matters enormously, you want as many of your requests to share a prefix as possible.

The best way to do this is static content first, dynamic content last. For Claude Code this looks like:

- Static system prompt & Tools (globally cached)
- Claude.MD (cached within a project)
- Session context (cached within a session)
- Conversation messages

1. Plan Mode — Design Around the Cache
Plan mode is a great example of designing features around caching constraints. The intuitive approach would be: when the user enters plan mode, swap out the tool set to only include read-only tools. But that would break the cache.
Instead, we keep all tools in the request at all times and use EnterPlanMode and ExitPlanMode as tools themselves. When the user toggles plan mode on, the agent gets a system message explaining that it's in plan mode and what the instructions are — explore the codebase, don't edit files, call ExitPlanMode when the plan is complete. The tool definitions never change.
This has a bonus benefit: because EnterPlanMode is a tool the model can call itself, it can autonomously enter plan mode when it detects a hard problem, without any cache break.

<img width="1323" height="714" alt="Screenshot 2026-02-27 at 10 03 34 PM" src="https://github.com/user-attachments/assets/7097b020-9e4b-4217-9aa1-bb8c27a208d2" />

<u>Compaction is what happens when you run out of the context window</u>. We summarize the conversation so far and continue a new session with that summary.
Surprisingly, compaction has many edge cases with prompt caching that can be unintuitive.
In particular, when we compact we need to send the entire conversation to the model to generate a summary. If this is a separate API call with a different system prompt and no tools (which is the simple implementation), the cached prefix from the main conversation doesn't match at all. 

2. Tool Search — Defer Instead of Remove
The same principle applies to our tool search feature. Claude Code can have dozens of MCP tools loaded, and including all of them in every request would be expensive. But removing them mid-conversation would break the cache.
Our solution: ```defer_loading```. Instead of removing tools, we send lightweight stubs — just the tool name, with defer_loading: true — that the model can "discover" via a ToolSearch tool when needed. The full tool schemas are only loaded when the model selects them. This keeps the cached prefix stable: the same stubs are always present in the same order.

