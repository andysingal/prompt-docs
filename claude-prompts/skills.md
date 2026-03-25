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



## Article
- [How to Use Agent Skills in Enterprise LLM Agent Systems](https://dev.to/qtalen/how-to-use-agent-skills-in-enterprise-llm-agent-systems-15h2)
After spending the better part of a year building enterprise agent applications, I came to one conclusion: if your agent system can't plug into your company's existing business processes, it won't bring real value to your organization.
- [skill-scanner](https://github.com/cisco-ai-defense/skill-scanner) -- A best-effort security scanner for AI Agent Skills that detects prompt injection, data exfiltration, and malicious code patterns. Combines pattern-based detection (YAML + YARA), LLM-as-a-judge, and behavioral dataflow analysis to maximize detection coverage of probable threats while minimizing false positives.
