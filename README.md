## RTI CDS Analytics Exercise 01

Welcome to Exercise 01. This exercise provides a small SQLite database with some data derived from the 1996 US Census and a few analytic questions related to working with SQL and open source analysis packages.

### Using the Code

If you wish to submit via GitHub:
1. Fork this repository to your personal GitHub account and clone the fork to your computer. If you've received this repo as a zip file, ignore
    - **Note**: This does mean you will have a visible public fork of this repo on your github account.
2. Save and commit your answers to your fork of the repository, and push them back to your forked repository. Include code and writeup.
3. Provide a link to that fork of the repository in your submission.

If you wish to submit via an emailed zip file:
1. Clone this repository or download the code as a zip file (see image below)
2. Extract this repo (if downloaded as zip) and work locally with the code.
3. When finished, zip your project folder (code and writeup) and submit to the email you received the exercise from. Do not encrypt or add a password to the zip.

<img src="https://i.postimg.cc/KzwCd2Mg/Screen-Shot-2021-12-27-at-9-05-31-AM.png" alt="Downloading A Repo as a ZIP file" width="350">

### Some guidance

1. Use open source tools and ecosystems - Python or R. Do not use proprietary tools, such as SAS, SPSS, JMP, Tableau, or Stata. 
2. Use the Internet - including generative AI tools like ChatGPT - as a resource to help you complete your work. We do it all the time.
3. Comment your code such that a fellow data scientist who isn't familiar with this data or analysis could understand the steps you take.
4. There are many ways to approach and solve the problems presented in this exercise.
5. [DB Browser for SQLite](https://sqlitebrowser.org/dl/) is a cross-platform application you can use for initially exploring the SQLite database.
6. For language specific instructions on how to connect to a SQLite database, use your favorite search engine.


### The Task

You will be building a predictive model and writing up a summary of the data and your model. **The whole exercise should take no longer than 4 hours (self-timed)**.

Your **code** needs to perform the following tasks:
1. Write a SQL query that creates a consolidated dataset from the normalized tables in the database. In other words, write a SQL query that "flattens" the database to a single table.
1. Export the "flattened" table to a CSV file.
1. Import the "flattened" table (or CSV file) into your open source analytic environment of choice (R, Python) and stage it for analysis.
1. Perform a simple exploratory analysis and generate summary statistics to get a sense of what is in the data.
    * You should commit any useful or informative exploratory code.
1. Split the data into a 70/20/10 training, validation, and test data split. 
1. Develop a model that predicts whether individuals, based on the census variables provided, make over $50,000/year. Use `over_50k` as the target variable. 
    * Commit enough code to reproduce your full model selection process, including your final model and all models developed along the way.
1. Create a chart that you feel conveys one important relationship in the data.

Your **writeup** should do the following:
1. Describe your methodology and results in 500 words or less.
  - Include the chart generated as of your write-up. Explain how the chart informs your analysis. 
  - You'll not be punished for going over 500 words, but it is a rough guideline of the length we expect.
2. Include a chart that you feel conveys one important relationship in the data.

_Additional Context:_

* Assume the audience for your write-up is a non-technical stakeholder. 
* Assume the audience for your code is a colleague who may need to read or modify it in the future.


### The Data

This repository contains a file called `exercise01.sqlite`. It is a normalized relational [SQLite database](http://www.sqlite.org). 

It contains a table, named `records`, that has 48842 US Census records with the following fields:

- `id`: a unique id number for each record
- `age`: a continuous variable representing an individual's age
- `workclass_id`: foreign key to the `workclasses` table, representing the broad class of occupation of an individual
- `education_level_id`: foreign key to the `education_levels` table, representing the highest level of education an individual received
- `education_num`: a continuous variable representing an individual's current education level
- `marital_status_id`: foreign key to the `marital_statuses` table, representing an individual's marital status
- `occupation_id`: foreign key to the `occupations` table, representing an individual's occupation
- `race_id`: foreign key to the `races` table, representing an individual's race
- `sex_id`: foreign key to the `sexes` table, representing an individual's sex
- `capital_gain`: a continuous variable representing post-social insurance income, in the form of capital gains.
- `capital_loss`: a continuous variable representing post-social insurance losses, in the form of capital losses.
- `hours_week`: a continuous variable representing the number of hours per week an individual worked.
- `country_id`: foreign key to the `countries` table, representing an individual's native country
- `over_50k`: a boolean variable and **the target variable**, representing whether the individual makes over $50,000/year. A value of 1 means that the person makes greater than $50,000/year and a value of 0 means that the person makes less than or equal to $50,000/year.

Inspection of the database will reveal the reference tables and the values that they contain, referenced by the foreign keys in the categorical fields of the `records` table. Basically, anywhere you see a field name above that ends with `_id`, there is a corresponding table in the database that contains the values associated with that categorical variable. Fields that contain continuous values, such as `age`, do not join to other tables.

Some of the reference tables have an entry for a question mark `?` that represents missing data in `records`.

#### The Target Variable

The target variable is `over_50k` in the `records` table in the database.

