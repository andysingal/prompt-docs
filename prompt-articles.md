[LLM Prompter: Advanced](https://rodrigobaron.com/posts/llm-prompter-advanced)

[Building a Hybrid Rule-Based and Machine Learning Framework to Detect and Defend Against Jailbreak Prompts in LLM Systems](https://www.marktechpost.com/2025/09/21/building-a-hybrid-rule-based-and-machine-learning-framework-to-detect-and-defend-against-jailbreak-prompts-in-llm-systems/)

[How System Prompts Reveal Model Biases](https://blog.nilenso.com/blog/2026/02/12/how-system-prompts-reveal-model-biases/)
Claude Code
- ```You can call multiple tools in a single response```. - This line appears 7 times in the system prompt! Once in the generic tool use policy, and then it is repeated inside almost every tool’s instruction.
- ```If you intend to call multiple tools and there are no dependencies between the calls, make all of the independent calls in the same response```. - This is repeated 4 times, right next to the previous sentence.
```Maximize use of parallel tool calls where possible to increase efficiency```
```If the user specifies that they want you to run tools "in parallel", you MUST send a single message with multiple tool use content blocks```. – This is repeated twice.
```For example, if you need to launch multiple agents in parallel, send a single message with multiple Task tool calls```. This appears in 3 different ways in 3 different tool instructions.
Cursor
Has a full section called ```maximize_parallel_tool_calls``` with repeated instructions, and in SCREAMING case.
```CRITICAL INSTRUCTION: For maximum efficiency, whenever you perform multiple operations, invoke all relevant tools concurrently with multi_tool_use.parallel rather than sequentially```
```MANDATORY: Run multiple Grep searches in parallel with different patterns and variations;```
```For instance, all of these cases SHOULD use parallel tool calls:```
```Searching for different patterns (imports, usage, definitions) should happen in parallel```
```And you should use parallel tool calls in many more cases beyond those listed above```
```DEFAULT TO PARALLEL: Unless you have a specific reason why operations MUST be sequential```
```Parallelize tool calls per <maximize_parallel_tool_calls>: batch read-only context reads and independent edits instead of serial drip calls.```
Gemini CLI
This seems to be the mildest of the lot, although we only know about this from Gemini 3 onwards.
```Use 'grep' and 'glob' search tools extensively (in parallel if independent) to understand file structures```
```Execute multiple independent tool calls in parallel when feasible (i.e. searching the codebase)```
```If you need to read multiple files, you should make multiple parallel calls to 'read_file'.```
```**Parallelism:** Execute multiple independent tool calls in parallel when feasible (i.e. searching the codebase).```
Kimi CLI
This has just one emphatic line. But this is the smallest system prompt of the lot too.
```you are HIGHLY RECOMMENDED to make them in parallel to significantly improve efficiency```
Codex CLI
Codex added support for parallel tool calls only a few months ago. With the original implementation, the instructions were quite explicit, and comparable to other models. -```Only make sequential calls if you truly cannot know the next file without seeing a result first.```
```Always maximize parallelism., Batch everything., Never read files one-by-one unless logically unavoidable..```
However, with the 5.2 model release, all this instruction vanished, and was replaced with a single line instruction.
```Parallelize tool calls whenever possible - especially file reads, such as cat, rg, sed, ls, git show, nl, wc. Use multi_tool_use.parallel to parallelize tool calls and only this.```
