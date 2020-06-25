# Wrangle and Analyze Data

Real-world data rarely comes clean. Using Python and its libraries, you will gather data from a variety of sources and in a variety of formats, assess its quality and tidiness, then clean it. This is called data wrangling. You will document your wrangling efforts in a Jupyter Notebook, plus showcase them through analyses and visualizations using Python (and its libraries) and/or SQL.

The dataset that you will be wrangling (and analyzing and visualizing) is the tweet archive of Twitter user @dog_rates, also known as WeRateDogs. WeRateDogs is a Twitter account that rates people's dogs with a humorous comment about the dog. These ratings almost always have a denominator of 10. The numerators, though? Almost always greater than 10. 11/10, 12/10, 13/10, etc. Why? Because "they're good dogs Brent." WeRateDogs has over 4 million followers and has received international media coverage.

## Project Details
Your tasks in this project are as follows:

* Data wrangling, which consists of:
  * Gathering data (downloadable file in the Resources tab in the left most panel of your classroom and linked in step 1 below).
  * Assessing data
  * Cleaning data
* Storing, analyzing, and visualizing your wrangled data
* Reporting on 1) your data wrangling efforts and 2) your data analyses and visualizations

## Directory Structure

This is the folder structure of the project

```bash
.
├── LICENSE
├── README.md                 ' This file for project description
├── act_report.html           ' Report file for Visualization
├── act_report.ipynb          ' Code file for Visualization
├── dand.yml                  ' Conda Env file
├── image-predictions.tsv     ' Tab delimited flat file downloaded by Gather Step
├── images                    ' Images used in reports
├── tweet-json.json           ' Twitter detail file provided by Udacity not used
├── tweet_json.txt            ' Twitter detail file created by Gather Step
├── twitter-archive-enhanced.csv ' Twitter enhanced file provided by Udacity and downloaded via Project Instructions
├── twitter.ini.template      ' Template ini file for credentials
├── twitter_analysis_source.csv ' Flat file persisted after Clean step
├── wrangle_act.html          ' Export file for Wrangling 
├── wrangle_act.ipynb         ' Code file for Wrangling 
├── wrangle_report.html       ' Report file for Wrangling 
└── wrangle_report.md         ' Source markdown for Report File
```

## Setup

### Prerequisites

1. Python setup on the host
2. conda setup on the host
3. conda environment that is similar to dand.yml
4. Rename `twitter.ini.template` as `twitter.ini`  and populate the credentials

### Running locally

1. Clone repository by running `git@github.com:seetdev/dand-p4.git`
2. Go into the cloned folder
3. Create conda environment `conda env create -f dand.yml`
4. Run the notebook using `jupyter notebook`