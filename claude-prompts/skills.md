A CLI skill that validates your SaaS idea before you write a single line of code
[launch_check](https://github.com/TiyaaaJain/launch-check)

[continuos_claude](https://github.com/parcadei/Continuous-Claude-v3)

```
> "Fix the login bug in auth.py"

🎯 SKILL ACTIVATION CHECK
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━

⚠️ CRITICAL SKILLS (REQUIRED):
  → create_handoff

📚 RECOMMENDED SKILLS:
  → fix
  → debug

🤖 RECOMMENDED AGENTS (token-efficient):
  → debug-agent
  → scout

ACTION: Use Skill tool BEFORE responding
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
```

```
---
name: pr-summary
description: Summarize changes in a pull request
context: fork
agent: Explore
allowed-tools: Bash(gh *)
---
## Pull request context
- PR diff: !`gh pr diff`
- PR comments: !`gh pr view --comments`
- Changed files: !`gh pr diff --name-only`

##Your task
Summarize this pull request
```
[mattpocock_skills](https://github.com/mattpocock/skills)

A collection of agent skills that extend capabilities across planning, development, and tooling


```
Let's create a skill together using your skill-creator skill. First ask me what the skill should do.

Skill Name: Outreach skill

Process and Knowledge:
Researching Prospects: The 5 minute habit
Effective research in 2026 is no longer about readin annual reports for 30 minutes, it is about targeted context gathering focused on specific trigers.
- Priortize Signals over Filmographics: While traditional data(industry, size)
- Structure for impact: Keep the message under 125 words. Use a three-part structure:
  1. Context: Why you are reaching out now (tied to a signal)
  2. Value: Stated as an outcome for a similar peer, not a feature list.
  3. Ask: A single, low-friction call to action
- Multichannel Sequences: Single-channel outreach leaves meetings on the table. Coordinated sequences involving Linkedin (Day 1), Email(Day 2), and Phone (
Day 4) increases response rates by 287%
- Timing: Research suggests emails sent at 1pm local time Tuesday through Thursday generate the highest engagement, while the 4-5 PM window is optimal for cold calls
- Persistence: It now takes an average o 18 touches to book a meeting, yet 44% of reps give up ater just one attempt. An effective sequence should run 14-21 days

Output: Use the Knowledge base to help generate work that aligns with the research

```

[AI-Research-SKILLs](https://github.com/Orchestra-Research/AI-research-SKILLs)


The "inject dynamic context" pattern in Claude Code skills is so useful.

IMO, this should be part of the "skills standard" and included in tools like Codex CLI, Pi, Cursor etc

<img width="727" height="668" alt="Screenshot 2026-04-11 at 9 34 08 PM" src="https://github.com/user-attachments/assets/0f80a35e-5db1-44b6-89f2-af4ddaa13b05" />

- 



## Article
- [How to Use Agent Skills in Enterprise LLM Agent Systems](https://dev.to/qtalen/how-to-use-agent-skills-in-enterprise-llm-agent-systems-15h2)
After spending the better part of a year building enterprise agent applications, I came to one conclusion: if your agent system can't plug into your company's existing business processes, it won't bring real value to your organization.
- [skill-scanner](https://github.com/cisco-ai-defense/skill-scanner) -- A best-effort security scanner for AI Agent Skills that detects prompt injection, data exfiltration, and malicious code patterns. Combines pattern-based detection (YAML + YARA), LLM-as-a-judge, and behavioral dataflow analysis to maximize detection coverage of probable threats while minimizing false positives.
- [Master Claude Skills](https://x.com/TheAIWorld22/status/2039650952937140267)
- [I Stopped Collecting Agent Skills. Started Wiring Them Into Loops](https://x.com/Voxyz_ai/status/2039704571165987213)
- [llm-wiki-skill](https://github.com/infranodus/skills/blob/master/skill-llm-wiki/SKILL.md)
Guide users through setting up a personal LLM-maintained wiki — a persistent, compounding knowledge base where the LLM incrementally builds and maintains interlinked markdown pages from raw sources. Use this skill when the user wants to: set up a personal knowledge base, create a research wiki, organize notes with LLM help, build a "second brain", set up an Obsidian + LLM workflow, create a persistent knowledge graph from documents, plan research priorities and next steps, or mentions "LLM wiki". This skill asks questions to understand the user's domain and goals, then scaffolds the entire wiki structure, schema, and workflows tailored to their needs. It also helps plan ongoing research by analyzing knowledge gaps and creating actionable todo lists.
- [paper-finder](https://github.com/bchao1/paper-finder/blob/main/SKILL.md)
Sharing a very simple Claude skill I created for ML literature survey. My experience with existing skills or ML paper search engines is that don't really capture how researchers *think* when doing literature search. Literature search is not just looking for keywords, but being creative, drawing parallels from different fields, and thinking two or three steps ahead. 

I iterated this skill with Claude a couple of times to refine it and I am pretty satisfied with its current hit rate. Topics I surveyed include efficient video tokenization, mixed-resolution diffusion / tokenization, etc, and it gave me pretty accurate results and found papers that went under my radar. 

Hope this is useful!

[Skill_manager_reseed](https://github.com/nattergabriel/reseed?twclid=2wx914zwaz90ysqka935hk7dd)

reseed manages your agent skills across projects. Keep all your skills in one central library, pull in open source ones from GitHub, and add exactly what each project needs. Instead of global skills that bloat every project, skills live in each project so every teammate has access to them.

If you find reseed useful, a ⭐ helps others discover it.

The best part: reseed is itself a skill. Drop it in, tell your agent "set up skills for this project," and it does the rest.

<img width="517" height="311" alt="Screenshot 2026-04-16 at 3 53 24 PM" src="https://github.com/user-attachments/assets/3eb032ae-dc47-40fc-bfd8-086a181b621e" />

