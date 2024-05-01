
A prompt is the input you provide, typically text, when interfacing with an AI model like ChatGPT or Midjourney. The prompt serves as a set of instructions the model uses to predict the desired response: text from Large Language Models (LLMs) like ChatGPT, or images from diffusion models like Midjourney.

Input
```
Can I have a list of product names for a pair of shoes that
can fit any foot size?
```

Output
```
Certainly! Here's a list of product names for a pair of shoes
that can fit any foot size:

UniFit SoleStrides
FlexiSize All-Fit Shoes
OmniFit FootFlex
...
AnyStep AdaptiWalkers
FlexiRange UniversalSteps
PerfectGlide MultiFit Shoes
```
If you were building a product name generator with thousands of users, there are some obvious issues you’d want attempt to fix:

```

1. Vague Direction: You’re not briefing the AI on what style of name you want, or what attributes it should have. Do you want a single word or a concatenation? Can the words be made up or is it important that they’re in real english? Do you want the AI to emulate somebody you admire who is famous for great product names?

2. Unformatted Output: You’re getting back a list of separated names line-by-line, of unspecified length. When you run this prompt multiple times you’ll see sometimes it comes back with a numbered list, and often it has text at the beginning which makes it hard to parse programmatically.

3. Missing Examples: You haven’t given the AI any examples of what good names look like. It’s autocompleting using an average of its training data, i.e. the entire internet (with all its inherent bias), but is that what you want? Ideally you’d feed it examples of successful names, common names in an industry, or even just other names you like.

4. Limited Evaluation: You have no consistent or scalable way to define which names are good or bad, so you have to manually review each response. If you can institute a rating system or other form of measurement, you can optimize the prompt to get better results, and identify how many times it fails.

5. No Task Division: You’re asking a lot of a single prompt here: there are lots of factors that go into product naming, and this important task is being naively outsourced to the AI all in one go, with no task specialization or visibility into how it’s handling this task for you.

```



## Overview of the Five Principles of Prompting

You’ll find references back to these principles throughout the rest of the book, to help you connect the dots to how they’re used in practice. The Five Principles of Prompting are as follows:

```

1. Give Direction: Describe the desired style in detail, or reference a relevant persona.

2. Specify Format: Define what rules to follow, and the required structure of the response.

3. Provide Examples: Insert a diverse set of test cases where the task was done correctly.

4. Evaluate Quality: Identify errors and rate responses, testing what drives performance.

5. Divide Labor: Split tasks into multiple steps, chained together for complex goals.

```


## Specify Format
AI models are universal translators. Not only does that mean translating from French to English, or Urdu to Klingon, but also between data structures like JSON to YAML, or natural language to Python code. These models are capable of returning a response in almost any format, so an important part of prompt engineering is finding ways to specify what format you want the response to be in.

```
Return a comma-separated list of product names in JSON for
"A pair of shoes that can fit any foot size.".
Return only JSON.

Examples:
[{
		"Product description": "A home milkshake maker.",
		"Product names": ["HomeShaker", "Fit Shaker",
		"QuickShake", "Shake Maker"]
	},
	{
		"Product description": "A watch that can tell
		accurate time in space.",
		"Product names": ["AstroTime", "SpaceGuard",
		"Orbit-Accurate", "EliptoTime"]}
]
```

Output
```
[
	{
		"Product description": "A pair of shoes that can \
		fit any foot size.",
		"Product names": ["FlexFit Footwear", "OneSize Step",
		"Adapt-a-Shoe", "Universal Walker"]
	}
]
```

## Evaluate Quality
There are a number of ways performance can be evaluated, and it depends largely on what tasks you’re hoping to accomplish. When a new AI model is released, the focus tends to be on how well the model did on evals (evaluations), a standardized set of questions with predefined answers or grading criteria that are used to test performance across models. Different models perform differently across different types of tasks, and there is no guarantee a prompt that worked previously will translate well to a new model. OpenAI has open-sourced its evals framework for benchmarking performance of LLMs, and encourages others to contribute additional eval templates.

