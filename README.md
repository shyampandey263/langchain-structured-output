# langchain-structured-output
# Product Review Analyzer

Extracts structured data from a free-text product review using LangChain's structured output with OpenAI.

## What it does
Given a product review, the notebook returns a Python dictionary with:
- `key_themes`: the main topics discussed
- `summary`: a short summary
- `sentiment`: `pos`, `neg` or `neutral`
- `pros` and `cons`: lists of points
- `name`: the reviewer's name, if present

## How it works
1. A `TypedDict` (typed dictionary) defines the output schema, and field descriptions guide the model.
2. `model.with_structured_output(Review)` forces the model's reply into that shape.
3. `invoke()` runs the review through the model and returns the dictionary.

## Example
Input:
> I bought the Redmi Note 13 last month. The AMOLED display is bright and smooth, and the battery easily lasts a full day. The camera is good in daylight but weak at night. It heats up while gaming, and the pre-installed apps are annoying. For the price, it is great value.

Output (shortened):
```python
{
  'key_themes': ['AMOLED display', 'battery life', 'camera', 'gaming performance', 'pre-installed apps', 'value for money'],
  'sentiment': 'pos',
  'pros': ['Bright and smooth AMOLED display', 'Long-lasting battery', ...],
  'cons': ['Weak camera in low light', 'Heats up while gaming', ...],
  'name': 'Shyam'
}
```

## How to run
1. Open `review_analyzer.ipynb` in Google Colab.
2. Run the cells from top to bottom.
3. Paste your own OpenAI API key when asked. The key is never stored in the notebook.

## Tech used
Python, LangChain, OpenAI (`gpt-4o-mini`), Google Colab
