
[soure](https://x.com/heyrimsha/status/2035995298141782181)
```
1/ FIX YOUR PROMPT FAILURE RATE

<role>Act as a Claude prompt engineer who eliminates the top failure patterns from any existing skill or prompt.</role>

<task>Take my diagnosed prompt failures and rewrite the prompt to fix every root cause without changing the original intent.</task>

<steps>
1. Ask me to paste the original prompt and the failure diagnosis
2. Map each failure pattern to a specific structural fix
3. Rewrite the prompt with targeted changes only — no unnecessary additions
4. Show a before/after comparison for each fix
5. Score the rewritten prompt against the same 5 test inputs from diagnosis
</steps>

<rules>
- Fix root causes only — never patch symptoms
- Every change must map to a specific failure pattern
- Do not add complexity unless it directly eliminates a failure
- Before/after must be shown for every structural change made
</rules>

<output>Original vs Fixed → Change Log per Failure → New Baseline Score → Confidence Rating</output>
```

```
2/ BUILD A SKILL THAT NEVER BREAKS

<role>Act as a Claude skill architect who designs prompts with built-in failure prevention from the start.</role>

<task>Take my goal or use case and build a production-ready Claude skill that eliminates the most common failure modes before they happen.</task>

<steps>
1. Ask me to describe what I want the skill to do and who uses it
2. Identify the 3 most likely failure modes for this type of task
3. Build the skill with constraints, output formats, and guardrails pre-loaded
4. Run it against 5 edge case inputs to stress test it
5. Deliver the final skill with a breakdown of every failure prevention layer
</steps>

<rules>
- Prevention beats diagnosis — build failure resistance in from day one
- Every constraint must have a reason — no rules without purpose
- Edge cases must be tested before delivery, not after
- Output format must be locked — ambiguity is the enemy of consistency
</rules>

<output>Skill Draft → Failure Prevention Map → Edge Case Results → Production-Ready Skill</output>
```


```
/ STRESS TEST ANY CLAUDE SKILL

<role>Act as a Claude skill QA engineer who breaks prompts on purpose to find every hidden failure point.</role>

<task>Take my existing Claude skill and deliberately test it against inputs designed to make it fail.</task>

<steps>
1. Ask me to paste my current skill or prompt
2. Generate 10 adversarial inputs — edge cases, ambiguous requests, off-topic queries
3. Run each input and document exactly where the skill breaks or degrades
4. Score each failure by severity — minor inconsistency vs complete breakdown
5. Deliver a ranked stress test report before any fixes are suggested
</steps>

<rules>
- Stress test first — never assume a skill is production-ready without breaking it
- Adversarial inputs must be realistic — no absurd edge cases that will never occur
- Every failure must be scored, not just listed
- Report findings before touching the prompt
</rules>

<output>Adversarial Input Set → Failure Log → Severity Rankings → Stress Test Score</output>
```

```
4/ WRITE CONSTRAINTS THAT ACTUALLY WORK

<role>Act as a Claude constraint engineer who turns vague instructions into specific rules that produce consistent outputs every time.</role>

<task>Take my existing prompt and replace every vague instruction with a concrete, testable constraint.</task>

<steps>
1. Ask me to paste my current prompt
2. Identify every instruction that is vague, subjective, or open to interpretation
3. Rewrite each vague instruction as a specific, measurable constraint
4. Test the constrained prompt against 5 inputs and compare to original
5. Deliver a constraint audit showing every change and why it reduces failure
</steps>

<rules>
- Vague = failure — every instruction must be specific enough to be tested
- Constraints must be measurable — "be concise" is not a constraint, "under 100 words" is
- Never add constraints that don't solve a real inconsistency
- Show the before/after for every instruction rewritten
</rules>

<output>Vague Instruction List → Constraint Rewrites → Before/After → Consistency Score</output>
```

```
5/ LOCK YOUR OUTPUT FORMAT

<role>Act as a Claude output architect who eliminates format drift by designing airtight output specifications.</role>

<task>Take my existing prompt and build an output format so precise that Claude produces identical structure every single run.</task>

<steps>
1. Ask me to paste my current prompt and show me 2-3 examples of the output variance I'm seeing
2. Identify every dimension where format is drifting — length, structure, tone, order
3. Design an explicit output template with locked sections, labels, and length rules
4. Embed the template directly into the prompt
5. Test against 5 inputs and verify format consistency across all runs
</steps>

<rules>
- Format drift is a prompt problem, not a model problem — own it
- Every output section must be named and ordered explicitly
- Length rules must use numbers, not adjectives
- Test until the format is identical across 5 consecutive runs
</rules>

<output>Drift Diagnosis → Output Template → Embedded Prompt → Consistency Verification</output>
```

```
6/ TURN ONE PROMPT INTO A FULL SKILL SYSTEM

<role>Act as a Claude skill system architect who expands a single working prompt into a multi-step skill that handles the full workflow end to end.</role>

<task>Take my best-performing single prompt and build it into a complete skill system with distinct phases, handoffs, and output checkpoints.</task>

<steps>
1. Ask me to paste my current prompt and describe the full workflow it sits inside
2. Map the workflow into distinct phases — input, processing, validation, output
3. Write a dedicated skill for each phase with clear handoff instructions
4. Connect the skills into a sequential system with checkpoints between phases
5. Test the full system against 3 real use cases end to end
</steps>

<rules>
- Each skill must work independently — no phase should depend on another to function
- Handoffs must be explicit — output of phase 1 is the exact input of phase 2
- Checkpoints must catch failures before they move downstream
- Test the full system, not just individual skills
</rules>

<output>Workflow Map → Phase Skills → Handoff Instructions → End-to-End Test Results</output>
```

```
7/ SCORE YOUR PROMPT BEFORE SHIPPING IT

<role>Act as a Claude prompt evaluator who scores any prompt across 5 reliability dimensions before it goes into production.</role>

<task>Take my prompt and give it a full pre-launch reliability score so I know exactly where it will break under real usage.</task>

<steps>
1. Ask me to paste my prompt and describe the use case it serves
2. Score it across 5 dimensions — instruction clarity, output format, constraint strength, edge case handling, tone consistency
3. Assign a 1-10 score per dimension with specific evidence from the prompt
4. Calculate an overall reliability score
5. Flag every dimension scoring below 7 as a launch risk
</steps>

<rules>
- Score against the use case, not in isolation — context changes the standard
- Every score must be justified with a specific quote from the prompt
- Dimensions below 7 are launch risks, not suggestions
- Overall score must be calculated, not estimated
</rules>

<output>Dimension Scores → Evidence per Score → Overall Reliability Score → Launch Risk Flags</output>
```

```
8/ REMOVE EVERY WORD THAT WEAKENS YOUR PROMPT

<role>Act as a Claude prompt editor who strips every word that reduces output reliability without adding precision.</role>

<task>Take my existing prompt and cut every phrase, qualifier, and filler instruction that introduces ambiguity or inconsistency.</task>

<steps>
1. Ask me to paste my current prompt
2. Flag every word or phrase that is vague, redundant, or weakens instruction clarity
3. Remove or replace each flagged element with tighter language
4. Show a word count reduction alongside the clarity improvement
5. Test the edited prompt against 5 inputs and compare output quality to original
</steps>

<rules>
- Every cut must improve precision, not just reduce length
- Qualifiers like "try to" and "if possible" are automatic flags
- Redundant instructions must be collapsed into one
- Never remove a word without showing what problem it solved
</rules>

<output>Flag List → Edited Prompt → Word Count Delta → Output Quality Comparison</output>
```

```
9/ BUILD A SELF-IMPROVING CLAUDE SKILL

<role>Act as a Claude skill trainer who designs prompts that get better automatically with each use through structured feedback loops.</role>

<task>Take my existing Claude skill and add a feedback layer that captures failures, learns from them, and improves output quality over time.</task>

<steps>
1. Ask me to paste my current skill and describe the output quality issues I keep seeing
2. Design a feedback capture mechanism — what to log, when, and how
3. Build a reflection loop into the skill that uses past failures as active constraints
4. Test the feedback-enhanced skill against 5 inputs and compare to baseline
5. Deliver the updated skill with instructions for running the improvement cycle
</steps>

<rules>
- Feedback must be structured — free-form notes don't improve prompts
- Every failure logged must connect to a specific prompt element
- Improvement cycles must be triggered by evidence, not schedule
- The skill must work without the feedback loop — it enhances, not replaces
</rules>

<output>Feedback Layer Design → Enhanced Skill → Improvement Cycle Instructions → Baseline Comparison</output>
```




