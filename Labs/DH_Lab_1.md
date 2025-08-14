# DH Lab 1: Introduction to Colab and Python (Poetry and AI)

## Getting Started

Welcome to our first DH lab! This lab will set up skills for you to be able to read in a text file to colab, understand some basic coding ideas, and get ready for the rest of our labs. Feel free to reach out to Madeline - madeline.gupta@yale.edu if you need help.

Before proceeding with the notebook below, please make sure you click "File" then click "Save a copy in drive". Doing so will make sure your work gets saved in your personal Google Drive account!

To make sure you've successfully created a copy of this notebook, please click "File" in the upper navigation bar, then click "Save". Once you see a little notification that your work has been saved successfully, you're ready to proceed!

## Collecting Resources

This notebook makes use of a files that is not present in the current notebook environment. To load those resources, please hover your mouse between the [ ] braces in the cell below and click the play button that appears. Once you've done that, we're ready to start the notebook! Can you guess what we may have imported here?

```bash
!wget https://raw.githubusercontent.com/YaleDHLab/lab-workshops/master/first-steps-with-python/jabberwocky.txt
```

### Colab/Python Tips

```python
# Some quick Colab/Python tips:
#
# lines that start with the '#' pound sign (or hashtag symbol) are comments, and are not run by python.
# Adding a cell below your current cell: Command+m and then 'b' (Windows: Control+m and then 'b')
# Adding a cell above your current cell: Command+m and then 'a' (Windows: Control+m and then 'a')
#
# Shift-Return 'excecutes' a cell, in the sense of running it. So does hitting the Play arrow inside the circle on the far left.
# Return without Shift just starts a new line.
```

## Getting Started

### Variables

Variables are the core building blocks of computer programming. A variable is a sequence of characters to which we assign a value or meaning using the = sign. Let's look at an example:

```python
my_jabber = 'slithy'
```

Here `my_jabber` is the variable, and `'slithy'` is the value assigned to that variable. In general in Python, the thing on the left hand side of the equals sign is the variable, and the thing on the right hand side is that variable's value.

When creating a variable, keep in mind that **variable names**:
- can only include letters, numbers, and underscores
- must start with a letter or underscore (variables that start with underscores have a special meaning, so for now, we'll start our all of our variables with letters)
- are case sensitive.

Given the above rules, try to anticipate which cells below will return an error message:

```python
jabberwocky_question = 'Hast thou slain the Jabberwock?'
```

```python
_jabberwocky_question = 'Who are you?'
```

```python
jabberwocky_Question1 = 'Who are you?'
```

```python
1jabberwocky_question = 'Who are you?'
```

The last example will produce a SyntaxError because variable names cannot start with a number.

<details>
  <summary><h5>Solution</h5></summary>

The final variable (`1jabberwocky_question`) is the problematic variable name, because it violates the second rule above (which states variables must start with a letter or an underscore).

To verify this for yourself, try instantiating each variable above and you should see that only the last variable throws an error!
</details>

Variables can be reassigned in Python. We might assign a value to a variable, then later assign a different value to that variable:

```python
my_jabberwocky = 'slithy'
my_jabberwocky = 'toves'
```

Here `my_jabberwocky` is given an initial value `'slithy'`, but is then given a new value `'toves'`.

### Printing

To check the value assigned to a variable at any given moment, you can use the `print()` function:

```python
my_jabberwocky = 'slithy'
print(my_jabberwocky)
```
Output: `slithy`

The `print()` command is a type of function. We can recognize `print()` as a function because it has parentheses after the name. In general, **functions** are little pieces of code that take **arguments** (the text enclosed in parentheses) as input and do something with those arguments. The `print()` function, for example, takes as its argument a variable like `my_jabberwocky`, then displays the value assigned to that variable. We will explore functions in greater depth below. For now, we just want to note that `print()` is a function, which we can recognize by the presence of parentheses after the function's variable name.

See if you can use the `print()` function to tell what value is assigned to the following variable:

```python
# see if you can display the value assigned to `my_motto` below
my_motto = "Beware the Jabberwock, my son!" + ", " + "The jaws that bite, the claws that catch!"

# add your code here
```

<details>
  <summary><h5>Solution</h5></summary>
  We can use the print function on the `my_motto` string as follows:

  ```
  print(my_motto)
  ```

  If you had trouble with the exercise above, try copying and pasting the code snippet in this solution block into a new code cell to see what the output looks like!
</details>

### Introspection

Just as we can use the `print()` function to see the value assigned to a variable, we can use the `dir()` function to see the kinds of things we can do with a variable. Brace yourself though, the `dir()` command displays lots of options!

```python
title = 'Jabberwocky'
dir(title)
```

Running the `dir()` function returns a list of methods that are defined on the provided variable. In the example above, we can see that `title` has 50 or so methods defined. **Methods** are similar to functions, except they're tied to the variable (or object) you're working with. You can call a method using dot notation. Let's look at a few examples:

```python
title.upper()
```
Output: `'JABBERWOCKY'`

```python
title.lower()
```
Output: `'jabberwocky'`

We can see that the `upper()` method lets us uppercase our title, and the `lower()` method lets us lowercase our title. We will use more methods in just a moment. For now, we just want to remember that the `dir()` command tells us which methods can be called on variables.

See if you can use the `dir()` command to identify the methods available on the variable below:

```python
# use the `dir()` command below to identify the methods available on the variable below
song = '''
  One, two! One, two! And through and through
      The vorpal blade went snicker-snack!
'''

#add your code here
```

<details>
  <summary><h5>Solution</h5></summary>
  We can run the `dir()` command on the `song` variable as follows:

  ```
  dir(song)
  ```

  The output of that command shows all of the methods one can call on `song`.
</details>

### Data Type: Strings

All of the variables we have seen so far have been examples of "strings", another way of referring to text data. We know these variables are strings because their values are wrapped in quotation marks.

Can you explain the error message we get if we try to assign text data as a value without using quotation marks?

```python
# the code below will result in an error
main_character = Jabberwocky

# fix the above code here
```

<details>
  <summary><h5>Solution</h5></summary>
  The problem with the line above is that Python interprets Jabberwocky as a variable, as it doesn't have quotation marks around it. We can fix that by placing quotes around it:

  ```
  main_character = "Jabberwocky"
  ```

  or

  ```
  main_character = 'Jabberwocky'
  ```

(The type of quotation mark we use does not matter--both are treated identically.)
</details>

### Reading Files

Many Python programs need to read files to load data you have collected into memory. Let's practice reading a file:

```python
my_file = open('/Users/maddiegupta/Desktop/sample1.txt').read()
```

You'll notice that the line above starts with `open()`. `open()` is an example of a **built-in** function, which means it comes predefined in all Python files. There are a small handful of these built-in functions, including the `print()` and `dir()` functions we saw above. For now we should note that `open()` returns a "file handler" that contains a `read()` method. Calling that `read()` method lets us read the text content of a file into memory.

You'll also notice a list of your variables can be seen if you click the {x} tab in the far left column. You can also see the file jabberwocky.txt if you click on the folder icon. Note that files stored here in colab are NOT saved outside of this specific runtime! There are other ways to keep files permanently available, if you wish.

## Conclusion

Congrats on finishing your first DH lab!

*This lab is adapted from "YDATA: Humanities Data Mining Course Materials" by Peter Leonard, used under CC BY 3.0.*