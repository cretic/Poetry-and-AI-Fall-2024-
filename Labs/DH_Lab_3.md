# DH Lab 3: Word Analysis and Functions

[![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/cretic/Poetry-and-AI-Fall-2024-/blob/main/DH_Lab_3.ipynb)

## Exercise 1: Word Frequency Analysis

Let's try out some pre-written code. Can you run the cell below and identify what it does? Write a couple sentences about what you observe below the code cell.

```python
from collections import Counter
import re

# Sample text
text = """
The quick brown fox jumps over the lazy dog. The fox is quick and the dog is lazy.
"""

# List of words to compare
words_to_compare = ["quick", "fox", "dog", "cat"]

# Preprocess the text: convert to lowercase and remove punctuation
cleaned_text = re.sub(r'[^\w\s]', '', text.lower())

# Tokenize the text into words
words = cleaned_text.split()

# Count the frequency of each word in the text
word_counts = Counter(words)

# Display the frequency of each word in the words_to_compare list
for word in words_to_compare:
    print(f"'{word}': {word_counts[word]} occurrences")
```

Output:
```
'quick': 2 occurrences
'fox': 2 occurrences
'dog': 2 occurrences
'cat': 0 occurrences
```

**Your observations:**

Now, let's try to modify it ourselves. Copy and paste the code above into a new code cell and edit the sample text to a poem of your choosing. Make sure to edit the words to compare as well! What do you notice? Write a few sentences below.

## Exercise 2: Debug the Shared Words Function

We can also create a function that finds a set of shared words between two poems. There's an error in the function below. Can you fix it so it is able to be run? Try first without asking Gemini.

```python
import re

def find_shared_words(text1, text2):
    # Preprocess the texts: convert to lowercase and remove punctuation
    cleaned_text1 = re.sub(r'[^\w\s]', '', text1.lower())
    cleaned_text2 = re.sub(r'[^\w\s]', '', text2.lower())

    # Tokenize the texts into words
    words1 = set(cleaned_text1.split())
    words2 = set(cleaned_text2.split())

    # Find shared words between the two texts
    shared_words = words1.intersection(words2)

    return shared_words

# Sample texts
text1 = """
The quick brown fox jumps over the lazy dog. The fox is quick and smart.
"""
text2 = """
The lazy dog lies down in the sun. The dog is smart but not as quick as the fox.
"""

# Find shared words between the two texts
shared_words = find_shared_words(text1, text2)

# Display the shared words
print("Shared words between the two texts:")
print(Shared_Words)  # ERROR: This should be 'shared_words' not 'Shared_Words'
```

**The Error:** The variable name is inconsistent - `shared_words` is defined but `Shared_Words` is used in the print statement.

**Fixed version:**
```python
print(shared_words)
```

## Exercise 3: Synonym Generator

Time to step it up a little bit. We've built a synonym generator below for you to try. Run the code cell as is, and then make a change that allows the code to still be run. Can you explain what your change is? Does your change affect the result or no?

```python
import nltk
from nltk.corpus import wordnet

nltk.download('wordnet')

def find_synonyms(word):
  synonyms = []
  for syn in wordnet.synsets(word):
    for lemma in syn.lemmas():
      synonyms.append(lemma.name())
  return synonyms

# Example usage
word = "happy"
synonyms = find_synonyms(word)
print(f"Synonyms for '{word}': {synonyms}")
```

**Your modification and explanation:**

## Creative Challenge: Build Your Own Tool

Let's see if we can think outside of the box for our last step of this assignment. Your goal is to build a new tool that assembles data (from strings? from .txts? from .csv?), analyzes, or changes a poem in some way. You CAN use AI to help you if you want (just make sure to acknowledge it per course regulations).

Will you pull text from a github repository? Create your own? Will your program create a new kind of data object?

Try to import and use CMUDICT!

### Brainstorming

The first step is BRAINSTORMING! Use the text box below to think out your ideas.

**Your brainstorming notes:**

### Implementation

Now, try coding it.

**Example Solution: First and Last Word Extractor**

```python
# prompt: can you write a program that loops over each line in a poem and pulls out the first and last words

def extract_first_last_words(poem):
  """
  Extracts the first and last words from each line in a poem.

  Args:
    poem: A string containing the poem.

  Returns:
    A list of tuples, where each tuple contains the first and last word of a line.
  """

  first_last_words = []
  for line in poem.splitlines():
    words = line.split()
    if words:
      first_word = words[0]
      last_word = words[-1]
      first_last_words.append((first_word, last_word))
  return first_last_words


# Example usage:
poem = """
The quick brown fox
Jumps over the lazy dog
The fox is quick and the dog is lazy
"""

first_last_word_pairs = extract_first_last_words(poem)

for first_word, last_word in first_last_word_pairs:
  print(f"First word: {first_word}, Last word: {last_word}")
```

### Reflection

Once you have your code running*, write a short paragraph about what you did, how you did it, and how you feel it turned out.

*oh no, your code never ran correctly? talk about that instead!

**Your reflection:**