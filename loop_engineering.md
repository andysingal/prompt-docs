[Loop Engineering Isn't What You Think](https://x.com/techwith_ram/status/2064925285003542820)

- Generate. Review. Redirect. Repeat.
  
Loop Engineering Highlights Compilation!

After Agents began focusing on long tasks in 2026, the emphasis gradually shifted to:

How to design a loop system capable of continuously thinking, executing, observing, verifying, and evolving?

From Codex to Claude Code, from OpenHands to various Coding Agents.

The biggest gap between hobby projects and production-grade systems is Harness engineering, including Loop.

Can Agents work continuously for tens of minutes or even hours?

Can they recover after failure?

Can they control costs?

Can they know when to stop?

These questions ultimately boil down to Loop design.

📚 Recommended Reading

1. Loop Engineering — Addy Osmani
https://addyosmani.com/blog/loop-engineering/

2. Loop Engineering — Firecrawl
https://firecrawl.dev/blog/loop-engineering

3. What Is the AI Agent Loop? — Oracle
https://blogs.oracle.com/developers/what-is-the-ai-agent-loop-the-core-architecture-behind-autonomous-ai-systems

4. Harness Engineering — OpenAI
https://openai.com/index/harness-engineering/

5. Harness Engineering for Coding Agent Users — Martin Fowler
https://martinfowler.com/articles/harness-engineering.html

6. Agentic Loops: From ReAct to Loop Engineering
https://datasciencedojo.com/blog/agentic-loops-explained-from-react-to-loop-engineering-2026-guide/

7. Loop Engineering for AI Agents (Memory-First) — Mem0
https://mem0.ai/blog/loop-engineering-for-ai-agents-memory-first-design

📄 Recommended Papers
1. Agentic Harness Engineering
https://arxiv.org/abs/2604.25850

2. From Agent Loops to Structured Graphs
https://arxiv.org/abs/2604.11378

🛠 Recommended Open-Source Projects from Research
Codex CLI
https://github.com/openai/codex

OpenHands
https://github.com/All-Hands-AI/OpenHands

PydanticAI
https://github.com/pydantic/pydantic-ai

OpenAI Agents SDK
https://github.com/openai/openai-agents-python

Key Research Areas:
How Loops Run
How Loops Stop
How Loops Verify
How Loops Recover
How Loops Debug

Prompts determine how Agents start.
Context determines what Agents can see.
Loops determine how far Agents can ultimately go.

Loop Engineering:
Think
↓
Act
↓
Observe
↓
Verify
↓
Evolve
↓
Repeat

You design the loop.
Agents continuously improve within the loop.
Each completed loop brings the system closer to the goal than the last.
Agents never lack for Loops.
What's missing is the engineering of Loops.


```
You are helping me build a loop orchestration skill in Claude Code.

Goal of the loop: [the repeating task, in one sentence]
Definition of done: [the objective rule that means it's finished]

Build the skill with:
1. A trigger I can run as /[name]-loop
2. The execution skills it should call (list the ones that already exist)
3. A verification step that returns approved / not approved or a 1-10 score
4. A separate sub-agent to grade the output, not the agent that produced it
5. An output file and a memory file that logs what worked and what failed each run

Start in loop training mode: pause at every step for my approval before continuing.
Do not run past the done-check.
```

[loop-engineering](https://github.com/cobusgreyling/loop-engineering)


[Loop Engineering vs Harness Engineering: The Difference](https://www.aibuilderclub.com/blog/loop-engineering-vs-harness-engineering)



