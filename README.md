# DS4300 - Fall 2024 - Assignment #1 - Applied Component

This is the template repository for Assignment #1. 

## Important Notes:

- [ ] EC Due Date:
- [ ] Regular Due Date:
- [ ] What to submit where?
- [ ] You may do this assignment in pairs (not required).  The written portion must be done individually. 

## Overview

Database systems use indexes to speed up retrieval operations.  In this assignment, you will implement several different in-memory indexing data structures, build indexes with them for a large corpus of documents, and explore their relative performance with respect to searches. 

### DataSet

**Link to dataset will be pinned in the class Slack Channel.**

The input corpus is based on the [US Financial News Articles](https://www.kaggle.com/datasets/jeet2016/us-financial-news-articles) Kaggle Dataset. Each news article is in a separate JSON file containing metadata about the article as well as the full text.  The full text has been pre-processed to remove stop words, any tokens composed of only digits and decimal points, and lemmatized. 

## Steps in the Final Deliverable

You may do the following simultaneously for all 4 data structures OR you may perform the steps below individually for each data structure (my suggestion).

1. Read in all the JSON files and extract the `preprocessed_text` element. It will contain a list of words/tokens to be indexed.  Insert each word from `preprocessed_text` into the current data structure as the key and using the filename as the value. 
1. Get a list of keys (tokens) from the index. Shuffle the resulting list. 
1. Using the list of randomized keys, perform a set of searches of increasing size, gathering execution time information for each data set. Start with ~100K and increase the size until the execution times of the set of searches against the 4 different data structures becomes significant.  

I have included a decorator in `indexer.util.timer` that tracks the execution time in nanoseconds and milliseconds.  You are free to track performance data in some other Pythonic way if you'd like.  

At the end of the experiments, you should have a table of data.  One dimension of the table will represent the 4 data structures, and the other dimension will represent the various dataset sizes for searches that you performed. 


## Implementation Details

You'll use the following data structures for this project:
- Binary Search Tree (already implemented for you)
- AVL Tree (started for you)
- Hash Table (main functions stubbed out for you)
- Unsorted List (not started)

Each of these should inherit from a common interface of functionality in `indexer.abstract_index.AbstractIndex`. Those for which I've provided a full or partial implementation already do. 

Each data structure should conceptually manage an inverted index for the corpus. In this case, the inverted index will map individual words (after they've been preprocessed) to a list of documents in which that word appears.

Your implementation should run with Python 3.11.  To create a new conda environment with python 3.11, run the following: 

```bash
conda create -n <new_env_name> python=3.11
```

Subsequently, install additional packages listed in the requirements.txt file with:
```bash
pip install -r requirements.txt
```

If you add any packages to the base install, be sure to add them to the `requirements.txt` so the TAs will be able to run your programs easily. 


## Deliverables 

- [ ] Full Python Implementation of the data structures and experiments. 
  - [ ] The code I am providing includes type hints to help you comprehend the code more quickly.  The code you add is not required to use type hints, although I recommend it for clarity. 
- [ ] Raw data collected in your experiments.  The raw data should be in one or more csv files and added to the `timing_data` folder of your repository.
- [ ] An analysis report in PDF saved in the `report` folder of your repository.
  - [ ] The report should be 1 - 2 pages (if any graphs or figures were removed), single spaced, 12 pt font size. 
  - [ ] It should include a brief synopsis of the project in your own words, point out any unique features of your implementation (if any), describe the experimental procedure you followed for collecting timing data, and finally, an analysis of the collected data. State any conclusions you can draw from the analysis. 

