# DH Lab 2: Code Tinkering (AI and Poetry)

[![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/cretic/Poetry-and-AI-Fall-2024-/blob/main/DH_Lab_2_Code_Tinkering_(AI_and_Poetry).ipynb)

Congrats on making it to the second DH lab! In this lab, we will be exploring "tinkering" with code. This means we will make some of our own changes and try to explain what the code is doing. Please reach out to Madeline - madeline.gupta@yale.edu if you need help.

The first thing we will do is read in the poem we are going to use for this lab. Reminder: to run the code, click the play button by the [] sign.

```python
# Here's the poem, stored as a string
poem = "The cow is of the bovine ilk;\nOne end is moo, the other, milk\nOgden Nash"
```

## Exercise 1

Run the code below. What do you think it does? Add your answer to the comments! (hint: comments begin with a #)

```python
# What does this code do?
# Your answer here
print(poem)
```

Output:
```
The cow is of the bovine ilk;
One end is moo, the other, milk
Ogden Nash
```

## Exercise 2

Let's step it up a little. Can you guess what this code does? Add your answer to the comments!

```python
# What does this code do?
# Your answer here
new_animal = "llama"
new_poem = poem.replace("cow", new_animal)
print(new_poem)
```

Output:
```
The llama is of the bovine ilk;
One end is moo, the other, milk
Ogden Nash
```

## Exercise 3

Now it's your turn! Can you change the animal again? Try replacing it with your favorite animal (change dog to something else).

```python
my_favorite_animal = "dog"
my_new_poem = poem.replace("cow", my_favorite_animal)
print(my_new_poem)
```

Output:
```
The dog is of the bovine ilk;
One end is moo, the other, milk
Ogden Nash
```

## Exercise 4

Now that you have the hang of it, let's try some more fun functions.
(hint: a function is a piece of code that performs a specific function, and can do it over and over again.)
Add explanations to the following code blocks!

### Length Function

```python
# What does this code do?
# Your answer here
length_of_poem = len(poem)
print(length_of_poem)
```

Output: `72`

### Upper Case Function

```python
# What does this code do?
# Your answer here
upper_case_poem = poem.upper()
print(upper_case_poem)
```

Output:
```
THE COW IS OF THE BOVINE ILK;
ONE END IS MOO, THE OTHER, MILK
OGDEN NASH
```

### Split by Lines

```python
# What does this code do?
# Your answer here
poem_lines = poem.split('\n')
print(poem_lines)
```

Output: `['The cow is of the bovine ilk;', 'One end is moo, the other, milk', 'Ogden Nash']`

### Word Count

```python
# What does this code do?
# Your answer here
poem_words = poem.split()
number_of_words = len(poem_words)
print(number_of_words)
```

Output: `16`

### Find Word Position

```python
# What does this code do?
# Your answer here
word_to_find = "moo"
word_position = poem.find(word_to_find)
print(word_position)
```

Output: `41`

### Character List

```python
# What does this code do?
# Your answer here
characters = list(poem)
print(characters)
```

Output: `['T', 'h', 'e', ' ', 'c', 'o', 'w', ' ', 'i', 's', ' ', 'o', 'f', ' ', 't', 'h', 'e', ' ', 'b', 'o', 'v', 'i', 'n', 'e', ' ', 'i', 'l', 'k', ';', '\n', 'O', 'n', 'e', ' ', 'e', 'n', 'd', ' ', 'i', 's', ' ', 'm', 'o', 'o', ',', ' ', 't', 'h', 'e', ' ', 'o', 't', 'h', 'e', 'r', ',', ' ', 'm', 'i', 'l', 'k', '\n', 'O', 'g', 'd', 'e', 'n', ' ', 'N', 'a', 's', 'h']`

### Reverse String

```python
# What does this code do?
# Your answer here
reversed_poem = poem[::-1]
print(reversed_poem)
```

Output:
```
hsaN nedgO
klim ,rehto eht ,oom si dne enO
;kli enivob eht fo si woc ehT
```

### Check if Word Exists

```python
# What does this code do?
# Your answer here
word_to_check = "instagram"
contains_word = word_to_check in poem
print(contains_word)

word_to_check = "bovine"
contains_word = word_to_check in poem
print(contains_word)
```

Output:
```
False
True
```

## Challenge

Great job! Before we finish, let's see if we can apply what we learned. Can you copy the code we have used so far to choose and input your own poem, reverse it, and return how many letters and words are in it?

```python
#try out the challenge here
```

## Reflection

Can you imagine some useful actions you might want to perform for a poem? Word counting, for instance, or creating an index of all words. What else? Feel free to say how you might do this in python (or even ask gemini to show you how!)

### Example: Extract Author

```python
#For example: Read the last line of "poem" and assign it to the variable "author"

author = poem.split('\n')[-1]
print('Author:' + author)
```

Output: `Author:Ogden Nash`

**Write your response here:**

---

You're all done!