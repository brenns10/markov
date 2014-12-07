Markov Chain Module
===================

This is a really simple Markov chain module for bodies of text.  It offers a
class that can train on bodies of text and then generate text based on its
model.  The command line interface allows for simple creation, training, and
generation using text files and Pickle.

Command Line Interface
----------------------

There are two flags for specifying markov chains:

* "-i" specifies the input chain (Pickle file).
* "-o" specifies the output (Pickled too).

Currently, these cannot be the same file.  If no input is specified, a new, one
is created.  If no output is specified, the resulting Markov chain is lost
(which is fine if it hasn't been modified).

There are two operations that can be performed: train ("-T") and generate
("-G").  The training operation takes a text file and trains on it.  You'll
want to make sure to output the chain to a new file afterwards.  The generation
operation just spits out words onto stdout.  You can specify how many words to
generate using "-w".

Examples
--------

Create a new chain, train on "training.txt", and save as "markov1.pickle".

    ./markov.py -T training.txt -o markov1.pickle

Open "markov1.pickle", train on "more_training.txt", and save to
"markov2.pickle".

    ./markov.py -i markov1.pickle -T more_training.txt -o markov2.pickle

Open "markov2.pickle", generate 500 words.

    ./markov.py -i markov2.pickle -G -w 500
