---
layout: post
title: Installing R and Python in Bioconda
subtitle: Anaconda for Biologists
tags: [install, test, linux]
---
This guide will take users through installation of R in a new Anaconda virtual environment. I always recommend biologists use Anaconda for managing R and its dependencies, because it gives us access to the Bioconda channel. The Bioconda channel is an incredibly powerful hub for many of the most important bioinformatic software. Not only does it consolidate the packages into a single channel, it manages version dependencies between them.

Any software stack that can be built with Anaconda can be replicated on any other similar system with ease. Reproduce-ability of environments and results is a must for biological research in the computer age.

We will make frequent mention of Python in this guide. This is because, at its core, Anaconda is a virtualizer for Python. There is a close relationship between Python and R in the biology community, so they are managed simultaneously by Anaconda. The principles in this guide can be similarly applied to creating Python environments. See the relevant section of the related guide in this repository on installing Python.

### Creating a Virtual Environment (UNIX)

We will reference this document: conda.io/docs/using/envs.html throughout.

We will name our environment “Bio” for these examples.

To create an environment: conda create --name Bio python=3.7
To activate the environment: source activate Bio
To deactivate the environment: source deactivate Bio
To list environments: conda info --envs
To remove an environment: conda remove --name Bio --all

After activating the environment, the command line will be prepended by (Bio) and the $PATH variable will be modified to point to anaconda3/envs/Bio/bin.

We will install dependencies to the virtual environment, so make sure the `(Bio)` environment is active for the next steps.

### Creating a Virtual Environment (Windows)
We will reference this document: conda.io/docs/using/envs.html throughout.

Windows users will run these commands in the Anaconda Prompt. The only difference is Windows users will ignore the `source` command when acitvating and deactivating virtual environments.

To create an environment: conda create --name Bio python=3.7
To activate the environment: activate Bio
To deactivate the environment: deactivate Bio
To list environments: conda info --envs
To remove an environment: conda remove --name Bio --all

After activating the environment, the command line will be prepended by (Bio) and the $PATH variable will be modified to point to anaconda3/envs/Bio/bin.

We will install dependencies to the virtual environment, so make sure the (Bio) environment is active for the next steps.


Run these commands in order. This will install R, RStudio, and add various channels for future package installations.

1. conda config --add channels conda-forge
2. conda config --add channels defaults
3. conda config --add channels r
4. conda config --add channels bioconda
5. conda install r
6. conda install rstudio

### Using the Anaconda Environment
Now, whenever you are working on this project, make sure you are operating in the (Bio) virtual environment. When you are using an IDE, you may have to tweak the settings to make sure it is using the (Bio) environment. When you are using the command line, make sure that you have activated the environment and (Bio) is prepended to the command line.

For maximum convenience, start RStudio from the Anaconda Prompt or command line by running rstudio from your virtual environment. This will load RStudio with your virtual environment’s R installation rather than your system’s R installation.

### Installing Bioconda Packages
Most of the popular bioinformatics packages that you will encounter are managed by Bioconda. In addition, most of them are UNIX-only. Use the following commands to install a few you may be interested in:

1. conda install bioconductor-phyloseq
2. conda install bioconductor-rsamtools
3. conda install bwa
4. conda install fastqc
5. conda install multiqc
6. conda install delly
7. conda install bowtie
8. conda install bedtools

Check out bioconda.github.io/recipes.html for the full list of Bioconda packages, and docs.continuum.io/anaconda/pkg-docs for a full list of Anaconda packages.

### Opening RStudio with your Anaconda Environment
Simply run:

1. rstudio
in the Anaconda Prompt or the terminal with your Anaconda Environment active. RStudio will open with the R version and packages of the environment. No hassle.