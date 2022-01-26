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
  - [Lecture 2, 01/20/22 (Wk1): Data Sampling and Probability](#lecture-2-012022-wk1-data-sampling-and-probability)
    - [Censuses and Surveys](#censuses-and-surveys)
    - [Sampling](#sampling)
    - [Common Non-Random Samples](#common-non-random-samples)
    - [Common Biases](#common-biases)
    - [The Literary Digest & The 1936 Election](#the-literary-digest--the-1936-election)
    - [Probability Sample (aka Random Sample)](#probability-sample-aka-random-sample)
    - [Simple Random Sample](#simple-random-sample)
    - [Approximation for sampling](#approximation-for-sampling)
    - [Binomial and Multinomial Probabilities](#binomial-and-multinomial-probabilities)
    - [Extra: Permutations and Combinations](#extra-permutations-and-combinations)
      - [Permutations](#permutations)
      - [Combinations](#combinations)
    - [Example: The Binomial Coefficient](#example-the-binomial-coefficient)
  - [Lecture 3, 01/25/22 (Wk1): Pandas](#lecture-3-012522-wk1-pandas)
    - [Resources](#resources)
    - [`Table` vs. `DataFrame`](#table-vs-dataframe)
    - [Indexing into DataFrames](#indexing-into-dataframes)
    - [Series](#series)
    - [Boolean Array Input and Alternatives](#boolean-array-input-and-alternatives)
    - [Some More Methods](#some-more-methods)

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

## Lecture 2, 01/20/22 (Wk1): Data Sampling and Probability

### Censuses and Surveys

In general, a **census** is "an official count or **survey** of a **population**, typically recording various details of individuals."

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

### Extra: Permutations and Combinations

#### Permutations

Given 5 people named A, B, C, D, & E...

a) **how many ways can ALL of them be arranged in a line?**

Any of the 5 people can be the first in line, and any of the 4 remaining people can be second in line, and any of those 3 remaining people can be third in line, and so on... which looks just like a factorial.

`n! = n * (n-1) * (n - 2) ... *  (n - k)`

`5! = 5 * 4 * 3 * 2 * 1` = 120 ways

b) **how many ways can THREE of them be arranged in a line?**

Any of the 5 people can be first in line, and any of the remaining 4 people can be second in line, and any of those remaining 3 people can be third in line, and nobody can be 4th in line.

`5 * 4 * 3` = 60 ways

`5 * 4 * 3` is equivalent to `5 * 4 * 3 * 2 * 1` / `2 * 1`, which is equivalent to `5!/(5 - 3)!` or `5!/2!`

The above case leads us to the general theorem for **permutations**, which holds the following:

- Having `n` objects and wanting to select `k` of them **in a certain order**, then the number of ways one can do this is `n! / (n - k)!`.

#### Combinations

Selecting three people from the set of 5 individuals {A, B, C, D, E} where **order does not matter**, we see that there are fewer selections. Compare the following:

- Ordered: ABE, EAB, BAE
- Unordered: ABE, EAB, BAE are all the same, so only one matters

For example, `3! people counted = 3 * 2 * 1 = 6 people = ABE, AEB, BAE, BEA, EAB, EBA`, which are really all the same now (when order doesn't matter)

Because of this, we need to divide our preivous answer by the number of times we overcounted: ``(5!/2!)/(3!)` turns into `5!/(2!3!)`.

The binomial coefficient is `(n k) = n! / (n - k)!k!`, read "n choose k".

### Example: The Binomial Coefficient

**How many ways can we flip a coin (whose flips are independent of one another) 7 times and see 3 heads?**

- Equivalent question: how m any different ways can we order the string "HHHTTT"?
- There are "7 positions." Choose 3 to be "H." This is 6 choose 4.

```
( n ) = (   n   )
( k )   ( n - k )
```
Choosing k successes is equivalent to choosing n - k failures.

## Lecture 3, 01/25/22 (Wk1): Pandas

### Resources

- [Data100 Pandas Reference](https://www.textbook.ds100.org/ch/a04/ref_pandas.html)

### `Table` vs. `DataFrame`

The **API** (application programming interface) for the `DataFrame` class is massive. When compared with the `Table` API from Data8, the two just don't compare; `DataFrame` is a much larger API.

**Syntactic sugar** - methods that are useful, but not necessarily for a library (or API) to function

### Indexing into DataFrames

- `loc` - return a subset of rows from a DataFrame
  - **ex:** `elections**.loc[0:4]` - first four rows from `elections`
  - Arguments passed to `loc` don't have to be in the same order in which they appear in the DataFrame
  - Usually preferable to use over `iloc` because it's safer (if the order of columns gets shuffled, the code still works) and more legible (easier to understand what code does when it includes dataframe labels instead of indexes)
  - [loc: pandas docs](https://pandas.pydata.org/docs/reference/api/pandas.DataFrame.loc.html)
- `iloc`
  - selects items by numbers
  - **ex:** `elections.iloc[[1, 2, 3], [0, 1, 2]]`
  - [`iloc`: pandas docs](https://pandas.pydata.org/docs/reference/api/pandas.DataFrame.iloc.html)
- `head`
  - **ex:** `elections.head(5)` is equivalent to `elections.loc[0:4]`
  - [`head`: pandas docs](https://pandas.pydata.org/docs/reference/api/pandas.DataFrame.head.html)
- `tail`
  - **ex:** `elections.tail(5)`
  - [`tail`: pandas docs](https://pandas.pydata.org/docs/reference/api/pandas.DataFrame.tail.html)
- `[]` *"Kool-Aid Notation"*
  - context sensitive
  - only takes one argument
  - **ex:** `elections[["Year", "Candidate", "Result"]]`

### Series

If we rquesting a single column, we're getting back a **series**, not a dataframe. The series class has [its own set of functions](https://pandas.pydata.org/docs/reference/api/pandas.Series.html).

### Boolean Array Input and Alternatives

**Boolean Array Input:**

- `elections[elections["Party"] == "Independent"]`

**Alternatives:**
  -  `.isin`
  -  `.str.startswith`
  -  `.query`
  -  `.groupby.filter`

### Some More Methods

1) By default, `sample` selects without replacement. Use `replace=True` in the arguments of the method call for replacement. **ex:** `elections**.sample(5, replace = True).iloc[:, 0:2]`

2) `Series.unique` method returns an array of every unique value in a Series

3) `DataFrame.sort_values` and `Series.sort_values` methods sort a `DataFrame` or `Series` in alphabetical order
