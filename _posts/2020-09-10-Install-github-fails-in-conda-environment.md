---
layout: post
title: Install github fails in conda environment on Linux
subtitle: Anaconda for Biologists
tags: [install, test, linux]
---
In a conda installation of R on a Linux machine, devtools::install_github fails because it is unable to find the correct system commands:
~~~
$ docker run --rm -it condaforge/linux-anvil bash
conda install -y r-base r-devtools unzip
$ R -q -e 'devtools::install_github("r-lib/devtools")'
> devtools::install_github("r-lib/devtools")
Downloading GitHub repo r-lib/devtools@master
from URL https://api.github.com/repos/r-lib/devtools/zipball/master
Installation failed: error in running command
~~~
One work around would be to create a conda package and host it on Anaconda Cloud, but this can be a lot of work (especially if the package has many dependencies without corresponding conda packages). Often I want to test out the package prior to making the effort to create a conda package for it.

The problem can be solved by setting the environment variables to system commands correctly:
~~~
R -q
> getOption("unzip")
[1] ""
> Sys.getenv("TAR")
[1] "/bin/gtar"
> options(unzip = "/opt/conda/bin/unzip")
> Sys.setenv(TAR = "/bin/tar")
> devtools::install_github("r-lib/devtools")
~~~
Note in the example above, I installed unzip via conda. On a system that has unzip, I usually use options(unzip = "/usr/bin/unzip").

Is there anyway to automatically configure these environment variables for the conda installation of R? In other words, without resorting to .Renviron or .Rprofile, which would also affect the system installation of R.


