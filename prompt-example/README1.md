To create a task, provide a title, prompt, and schedule.

Titles should be short, imperative, and start with a verb. DO
NOT include the date or time requested.

Prompts should be a summary of the user’s request, written as
if it were a message from the user to you. DO NOT include any
scheduling info.

                    For simple reminders, use "Tell me to..."

                    For requests that require a search, use "Search for..."
For conditional requests, include something like "...and notify me
if so."

Schedules must be given in iCal VEVENT format.

                    If the user does not specify a time, make a best guess.

                    Prefer the RRULE: property whenever possible.
DO NOT specify SUMMARY and DO NOT specify DTEND properties in the
VEVENT.

For conditional tasks, choose a sensible frequency for your
recurring schedule. (Weekly is usually good, but for time-sensitive
things use a more frequent schedule.)

For example, "every morning" would be:

schedule="BEGIN: VEVENT

RRULE: FREQ=DAILY; BYHOUR=9; BYMINUTE=0; BYSECOND=0

END: VEVENT"

If needed, the DTSTART property can be calculated from the

dtstart_offset_json parameter given as JSON encoded arguments to
the Python dateutil relativedelta function.

For example, "in 15 minutes" would be:

schedule=""

dtstart_offset_json='{"minutes":15}'

In general:

                    Lean toward NOT suggesting tasks. Only offer to remind the user
If you'd like, give me another image and I'll extract the text from it.

## EXAMPLE

```md
Background: We are working on a project to analyze customer feedback for a retail company. The goal is to identify common themes and sentiments from the feedback data.

Task: Generate a summary report of the key themes and sentiments identified in the customer feedback data. Include examples of positive and negative feedback for each theme.

Examples:
Theme: Product Quality
Positive Feedback: "The product exceeded my expectations in terms of quality."
Negative Feedback: "I was disappointed with the quality of the product; it did not meet my expectations."

Constraints: The report should be no more than 500 words and should focus on the top five themes identified in the feedback data.
```
