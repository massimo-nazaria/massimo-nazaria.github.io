---
layout: post
title: Find Rhymes in Text with Rhyme-Grep
description: A command-line tool to find rhyming words in a text by using Grep and the CMU pronouncing dictionary.
---

Let's see how to implement _(and have fun with!)_ a command-line tool to find rhyming words.

## Quick Tutorial

1) Get the `rhyme-grep/` folder and enter it:

```sh
$ git clone https://github.com/massimo-nazaria/rhyme-grep.git
$ cd rhyme-grep/
```

2) Make `rhymp.sh` executable:

```sh
$ chmod +x rhymp.sh
```

3) Find words that rhyme with "leaves" in [_Leaves of Grass_][1]{:target="_blank"} by Walt Whitman:

```sh
$ ./rhymp.sh "leaves" leaves-of-grass.txt
```

_**Output:**_

![]({{ '/assets/rhyme-grep/demo.svg' | relative_url }})

4) Let's print _only_ the rhyming words by using the `-o` argument, and at the same time remove possible duplicates with `sort -fu`:

```sh
$ cat leaves-of-grass.txt | ./rhymp.sh "leaves" -o | sort -fu
believes
heaves
perceives
receives
recitatives
sleeves
thieves
```

That's quite funny _(and useful)_!

## How it Works

Rhyme-Grep extracts the following data from the [CMU Pronouncing Dictionary][2]{:target="_blank"}:

1. The English pronunciation (namely a list of phonemes) of the input word; as well as
2. The list of dictionary words that have the same pronounciation phonemes as the input word starting from their primary accent.

Then it runs [Grep][3]{:target="_blank"} to search for the found rhyming words in the input text.


### ALGORITHM OVERVIEW

Let's see how to search for words that rhyme with _leaves_ in `leaves-of-grass.txt`.

#### Step 1: Input word pronunciation

Extract from the CMU dictionary the pronounciation of the word _leaves_, which is denoted by the list of phonemes `L IY1 V Z`.

_Note the primary accent falls on the phoneme `IY`, which is marked by `1` in the list._

#### Step 2: List of rhyming dictionary words

Extract from the dictionary the list of words that rhyme with _leaves_, namely the words whose pronunciation ends with `IY1 V Z`.

#### Step 3: Rhyming words from the input text

Search for the rhyming words within `leaves-of-grass.txt`.

Let's say the rhyming word are:

* _eves_,
* _perceives_.

Run Grep as follows:

```sh
$ cat leaves-of-grass.txt | grep -E -wi --color "eaves|perceives"
```

## Implementation

For additional info, please [_get the code from GitHub_][4]{:target="_blank"} and have fun playing with it!

Rhyme-Grep was initially inspired by [_Semantic Grep_][5]{:target="_blank"}: a [_word2vec_][6]{:target="_blank"}-based tool that searches for words with similar meanings to a given word.

[1]: https://gutenberg.org/ebooks/1322
[2]: https://github.com/cmusphinx/cmudict
[3]: https://www.gnu.org/software/grep/
[4]: https://github.com/massimo-nazaria/rhyme-grep
[5]: https://github.com/arunsupe/semantic-grep
[6]: https://code.google.com/archive/p/word2vec/
