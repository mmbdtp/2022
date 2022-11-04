---
layout: page
---

# Check environment, software, and tools ready for later exercises

We recommend installing command-line bioinformatics software through the package manager `conda`.

`Conda` is an open source package management system and environment management system that runs on Windows, macOS, Linux and z/OS. `Conda` quickly installs, runs and updates packages and their dependencies. `Conda` easily creates, saves, loads and switches between environments on your local computer. It was created for `Python` programs, but it can package and distribute software for any language.

* The installation instructions for [macOSX can be found here](https://docs.conda.io/projects/conda/en/latest/user-guide/install/macos.html)
* The installation instructions for [Linux can be found here](https://docs.conda.io/projects/conda/en/latest/user-guide/install/linux.html)

You should not be using a computer running windows for this course, unless you are using windows just to terminal into a system with MacOSX or Linux. 

Andrea has an extended guide here: [https://telatin.github.io/microbiome-bioinformatics/Install-Miniconda/](https://telatin.github.io/microbiome-bioinformatics/Install-Miniconda/). 


###### In this week's course, you should use conda or containers (from week one) to manage your software


### Installing software via conda (shovill)
This an example of how to install `shovill` in it's own environment, which we will need later. 

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

### Installing Artemins, Bandage and Mauve 

Artemis, bandage and mauve are software with a graphical interface you can run on your local computer. Follow the instructions at:

* [https://rrwick.github.io/Bandage/](https://rrwick.github.io/Bandage/)
* [https://darlinglab.org/mauve/user-guide/viewer.html](https://darlinglab.org/mauve/user-guide/viewer.html)
* [https://www.sanger.ac.uk/tool/artemis/](https://www.sanger.ac.uk/tool/artemis/)

### What is mamba?

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

* Use `conda` for package management (https://docs.conda.io/en/latest/)
* `Jupyter` notebooks for exploring data and plotting figures (https://jupyter.org/)

For Processing large datasets

* Use workflow languages (`nextflow`)
* [Bactopia](https://bactopia.github.io/) is a good all-included workflow to start


### Some guidance on getting Jupyter notebooks up and running
*This is for future reference, and is not covered in this course.* 

You can Install and control R and jupyter notebooks through `conda`.

You can naturally change the name of the `conda env` (I used mapdemo here) to anything you like. I use mamba here to speed up the install process. I highly recommend mamba! I explain mamba in more detail here.

The first mamba install line is to install `jupyter` notebook, the second is for `R`, the `R` kernel for `jupyter` and common `R` packages `dplyr` and `ggplot`. The third `mamba` install line is for more specific `R` packages I want to use.

```
conda create -n mapdemo mamba
conda activate mapdemo
mamba install -y -c conda-forge pip notebook  nb_conda_kernels  jupyter_contrib_nbextensions
mamba install -y -c conda-forge r r-irkernel r-ggplot2 r-dplyr
mamba install -y -c conda-forge r-sf  r-ggrepel  r-cowplot r-maps
```

#### Starting the notebook
Once these are all installed you can start the `jupyter` notebook from a diretory of your choosing. Here I just make a demo directory

```
mkdir demo
jupyter notebook
```

You will then see the `jupyter` service start up and it will tell you where you can access it i.e. `http://localhost:8888/`

```
(mapdemo) ubuntu@chomp:~/code/demo$ jupyter notebook
[I 10:36:03.954 NotebookApp] [nb_conda_kernels] enabled, 8 kernels found
[I 10:36:04.186 NotebookApp] [jupyter_nbextensions_configurator] enabled 0.4.1
[I 10:36:04.188 NotebookApp] Serving notebooks from local directory: /home/ubuntu/code/demo
[I 10:36:04.188 NotebookApp] Jupyter Notebook 6.4.11 is running at:
[I 10:36:04.188 NotebookApp] http://localhost:8888/
[I 10:36:04.188 NotebookApp] Use Control-C to stop this server and shut down all kernels (twice to skip confirmation).
```