<img width="590" alt="Screenshot 2024-05-01 at 11 24 11 AM" src="https://github.com/andysingal/prompt-docs/assets/20493493/842d2ef2-51a4-41d9-babb-0a17240911cd">

```py
### The first step is getting responses for multiple runs of each prompt, and storing it in a spreadsheet.

from dotenv import load_dotenv

load_dotenv()

```
```py
# Define two variants of the prompt to test zero-shot
# vs few-shot
prompt_A = """Product description: A pair of shoes that can
fit any foot size.
Seed words: adaptable, fit, omni-fit.
Product names:"""

prompt_B = """Product description: A home milkshake maker.
Seed words: fast, healthy, compact.
Product names: HomeShaker, Fit Shaker, QuickShake, Shake
Maker

Product description: A watch that can tell accurate time in
space.
Seed words: astronaut, space-hardened, eliptical orbit
Product names: AstroTime, SpaceGuard, Orbit-Accurate,
EliptoTime.

Product description: A pair of shoes that can fit any foot
size.
Seed words: adaptable, fit, omni-fit.
Product names:"""

test_prompts = [prompt_A, prompt_B]

import pandas as pd
from openai import OpenAI
import os

# Set your OpenAI key as an environment variable
# https://platform.openai.com/api-keys
client = OpenAI(
  api_key=os.environ['OPENAI_API_KEY'],  # Default
)

def get_response(prompt):
    response = client.chat.completions.create(
        model="gpt-3.5-turbo",
        messages=[
            {
                "role": "system",
                "content": "You are a helpful assistant."
            },
            {
                "role": "user",
                "content": prompt
            }
        ]
    )
    return response.choices[0].message.content

# Iterate through the prompts and get responses
responses = []
num_tests = 5

for idx, prompt in enumerate(test_prompts):
    # prompt number as a letter
    var_name = chr(ord('A') + idx)

    for i in range(num_tests):
        # Get a response from the model
        response = get_response(prompt)

        data = {
            "variant": var_name,
            "prompt": prompt,
            "response": response
            }
        responses.append(data)

# Convert responses into a dataframe
df = pd.DataFrame(responses)

# Save the dataframe as a CSV file
df.to_csv("responses.csv", index=False)

print(df)
```
Here we’re using the OpenAI API to generate model responses to a set of prompts and storing the results in a dataframe, which is saved to a CSV file. Here’s how it works:

Two prompt variants are defined, and each variant consists of a product description, seed words, and potential product names, but prompt_B provides two examples.

1. Import statements are called for the pandas library, openai library, and os library.

2. The get_response function takes a prompt as input and returns a response from the gpt-3.5-turbo model. The prompt is passed as a user message to the model, along with a system message to set the model’s behavior.

3. Two prompt variants are stored in the test_prompts list.

4. An empty list responses is created to store the generated responses, and the variable num_tests is set to 5.

5. A nested loop is used to generate responses. The outer loop iterates over each prompt, and the inner loop generates num_tests (5 in this case) number of responses per prompt.

6. The enumerate function is used to get the index and value of each prompt in test_prompts. This index is then converted to a corresponding uppercase letter (e.g., 0 becomes A, 1 becomes B) to be used as a variant name.

7. For each iteration, the get_response function is called with the current prompt to generate a response from the model.

8. A dictionary is created with the variant name, the prompt, and the model’s response, and this dictionary is appended to the responses list.

9. Once all responses have been generated, the responses list (which is now a list of dictionaries) is converted into a pandas dataframe.

This dataframe is then saved to a CSV file with the Pandas built-in to_csv function, naking the file responses.csv with index=False so as to not write row indices.

Finally, the dataframe is printed to the console.



Having these responses in a spreadsheet is already useful, because you can see right away even in the printed response that prompt_A (zero-shot) in the first five rows is giving us a numbered list, whereas prompt_B (few-shot) in the last five rows, tends to output the desired format of a comma separated in-line list.

