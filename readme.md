This project tries to provide an example of how you might model pupilometry data using hierarchical generalised additive models (gams).

Sounds complicated. But it's just a multi-level (mixed) model that can fit curves instead of straight lines AND the model decides on the curviness or wiggliness. All of which is rather satisfying compared to many alternatives.

# Backgroup reading and material #

1. Key modelling papers are here:

https://doi.org/10.1177/2331216519832483

https://doi.org/10.7717/peerj.6876


The slight additional twist in this project is that we use a Bayesian formulation. The above papers use a frequentist approach and the 'mgcv' package. Here, we use brms (which in turn uses stan) to fit these models in a Bayesian way, whilst also noting that brms uses the smooth functions provided by the mgcv package. So, we use mgcv smooth functions in a Bayesian way. Clear as mud? Thought so.

2. And a great paper on preprocessing and analysing pupil data more generally that Jenny sent me (thanks Jenny):

https://doi.org/10.3758/s13428-023-02098-1

From becomes very clear from reading this paper is that there are a zillion ways to analyse pupil data and it depends on your aim and scientific question which may (or ways) you might choose. And more specifically, there are may different ways to preprocess pupil data and many ways to model it. And your choice of modelling approach matters for how you migtht preprocess the data. So, all in, the most important thing (as always!) is to be clear on your choices, be explicit how they fit the question, and make the code and data available, so that folks know.


# What is the easiest way to access this project? #

If you want to see and work with the code, then:

1. Clone, fork or download the project from github to your local machine.
See this link for the difference between cloning and forking. https://github.com/orgs/community/discussions/35849

2. Open the pupil_example.Rproj file and renv() will automatically bootstrap itself.

3. Use renv::restore() to install all of the packages. Say yes.

4. At this point, you can use the project with the same package versions that are stored in the renv.lock file.

# System requirements #

Data analysis was performed in the R programming language (v4.4.0; R Core Team, 2024). 
All package dependencies were recorded and controlled via renv(). 
For an introduction to renv() for package management, see here: https://rstudio.github.io/renv/articles/renv.html.


# Basic structure of the project #

## R project file ##

All files and folders are based within an R project called 'pupil_example.Rproj'

## There are three main R markdown files: ##

**1. wrangle.Rmd**

This file wrangles raw data, produces some summary data plots, saves out data files for modelling and further analysis in later scripts.

**2. model.Rmd**

This file builds Bayesian regression models.

**3. effects.Rmd**

This file visualises and tabulates parameters and/or posterior predictions of interest.

## There are four sub-folders, which have largely self-explanatory titles: ##

**1. /figures/**

**2. /tables/**

**3. /models/**

**4. /data/**

## A brief description of the dataset ##

[[note - some of these details might be wrong. Jenny knows the truth.]]

The data comes from Jenny's PhD work, which is about motor slowing. In this case, the task involves wrist flexion and extension movements (as fast as possible) for 40 seconds. After 20 seconds, there is an experimental manipulation, where a cue is presented. The cue can signal that a reward is available (1 CHF, I think), if they wrist-tap quickly, or that no reward is available. Therefore, the design has one within-participant experimental factor with two levels (neutral and reward).

There are 20 trials per participant (half neutral, half reward). Order of condition was randomised across each pid's trials.

In this project I only include pupil size over time (movement cycles are not included here).

And the sampling rate for pupil size measurements was ~60Hz during data collection. But the data analysed here has been re-sampled to 5Hz, so that modelling will be a lot faster. And to minimise issues with auto-correlation. 





