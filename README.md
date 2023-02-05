# lexial_order

We want to train a transformer model to sort a list of words alphabetically .
Example
Input:
[”glue”, “cat”, “avocado”, “matrix”]
Output:
[”avocado”, “cat”, “glue”, “matrix”]

We will consider several approaches to solve this problem:

## Train a transformer model from scratch** to build new word embeddings 

As we don’t need positional information, because the output would always be the same no matter which combination the list of words come
 [a, b ,c] or [b,c, a] or [c, b, a] would be the same results [a, b, c] 
 
**Metric**:

BLEU score:
Which makes sure the output words are the correct ones, and in the right order.



##  Fine tune a language model (like T5)  to solve this problem as sequence to sequence problem

This solution is not optimal, as the word embeddings of T5 contains semantic knowledge that is unnecessary for this task.

Metric:

BLEU score:

Which makes sure the output words are the correct ones, and in the right order.


## Fine tune or train from scratch to classify word location** into 32 locations (classes)

This approach is simpler as we have more control on the output than the text generation.

**Metric:**

F1 Score

as it’s a classification problem and we need to insure no

## Input:

The model expects a list of words of length between 2 and 32, as we set the max length to 32, and we use a padding to make all input have the same size.


### Objective:

Cross-entropy loss measures the dissimilarity between the unsorted list and the sorted list, by minimizing the cross-entropy loss, the model learns to generate lists  that are more similar to the sorted ones.

###  Building dataset: 

To mix hard and easy samples in the training set, we build part of the data to contain consecutive words in the corpus while the other part is randomly selected words from the corpus.
