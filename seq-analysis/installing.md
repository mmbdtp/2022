---
layout: page
---

# Check environment, software, and tools ready for later exercises

We recommend installing command-line bioinformatics software through the package manager `conda`.

Conda is an open source package management system and environment management system that runs on Windows, macOS, Linux and z/OS. Conda quickly installs, runs and updates packages and their dependencies. Conda easily creates, saves, loads and switches between environments on your local computer. It was created for Python programs, but it can package and distribute software for any language.

* The installation instructions for [macOSX can be found here](https://docs.conda.io/projects/conda/en/latest/user-guide/install/macos.html)
* The installation instructions for [Linux can be found here](https://docs.conda.io/projects/conda/en/latest/user-guide/install/linux.html)

You should not be using a computer running windows for this course, unless you are using windows just to terminal into a system with MacOSX or Linux. 

##### In this week's course, you should use conda or containers (from week one) to manage your software


## Installing software via conda (shovill)
This an example of how to install shovill in it's own environment, which we will need later. 

```
conda create -n shovill shovill 
conda activate shovill
```

You can install more programs in a single environment, as below:
```
conda create -n myproject shovill samtools
conda activate myproject
```

You can add more software to an existing environment, as below:
```
conda activate myproject
conda install blast
```

## Installing Artemins, Bandage and Mauve 

Artemis, bandage and mauve are software with a graphical interface you can run on your local computer. Follow the instructions at:

* [https://rrwick.github.io/Bandage/](https://rrwick.github.io/Bandage/)
* [https://darlinglab.org/mauve/user-guide/viewer.html](https://darlinglab.org/mauve/user-guide/viewer.html)
* [https://www.sanger.ac.uk/tool/artemis/](https://www.sanger.ac.uk/tool/artemis/)

## What is mamba?

If you use conda, you should use `mamba`. What is `mamba` then? The website describes it as:

> A Python-based CLI conceived as a drop-in replacement for conda, offering higher speed and more reliable environment solutions

So you install `mamba` into your conda environment and for certain commands where you would use conda you use `mamba` instead. The parameters are effectively the same.

So when you want to Create an enviroment:
```
conda create  -n myenv -c bioconda samtools
# becomes
mamba create -n myenv  -c bioconda  samtools
```

Installing software: 
```
conda install bqplot
# becomes
mamba install bqplot
```

Removing software:
```
conda remove bqplot
# becomes
mamba remove bqplot
```

As you can see, it's pretty much substitute `conda` for `mamba`. The outcome is exactly the same, except the install time is much faster.

I usually keep seperate enviroments for each project, so I first create the enviroment with `conda` with `mamba` installed and then I switch to using mamba like the examples above. e.g.

```
conda create  -n myenv mamba
conda activate myenv
mamba install prokka
```

### Tips on organising your projects long term

A quick aside, "how should I organise my projects?" in the long term. 

* Use conda for package management (https://docs.conda.io/en/latest/)
* Jupyter notebooks for exploring data and plotting figures (https://jupyter.org/)

For Processing large datasets

* Use workflow languages (nextflow)
* [Bactopia](https://bactopia.github.io/) is a good all-included workflow to start