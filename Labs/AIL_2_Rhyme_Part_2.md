# AI Lab 2: Rhyme (Part 2)

**Due:** Tuesday, 10/8 by start of class. Submit via Google Classroom

In class we have distinguished between two kinds of knowledge LLMs have about poetry: generative (writing poetry) and metapoetic (analyzing it). In this lab we will play with AI's ability to both generate and analyze rhyme.

When AI writes rhyming poems, it is telling us something about the history of poetry and rhyme, and about how words relate to each other. In DHL3 we saw basic vector representations of words. Some rhyme words will be "closer" to some rhymes than other in that vector space. This is not, of course, how poets thought about rhyme.

As for metapoetic knowledge: when asked to analyze rhymes, an LLM may draw on the words themselves, ways people have talked about those words, examples of literary criticism of rhyme, among other resources.

## First Part: Generation

Using your knowledge of prompt engineering, design a sequence of three prompts of ascending complexity to test your chosen LLMs capacity (or predilection) for rhyme. Try different LLMs if you'd like! Some LLMs (google's AI studio) allow you to give the system instructions. Others allow longer inputs. After each prompt, note what you see (2-3 sentences is great)

### Example: (Gemini 1.5 Pro)

**Prompt 1:**

Not a single LLM took the bait of "canuck". None of these words have anything to do with the phrases they end, much less Canada. Moose cluck?

**Prompt 2:**

I notice that gemini manages the disagreement task only when I give it an easy word to rhyme. "interesting" and "danger" break it. It seems like limited rhyme options – thus extreme unlikeliness at the end of the phrase -- pull the LLM too far from its ability to sequence likely words.

**Prompt 3:**

Naming different poets doesn't do much, but directing GPTs away from their vaguely happy tone produces much better rhymes. I suspect that a large-scale analysis of lots of LLM poetry would show a ton of "breeze / trees / high / sky / blow / flow" etc and not many morphologically divergent examples like "bland / unmanned." I wonder why the negative tone helps?

### Your Experiments:

**Prompt 1:**

**Your observation:**

**Prompt 2:**

**Your observation:**

**Prompt 3:**

**Your observation:**

## Second Part: Analysis

- Go back to PE2 and the lines you studied there. Plug them into a GPT and have whatever sort of conversation or set of prompts you think will produce literary analysis.
- Copy-paste the most interesting results (2 or 3, or one longer conversation), followed by a few sentences of your own commentary. Think about:
  - How AI analysis compares from your own
  - What kinds of claims, with what evidence, does AI make? Notice its habits or ticks.

**Your AI analysis results:**

**Your commentary:**

## Choose One:

### Option A: Modified Lines

Make some substantial change to the lines, so that the rhyme is very different, maybe even not fully rhyming. How does the analysis change?

**Your modified lines:**

**How the analysis changed:**

### Option B: Song Lyrics

Return to song lyrics (either the ones you chose for PE2, or choose new ones). Plug these into ChatGPT and make it clear that they are song lyrics, then ask for analysis. You might specify "analyze the rhyme" or not. Does the change of genre from poetry to song change the kind of analysis?

**Your song lyrics:**

**AI analysis:**

**Your reflection on genre differences:**