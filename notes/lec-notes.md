# Data 100: Principles and Techniques of Data Science

    University of California, Berkeley
    Instructors: Josh Hug
    j.hug@berkeley.edu
    Office Hours: TBD
    https://ds100.org/sp22
    Lecture: Tues/Thurs 3:30pm-5:00am 
    Zoom link TBD
    Author: Will Tholke

## Table of Contents

- [Data 100: Principles and Techniques of Data Science](#data-100-principles-and-techniques-of-data-science)
  - [Table of Contents](#table-of-contents)
  - [Lecture 1, 01/18/22 (Wk1): Course Overview](#lecture-1-011822-wk1-course-overview)
    - [Associated Reading](#associated-reading)
    - [The Data Science Lifecycle](#the-data-science-lifecycle)
  - [Lecture 1, 01/20/22 (Wk1): Data Sampling and Probability](#lecture-1-012022-wk1-data-sampling-and-probability)
    - [Censuses and Surveys](#censuses-and-surveys)
    - [Sampling](#sampling)
    - [Common Non-Random Samples](#common-non-random-samples)
    - [Common Biases](#common-biases)
    - [The Literary Digest & The 1936 Election](#the-literary-digest--the-1936-election)
    - [Probability Sample (aka Random Sample)](#probability-sample-aka-random-sample)
    - [Simple Random Sample](#simple-random-sample)
    - [Approximation for sampling](#approximation-for-sampling)
    - [Binomial and Multinomial Probabilities](#binomial-and-multinomial-probabilities)

## Lecture 1, 01/18/22 (Wk1): Course Overview

### Associated Reading

- [0: Notation](https://www.textbook.ds100.org/notation.html)
- [1.1: The Students of Data 100](https://www.textbook.ds100.org/ch/01/lifecycle_intro.html)
- [1.2: Exploratory Data Analysis](https://www.textbook.ds100.org/ch/02/data_scope_intro.html#)

### The Data Science Lifecycle

The following positive feedback loop is called the **data science lifecycle**:

1) Formulate a question or problem
2) *Acquire* and *clean* data
3) Conduct **exploratory data analysis** (EDA)
4) Use *prediction* and *inference* to draw conclusions

## Lecture 1, 01/20/22 (Wk1): Data Sampling and Probability

### Censuses and Surveys

In general, a **census** is "an official count or **survey** of a **population**, typically recording various details of individuals.

A **survey** is defined as a set of questions, i.e. Decennial Census Questionnaires. Stat 152 (Sampling Surveys) goes into sampling in more detail.

In the case of the Decennial Census, the high court rejected sampling, but why? It often minoritized the poor and those who voted Democratic.

### Sampling

The **population** is the group you want to know something about whereas the **sampling frame** is the list from which the sample is drawn. 

- Note that *the sample is a subset of your sampling frame* but not your population. There may be individuals in the sample frame that are not in the population.


A **sample** is a subset of the population often used to make inferences about that population.

- Chance error
- Bias: systematic error in one direction

### Common Non-Random Samples

**Convenience Sample:** whoever you can get ahold of; not a good idea for inference!

**Quota Sample:** first specify the desired breakdown of various subgroups, then reach those targets however you can

### Common Biases

**Selection Bias:** systematically excluding/favoring certain groups

**Response Bias:** people don't always respond untruthfully

**Non-response Bias**: people don't always respond

### The Literary Digest & The 1936 Election

The Literary Digest was horrifically inaccurate about the impending 1936 election result because their sampling frame was those who were rich enough to own a landline, subscribe to magazines, and belong to a country club. See **selection bias** and **non-response bias**.

### Probability Sample (aka Random Sample)

Random samples may have bias, but they allow us to *estimate the bias and chance error*.

A **probability** sample from a random sampling scheme has the following properties:
- must be able to provide the chance that any specified set of individuals will be in the sample
- All individuals in the population need not have the same chance of being selected

### Simple Random Sample

Every subset of the same size has the same probability of being selected.

### Approximation for sampling

If the population is huge compared to the sample, then *random sampling with and without replacement are nearly equivalent*.

### Binomial and Multinomial Probabilities

**Binomial and multinomial probabilities arise when we:**

- Sample at random with replacement
- Sample a fixed number (n) times
- Sample frmo a categorical distribution:
  - If 2 categories (binomial):
    - Bag of marbles: 60% blue, 40% not blue
  - If >2 categories (multinomial):
    - Bag of marbles: 60% blue, 30% green, 10% red

**Goal:** Count the number of each category that end up in our sample using `np.random.multinomial`

For examples of binomial and multinomial probabilities, start reading from Slide 36 of the [Lecture 2 Slides](https://docs.google.com/presentation/d/15CbbMS0guv9CNJTTDP4h5T4hrNK8rJJ2cO1rmXo3H3Y/edit#slide=id.g10c5bf81273_0_46)!