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
  - [Lecture 3, 01/25/22 (Wk2): Pandas I](#lecture-3-012522-wk2-pandas-i)
    - [Resources](#resources)
    - [`Table` vs. `DataFrame`](#table-vs-dataframe)
    - [Indexing into DataFrames](#indexing-into-dataframes)
    - [Series](#series)
    - [Boolean Array Input and Alternatives](#boolean-array-input-and-alternatives)
    - [Some More Methods](#some-more-methods)
  - [Lecture 4, 01/27/22 (Wk2): Pandas II](#lecture-4-012722-wk2-pandas-ii)
    - [Example: Custom Sorts](#example-custom-sorts)
    - [Column Addition](#column-addition)
    - [Example: `Groupby.agg`](#example-groupbyagg)
    - [Example: `.filter()`](#example-filter)
    - [Example: `.pivot()`](#example-pivot)
  - [Lecture 5, 01/28/22 (Wk3): Data Cleaning, EDA](#lecture-5-012822-wk3-data-cleaning-eda)
    - [Data Wrangling](#data-wrangling)
    - [Exploratory Data Analysis (EDA)](#exploratory-data-analysis-eda)
      - [Some Context](#some-context)
    - [What should we look for? (there's a lot!)](#what-should-we-look-for-theres-a-lot)
      - [Structure](#structure)
      - [Granularity](#granularity)
      - [Scope](#scope)
      - [Temporality](#temporality)
      - [Faithfulness](#faithfulness)
      - [Missing Data & Input Values](#missing-data--input-values)
  - [Lecture 6, 01/30/22 (Wk3): Regular Expressions (Regex)](#lecture-6-013022-wk3-regular-expressions-regex)
    - [Resources](#resources-1)
      - [Python String Methods](#python-string-methods)
    - [What is a Regular Expression?](#what-is-a-regular-expression)
    - [Regex Syntax](#regex-syntax)
      - [Order of Operations](#order-of-operations)
      - [Expanded Regex Syntax](#expanded-regex-syntax)
      - [Convenient Regex](#convenient-regex)
      - [Even More Regex Features](#even-more-regex-features)
  - [Lecture 7, 02/8/22 (Wk3): Data Visualizations](#lecture-7-02822-wk3-data-visualizations)
    - [Resources](#resources-2)
    - [Goals of Data Visualization](#goals-of-data-visualization)
    - [Distributions](#distributions)
    - [Describing Distributions](#describing-distributions)
      - [Bar Plot](#bar-plot)
      - [Rugplot](#rugplot)
      - [Box Plot](#box-plot)
      - [Histogram](#histogram)
      - [Violin Plot](#violin-plot)
      - [Scatter Plot](#scatter-plot)
      - [Hex Plot](#hex-plot)
      - [Contour Plot](#contour-plot)

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

Because of this, we need to divide our preivous answer by the number of times we overcounted: `(5!/2!)/(3!)` turns into `5!/(2!3!)`.

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

## Lecture 3, 01/25/22 (Wk2): Pandas I

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
  - [`loc`: pandas docs](https://pandas.pydata.org/docs/reference/api/pandas.DataFrame.loc.html)
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

If we're requesting a single column, we're getting back a **series**, not a dataframe. The series class has [its own set of functions](https://pandas.pydata.org/docs/reference/api/pandas.Series.html).

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

## Lecture 4, 01/27/22 (Wk2): Pandas II

### Example: Custom Sorts

What does the following code do?

`babynames.query('Sex == "M" and Year == 2020').sort_values("Name", key = lambda x: x.str.len(), ascending = False)`

### Column Addition

```py
# create a new series of only the lengths
babyname_lengths = babynames["Name"].str.len()

# add that series to the dataframe as a column
# this next line adds the column
babynames["name_lengths"] = babyname_lengths
```

*Side note:* when dropping a column, you need to add an axis (like `axis = "column"` inside the arguments to the function call)

### Example: `Groupby.agg`

`female_babynames.groupby("Name").agg(ration_to_peak)`
- Takes the `female_babynames` dataframe and separates unique names (items in the column "Name") and adds a row with a column based on the collection function

*This method will be covered more in Lab 2, released tomorrow (Friday, January 28th)*

### Example: `.filter()`

- [`.filter()`: pandas docs](https://pandas.pydata.org/docs/reference/api/pandas.DataFrame.filter.html)

### Example: `.pivot()`

<img src="images/../../images/lec-4-0.png">

## Lecture 5, 01/28/22 (Wk3): Data Cleaning, EDA

### Data Wrangling

**Data Wrangling** is the process of transforming *raw data* to facilitate subsequent analysis

Addresses issues such as:
- are numbers stored as integers or as strings? (structure/formatting)
- missing or corrupted values
- unit conversion
- etc.

### Exploratory Data Analysis (EDA)

**Exploratory Data Analysis (EDA)** is the process of *transforming*, *visualizing*, or *summarizing* data to build/confirm understanding of the data and its **provenance** (origin of data; methodology by which data were produced).

EDA is open-ended! Be prepared to find results that may surprise you.

#### Some Context

John Tukey, Princeton Mathematician & Statistician, coined and introduced:
- *Fast Forier Transform* algorithm
- *"Bit":* binary digit
- *EDA!*


### What should we look for? (there's a lot!)

This list serves as Sparknotes for the [lecture slides](https://docs.google.com/presentation/d/1R9lPV6ysgxGKe5g9vnfzh7Z6p8R5wmNQtE4k-lZEn74/edit#slide=id.g10ff83c27a6_0_1518).

#### Structure

*Structure* - the "shape" of a data file

- File types: TSV, CSV, JSON, etc.
- Rectangular data: tables vs. matrices

JSON files are particuilarly useful because they save **metadata**, data about the data! However, there is no `read_data` method in pandas, and the metadata isn't stored in rectangular form.

**Variables** are equivalent to **fields**. Each **record** has a set of variables, and all data are comosed of **records**. Variables are defined by their type

**Feature types:**

```
Variable ----------------> Qualitative (categorial)
  |     |                   |                   |
  |     V                   |                   V
  |   Discrete (finite)     |   Nominal (No specific ordering)
  V                         V
Continuous (infinite)       Ordinal (no order)
```

**Primary Key:** the column or set of columns in a table that determine the values of the remaining columns.

**Foreign Keys:** the column or sets of columns that reference primary keys in other tables

#### Granularity

*Granularity* - how fine/coarse is each datum

**Question:** what does each record represent? A purchase, a person, a group of users, etc.

**Coarse data** is that which is sampled, average, etc.: combined in some way and not raw 

#### Scope
 
*Scope* - how (in)complete is the data

**Questions:** Does my data cover my area of interest? Are my data too expansive? If so, *filter it*!

Scope is really about **sampling frame**, the population from which the data were sampled. If the sampling frame is too small, do we need more data? If the sampling frame is too big, do we need to filter it? Does the sampling frame capture *reality*? Is anything even real?? (I'm just joking, that's up for debate in [Philos125](https://philosophy.berkeley.edu/courses/detail/350))

#### Temporality

*Temporality* - how the data is situated in time

**Questions:** When was the data collected? Is there periodicity? Diurnal (24-hr) patterns? What about timezones? If you've taken CS61B, you might be familiar with formatting datatime from building Gitlet.

**UNIX-** time measured in seconds since January 1st 1970! Unix time follows Coordinated Universal Time (UTC).

#### Faithfulness

*Faithfulness* - how well does the data represent reality?

**Questions:** do I really trust this data? Does it contain unrealistic or incorrect values? Are there some locations that don't exist, negative counts, typos, large outliers, etc. Does my data violate *obvious dependencies* (such as "age" and "birthday" not matching)? 

**Wait, but what about data falsification?** Try and spot it!

#### Missing Data & Input Values

We can address missing data and input values by:
- **Dropping data** with missing values (most common approach)
- **Imputation** (inferring missing values)
  - Average imputation - replace with an *average* value
  - Hot deck imputation - replace with a *random* value
- Directly model missing values during future analysis
- Drop missing values but check for *induced values* (using domain knowledge, which may potentially come from your domain emphasis)!

## Lecture 6, 01/30/22 (Wk3): Regular Expressions (Regex)

### Resources

- [Data100 Regex Practice](https://ds100.org/sp22/resources/#regex-practice)
- Check your Regex with [Regex101](https://regex101.com/)
- Python [re.sub](https://docs.python.org/3/library/re.html#re.sub)
  - The Pandas equivalent [Series.str.replace](https://pandas.pydata.org/pandas-docs/stable/reference/api/pandas.Series.str.replace.html)
- Python [re.findall](https://docs.python.org/3/library/re.html#re.findall)
  - The Pandas equivalent [Series.str.findall](https://pandas.pydata.org/pandas-docs/stable/reference/api/pandas.Series.str.findall.html)

**Canonicalization** is the process of converting data into a standardized *canonical* form.

#### Python String Methods

<img src="images/../../images/lec-6-0.png">

### What is a Regular Expression?

A **regular expression** (*regex*) is a sequence of characters that specifies a search pattern.

- **Example 1:** `[0=9]{3} - [0-9]{2} - [0-9]{3}` represents the set of all possible social security numbers. 
- [Example 2](https://tinyurl.com/ds100reg1)
- [Example 3](https://tinyurl.com/ds100reg02)

### Regex Syntax

#### Order of Operations
<img src="images/../../images/lec-6-1.png">

#### Expanded Regex Syntax
<img src="images/../../images/lec-6-2.png">

#### Convenient Regex
<img src="images/../../images/lec-6-3.png">

#### Even More Regex Features
<img src="images/../../images/lec-6-4.png">

## Lecture 7, 02/8/22 (Wk3): Data Visualizations

### Resources

- [Lecture 7 Slides: Plotting for Distributions](https://docs.google.com/presentation/d/16I18f4NlOdODeQ20e4YQVwDJ_869MHKKklWeMmYK8IQ/edit#slide=id.g11326e8245b_0_326) – *note that the lecture slides contain comprehensive explanations whereas these notes serve as a quick summary of thoses same slides*

### Goals of Data Visualization

- **Goal 1:** To help your own understanding of your data/results
- **Goal 2:** To communicate results/conclusions to prove

### Distributions

A **distribution** describes the frequency at which values of a variable occur:

- Every value is accounted for **only once**
- All values add up to 100%

### Describing Distributions

**Skweness** (somewhat counterintuitive)
- **Skewed right**: long right tail
- **Skewed left**: long left tail
- **Symmetric**: tails are of equal size

**Outliers**
- What qualifies as an "outlier"? Defining outliers is a judgement call (we'll come back to this later)

**Mode**
- Local or a global maximum
- **Unimodal**: single clear maximum
- **Bimodal**: two modes
- Note that we need to distinguish between modes and **random noise**; we can use a **Kernel Density Estimate** to do this

#### Bar Plot

- Most comon way of displaying the distribution of a **qyalitative (categorical) variable**
- The lengths of the bars encode *values*, while widths encode *nothing*

<img src="images/../../images/lec-7-0.png">

#### Rugplot

<img src="images/../../images/lec-7-1.png">

#### Box Plot

<img src="images/../../images/lec-7-2.png">

#### Histogram

Note that the y-axis label is **density**, not *count*!
<img src="images/../../images/lec-7-7.png">

#### Violin Plot

<img src="images/../../images/lec-7-3.png">

#### Scatter Plot

<img src="images/../../images/lec-7-4.png">

#### Hex Plot

<img src="images/../../images/lec-7-5.png">

#### Contour Plot

<img src="images/../../images/lec-7-6.png">