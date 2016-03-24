Markov Chain Module
===================

This is a really simple Markov chain module for bodies of text.  It offers a
class that can train on bodies of text and then generate text based on its
model.  The command line interface allows for simple creation, training, and
generation using text files and Pickle.

Command Line Interface
----------------------

There are two flags for specifying markov chains:

* `-i` specifies the input chain (Pickle file).
* `-o` specifies the output (Pickled too).

Currently, these cannot be the same file.  If no input is specified, a new one
is created.  If no output is specified, the resulting Markov chain is lost
(which is fine if it hasn't been modified).  When you're creating a new one,
make sure to specify `-n`, the depth of the chain (i.e. how many words back the
next word is based on).

There are two operations that can be performed: train (`-T`) and generate
(`-G`).  The training operation takes a text file and trains on it.  You'll
want to make sure to output the chain to a new file afterwards.  The generation
operation just spits out a "sentence" onto stdout.

Examples
--------

Create a new chain whose states consist of word pairs, train on "training.txt",
and save as "markov1.pickle".

    ./markov.py -T training.txt -o markov1.pickle -n 2

Open "markov1.pickle", train on "more_training.txt", and save to
"markov2.pickle".

    ./markov.py -i markov1.pickle -T more_training.txt -o markov2.pickle

Open "markov2.pickle", generate a sentence.

    ./markov.py -i markov2.pickle -G

Recommendation
--------------

If you're a fan of a particular popular musician (say, Taylor Swift), you could
head over to my [tswift](https://github.com/brenns10/tswift) module, use it to
download all your artist's song lyrics, and then train a Markov chain on that.
It's quite interesting to read text generated from lyrics because if you know
enough of them, you can start to understand where the generated text came from.
PS: if you just wanted to do Taylor Swift lyrics, just download the `taylor.txt`
file from [pyswizzle](https://github.com/brenns10/pyswizzle).  Wow, I have a lot
of Taylor Swift related code.  That's probably weird.  Oh well.
