# Planning Notes

Use this file for the short planning and verification notes in the lesson.

## Step 1: RAG API goal and output contract

- User or role:
Employees asking facilities operations questions.

- Business problem:
Employees need quick answers from approved facility information rather than general AI guesses.

- User question:
"Can I get building access after 7 PM?"

- Searchable content:
Facilities documents about building access, badges, visitors, room setup, maintenance, and equipment repair.

- Endpoint route:
POST /api/ask

- Expected successful response:
A JSON object with an answer and a sources list.

- Fallback behavior:
If the retrieved context is missing or weak, return a safe answer stating that there are not enough approved facilities in the context.

- Verification goal:
The answer should use the retrieved facilities context and include traceable source metadata.

## Step 12: Verification note

Functional output:
output should be a JSON object containing the answer and sources

Input validation:
Input should be checked for empty strings or vague questions

Retrieval quality:
top k results should be checked for relevance

Prompt grounding:
relevant retrieved context should be added to prompt along with instructions to build answer
from apporved documents only

Source traceability:
prompt instructions should dictate that context document sources be listed below the answer

Fallback behavior:
If there is not enough context to support the question, the model should return a response
stating that there is not enough context to support the question and to reformat the question
and try again, rather than invent an answer.

## Step 13: Reflection

What does Chroma own in this workflow?


What does the prompt builder own?


What does the Flask route coordinate?


Why does the API response include sources?


What would break if the route sent the user question directly to the model?
