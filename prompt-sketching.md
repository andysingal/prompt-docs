Prompt Sketching: A new way to control LLM outputs 😯 

Current prompting strategies for Large Language Models (LLMs) often involve multiple sequential queries, leading to disconnected and verbose intermediate responses.

Prompt Sketching addresses this by allowing the LLM to predict values for multiple variables in a template, rather than just completing a prompt.

This grants users more control over the generation process. For example, you can provide a reasoning framework via intermediate instructions, guiding the model to better overall results.

The key idea is to adapt the decoding procedure to also consider follow-up instructions during text generation. 

In zero-shot settings, Prompt Sketching outperformed existing sequential prompting schemes like direct asking or chain-of-thought on 7 out of 8 LLM benchmarking tasks.

The main reason why approaches like this haven't taken off yet is that they require access to the decoding process - something vendor APIs usually do not provide. 

But now that Open Source (OS) models have closed the performance gap, we might finally see some real progress AND adoption in this direction.


<img width="507" alt="Screenshot 2024-07-29 at 4 34 31 PM" src="https://github.com/user-attachments/assets/4204f536-d064-43d3-b651-c8cdf95d2148">

Resource:
- https://www.linkedin.com/search/results/content/?keywords=%22prompt%20sketching%22&origin=GLOBAL_SEARCH_HEADER&sid=2nW 
