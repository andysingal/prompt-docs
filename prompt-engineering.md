## Clear Instructions
The principle of giving clear instructions is to provide the model with enough information and guidance to perform the task correctly and efficiently. Clear instructions should include the following elements:

- The goal or objective of the task, such as “write a poem” or “summarize an article”.
- The format or structure of the expected output, such as “use four lines with rhyming words” or “use bullet points with no more than 10 words each”.
- The constraints or limitations of the task, such as “do not use any profanity” or “do not copy any text from the source”.
- The context or background of the task, such as “the poem is about autumn” or “the article is from a scientific journal”.
<img width="717" alt="Screenshot 2024-04-18 at 2 53 06 PM" src="https://github.com/andysingal/prompt-docs/assets/20493493/4dd2f8e4-bf5e-41bf-8570-bb34106fbcf0">

## Split complex tasks into subtasks
Prompt engineering is a technique that involves designing effective inputs for large language models (LLMs) to perform various tasks. Sometimes, the tasks are too complex or ambiguous for a single prompt to handle, and it is better to split them into simpler subtasks that can be solved by different prompts. Here are some examples of splitting complex tasks into subtasks:

1. Text summarization: A complex task that involves generating a concise and accurate summary of a long text. This task can be split into subtasks such as:
Extracting the main points or keywords from the text.
Rewriting the main points or keywords in a coherent and fluent way.
Trimming the summary to fit a desired length or format.
2. Machine translation: A complex task that involves translating a text from one language to another. This task can be split into subtasks such as:
Detecting the source language of the text.
Converting the text into an intermediate representation that preserves the meaning and structure of the original text.
Generating the text in the target language from the intermediate representation.
3. Poem generation: A creative task that involves producing a poem that follows a certain style, theme, or mood. This task can be split into subtasks such as:
Choosing a poetic form (such as sonnet, haiku, limerick, etc.) and a rhyme scheme (such as ABAB, AABB, ABCB, etc.) for the poem.
Generating a title and a topic for the poem based on the user’s input or preference.
Generating the lines or verses of the poem that match the chosen form, rhyme scheme, and topic.
Refining and polishing the poem to ensure coherence, fluency, and originality.
4. Code generation: A technical task that involves producing a code snippet that performs a specific function or task. This task can be split into subtasks such as:
Choosing a programming language (such as Python, Java, C++, etc.) and a framework or library (such as TensorFlow, PyTorch, React, etc.) for the code.
Generating a function name and a list of parameters and return values for the code based on the user’s input or specification.
Generating the body of the function that implements the logic and functionality of the code.
Adding comments and documentation to explain the code and its usage.

## Repeat instructions at the end 
Large Language Models tend not to process the metaprompt attributing the same weight or imprortance to all the sections. In fact, in his blog post “Large Language Model Prompt Engineering for Complex Summarization”, Microsoft’s Software Engineer John Stewart found out some interesting outcomes from arranging prompt sections. More specifically, after several experimentations, he found that repeating the main instruction at the end of the prompt can help the model to overcome its inner recency bias.

Definition

Recency bias is the tendency of large language models to give more weight to the information that appears near the end of a prompt, and ignore or forget the information that appears earlier. This can lead to inaccurate or inconsistent responses that do not take into account the whole context of the task. For example, if the prompt is a long conversation between two people, the model may only focus on the last few messages and disregard the previous ones.

One possible way to overcome recency bias is to break down the task into smaller steps or subtasks, and provide feedback or guidance along the way. This can help the model focus on each step and avoid getting lost in irrelevant details. 
<img width="670" alt="Screenshot 2024-04-18 at 3 15 05 PM" src="https://github.com/andysingal/prompt-docs/assets/20493493/b571689c-0bab-48d5-8a2e-bf046058584d">
