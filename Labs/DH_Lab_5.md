# DH Lab 5: Data Formatting and Display

[![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/cretic/Poetry-and-AI-Fall-2024-/blob/main/DH_Lab_5.ipynb)

One of the challenges in the final project is finding a way to output, store, and ultimately display your data in a clean, easy to read format. DH Lab 5 will give you an opportunity to think about how you want to tackle that with your project.

First, here's a demo on a few different formatting options using sonnet 129. In each, let's say we want to display the line, track its enjambments, and record a few other metrics about the line.

## Sample Text: Shakespeare's Sonnet 129

```python
sonnet_129 = """The expense of spirit in a waste of shame
Is lust in action; and till action, lust
Is perjured, murderous, bloody, full of blame,
Savage, extreme, rude, cruel, not to trust,
Enjoyed no sooner but despisèd straight,
Past reason hunted; and, no sooner had
Past reason hated as a swallowed bait
On purpose laid to make the taker mad;
Mad in pursuit and in possession so,
Had, having, and in quest to have, extreme;
A bliss in proof and proved, a very woe;
Before, a joy proposed; behind, a dream.
    All this the world well knows; yet none knows well
    To shun the heaven that leads men to this hell."""

# note the triple quotes, these allow line breaks to be preserved in the sonnet
```

## Method 1: Basic Dictionary Output

```python
import spacy

# Load SpaCy English model
nlp = spacy.load("en_core_web_sm")

# Split text into lines
lines = sonnet_129.split("\n")

# Initialize results
results = []

# Process each line
for i in range(len(lines) - 1):
    line = lines[i].strip()
    next_line = lines[i + 1].strip()

    # Parse lines with SpaCy
    doc = nlp(line)
    next_doc = nlp(next_line)

    # Check for punctuation at the end of the line
    enjambed = "no" if line[-1] in ".;!?," else "yes"

    # Check for substantial enjambment (based on syntactic dependencies)
    last_token = doc[-1]
    substantial = "yes" if last_token.dep_ in ["cc", "prep", "conj", "det"] else "no"

    # Append results
    results.append({"Line": line, "Enjambed": enjambed, "Substantial Enjambment": substantial})

# Print results
for result in results:
    print(result)
```

## Method 2: Using Prosodic for Metrical Analysis

```python
## run this cell to install prosodic, then restart runtime as requested

!apt-get install espeak libespeak1 libespeak-dev
!pip install -U prosodic

import prosodic
prosodic.logger.setLevel('ERROR')

# these are the meter parameters.
# if you want to play around with different rules and values, do that and make sure to change the inputs and rerun

constraints={
    'w_peak':3.0,
    'w_stress':1.0,
    's_unstress':1.0,
    'unres_across':1.0,
    'unres_within':1.0,
    'pentameter':20.0,
}
meter = prosodic.Meter(
    constraints=constraints,
    resolve_optionality=True,
    max_s=1,
    max_w=2,
)

linesProsodic = prosodic.Text(sonnet_129)
parse = linesProsodic.parse()
df = parse.stats()
# we are storing these results in a data frame so we can do more with them
```

## Method 3: Pandas DataFrame

This is a lot of information. Let's clean it up a bit. We can extract just the parse score and add our enjambment information.

```python
import pandas as pd

# Extract the parse score column
df_parse_scores = df[['parse_score']]

# Prepare data for the new DataFrame
data = []

for i in range(len(lines) - 1):
    line = lines[i].strip()

    # Parse lines with SpaCy
    doc = nlp(line)

    # Check for punctuation at the end of the line
    enjambed = "no" if line[-1] in ".;!?," else "yes"

    # Check for substantial enjambment (based on syntactic dependencies)
    last_token = doc[-1]
    hard_enjambment = "yes" if last_token.dep_ in ["cc", "prep", "conj", "det"] else "no"

    # Add the results to the data list
    data.append({
        "The line": line,
        "Parse score": df_parse_scores.iloc[i]["parse_score"],
        "Enjambed?": enjambed,
        "Hard enjambment?": hard_enjambment
    })

# Create a new DataFrame
df_results = pd.DataFrame(data)

# Display the DataFrame
print(df_results)
```

## Method 4: Interactive Tables with Plotly

Want to make your table more dynamic? Try Plotly, shown below!

```python
import plotly.graph_objects as go

# Extract the parse score column
df_parse_scores = df[['parse_score']]

# Prepare data for the new DataFrame
data = []

for i in range(len(lines) - 1):
    line = lines[i].strip()

    # Parse lines with SpaCy
    doc = nlp(line)

    # Check for punctuation at the end of the line
    enjambed = "no" if line[-1] in ".;!?," else "yes"

    # Check for substantial enjambment (based on syntactic dependencies)
    last_token = doc[-1]
    hard_enjambment = "yes" if last_token.dep_ in ["cc", "prep", "conj", "det"] else "no"

    # Add the results to the data list
    data.append({
        "The line": line,
        "Parse score": df_parse_scores.iloc[i]["parse_score"],
        "Enjambed?": enjambed,
        "Hard enjambment?": hard_enjambment
    })

# Create a new DataFrame
df_results = pd.DataFrame(data)

# Create an interactive table using Plotly
fig = go.Figure(data=[
    go.Table(
        header=dict(
            values=["<b>The Line</b>", "<b>Parse Score</b>", "<b>Enjambed?</b>", "<b>Hard Enjambment?</b>"],
            fill_color="lightblue",
            align="left"
        ),
        cells=dict(
            values=[
                df_results["The line"],
                df_results["Parse score"],
                df_results["Enjambed?"],
                df_results["Hard enjambment?"]
            ],
            fill_color="white",
            align="left"
        )
    )
])

# Show the interactive table
fig.show()
```

These are just a few kinds of tables and calculations you can show. When you organize your data into a data frame, there's a lot more functions you can run.

## Your Turn

Your turn! Think about the texts and data objects you need in your final project. In the example above, the top level object was the sonnet, and each line was a row. Columns tracked enjambment and metrical complexity. What are your rows and columns? You will need to display them. Do your best to create a dataframe (or another data structure if more useful!) and display it. If you struggle to get code running, flag that for future work.

```python
## your code here
```

## Final Reflection

Final Reflection: What is the primary challenge you are facing when it comes to assembling and/or displaying data? Do you know what your data looks like but need help formatting or analyzing it? Or are you unsure what the data should look like? Sometimes there is no "right" or even "best" structure, but it is important to notice when that is the case.

Add your reflection in the text box below.

**YOUR REFLECTION:**