```py
import ipywidgets as widgets
from IPython.display import display
import pandas as pd

# load the responses.csv file
df = pd.read_csv("responses.csv")

# Shuffle the dataframe
df = df.sample(frac=1).reset_index(drop=True)

# df is your dataframe and 'response' is the column with the
# text you want to test
response_index = 0
# add a new column to store feedback
df['feedback'] = pd.Series(dtype='str')

def on_button_clicked(b):
    global response_index
    #  convert thumbs up / down to 1 / 0
    user_feedback = 1 if b.description == "\U0001F44D" else 0

    # update the feedback column
    df.at[response_index, 'feedback'] = user_feedback

    response_index += 1
    if response_index < len(df):
        update_response()
    else:
        # save the feedback to a CSV file
        df.to_csv("results.csv", index=False)

        print("A/B testing completed. Here's the results:")
        # Calculate score and num rows for each variant
        summary_df = df.groupby('variant').agg(
            count=('feedback', 'count'),
            score=('feedback', 'mean')).reset_index()
        print(summary_df)

def update_response():
    new_response = df.iloc[response_index]['response']
    if pd.notna(new_response):
        new_response = "<p>" + new_response + "</p>"
    else:
        new_response = "<p>No response</p>"
    response.value = new_response
    count_label.value = f"Response: {response_index + 1}"
    count_label.value += f"/{len(df)}"

response = widgets.HTML()
count_label = widgets.Label()

update_response()

thumbs_up_button = widgets.Button(description='\U0001F44D')
thumbs_up_button.on_click(on_button_clicked)

thumbs_down_button = widgets.Button(
    description='\U0001F44E')
thumbs_down_button.on_click(on_button_clicked)

button_box = widgets.HBox([thumbs_down_button,
thumbs_up_button])

display(response, button_box, count_label)
```
<img width="625" alt="Screenshot 2024-05-01 at 11 29 37 AM" src="https://github.com/andysingal/prompt-docs/assets/20493493/8b60e65b-b032-4c3d-946f-8588b777b1bf">


## Conclusion
A simple rating system such as this one can be useful in judging prompt quality and encountering edge cases. Usually in under 10 test runs of a prompt you uncover a deviation, which you otherwise wouldn’t have caught until you started using it in production. The downside is that it can get tedious rating lots of responses manually, and your ratings might not represent the preferences of your intended audience. However, even small numbers of tests can reveal large differences between two prompting strategies, and reveal non-obvious issues before reaching production.

```
The thumbs up or other manually labelled indicators of quality doesn’t have to be the only judging criteria. Human evaluation is generally considered to be the most accurate form of feedback. However it can be tedious and costly to rate many samples manually. In many cases, as in math or classification use cases, it may be possible to establish ground truth (reference answers to test cases) in order to programmatically rate the results, allowing you to scale up considerably your testing and monitoring efforts. The following is not an exhaustive list, for there are many motivations for evaluating your prompt programmatically:

Cost: Prompts that use a lot of tokens, or only work with more expensive models, might be impractical for production use.

Latency: Equally the more tokens there are, or the larger the model required, the longer it takes to complete a task, which can harm user experience.

Calls: Many AI systems require multiple calls in a loop to complete a task, which can seriously slow down the process.

Performance: Implement some form of external feedback system, for example a physics engine or other model for predicting real-world results.

Classification: Determine how often a prompt correctly labels given text, using another AI model or rules-based labeling.

Reasoning: Work out which instances the AI fails to apply logical reasoning or gets the math wrong vs reference cases.

Hallucinations: See how frequently you encouner hallucinations, as measured by invention of new terms not included in the prompt’s context.

Safety: Flag any scenarios where the system might return unsafe or undesirable results using a safety filter or detection system.

Refusals: Find out how often the system incorrectly refuses to fulfill a reasonable user request by flagging known refusal language.

Adversarial: Make the prompt robust against known prompt injection attacks, that can get the model to run undesirable prompts instead of what you programmed.
```

Once you start rating which examples were good, you can more easily update the examples used in your prompt, as a way to continuously make your system smarter over time
<img width="629" alt="Screenshot 2024-05-01 at 11 32 31 AM" src="https://github.com/andysingal/prompt-docs/assets/20493493/ca0d3ffe-0d26-4cf8-b954-830e5833a9c7">




