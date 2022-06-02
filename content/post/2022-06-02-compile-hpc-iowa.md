---
title: "Compiling R on University of Iowa HPC"
author: "Brandon LeBeau"
date: 2022-06-02
categories: ["r", "HPC", "Iowa", "compile"]
slug: "compile-hpc-iowa"
math: true
---

As of writing this (June 2022), there is a relatively new version of R, R 4.2.0, published in April of 2022. I like to use recent versions of R, both on my computers, but also on the high performance computing (HPC) system that I use occasionally here at the University of Iowa. Unfortunately, to use up to date versions of R requires a bit of work as the release cycle for R tends to be quicker than the HPC update cycle. 

As such, I compile R on the HPC system to use and launch by default. I'm documenting this for a few reasons, one for future me, but also for anyone else looking to compile R on an HPC system. This is likely the most useful for those at the University of Iowa as it could be almost copied and pasted, but the general structure/requirements may be useful for others. The compilation procedure was adapted from an [RStudio docs page](https://docs.rstudio.com/resources/install-r-source/). 

## Download R Source

After logging into the HPC system, the following commands will download R-4.2.0 (using `curl`), extract the source files into a directory (using `tar`), make a new directory to install R to (using `mkdir`), and move to the extracted directory (using `cd`). The portion of making a new directory is important in the HPC environment as sudo rights are not enabled, therefore, R needs to be installed to the local profile. More on this in future steps to ensure this version of R is launched by default. 

```bash
curl -O https://cran.rstudio.com/src/base/R-4/R-4.2.0.tar.gz
tar -xzvf R-4.2.0.tar.gz

mkdir R-4.2

cd R-4.2.0
```

## Configure R for Compilation

Next, configuration of how R should be compiled is specified. This is done with `./configure` and at least 1 option is needed to ensure the R is installed to the proper location within the local directory. This again, is very important on the HPC where write access is only granted to the personal directory and is not allowed globaly. For your processing at the University of Iowa HPC, you would change the HawkID part with your specific HawkID. I set this with the `export` command to assign a specific value to the object HawkID that is used within the `./configure` command. 

```bash
export HawkID=bleb

./configure \
    --prefix=/Users/${HawkID}/R-4.2/ \
    --enable-memory-profiling \
    --enable-R-shlib \
    --with-blas \
    --with-lapack
```

### Load Required Software for Compilation

When you run this as is and it is the first time compiling R from source, the configure command will likely fail. This is due to needing to ensure that the required dependencies are available to actually compile R, this is one this the configure command checks for. The University of Iowa HPC uses a module system for loading specific software and these can be loaded with `module load software_name`. More explicitly, gcc is need to compile R, this can be loaded with the following command: `module load gcc/9.3.0`. 

This is the list of the software I had loaded when compiling R 4.2.0 which I obtained from running `module list`:

  1) stack/2021.1               
  2) readline/8.1_gcc-9.3.0     
  3) xz/5.2.5_gcc-9.3.0       
  4) bzip2/1.0.8_gcc-9.3.0      
  5) libiconv/1.16_gcc-9.3.0    
  6) libxml2/2.9.10_gcc-9.3.0   
  7) tar/1.34_gcc-9.3.0         
  8) gettext/0.21_gcc-9.3.0     
  9) binutils/2.36.1_gcc-9.3.0  
  10) libunistring/0.9.10_gcc-9.3.0
  11) libidn2/2.3.0_gcc-9.3.0
  12) openssl/1.1.1k_gcc-9.3.0
  13) curl/7.76.0_gcc-9.3.0
  14) gcc/9.3.0
  15) ncurses/6.2_gcc-9.3.0
  16) zlib/1.2.11_gcc-9.3.0
  17) pcre2/10.35_gcc-9.3.0
  18) openjdk/11.0.8_10_gcc-9.3.0
  
One all of these are loaded with the `module load` command, then the `./configure` command can be ran again to configure the compilation. Note, it is helpful to check that all of the modules were properly loaded by using the `module list` command prior to doing configure. 

## make and make install

The final two commands that do the actual installation are `make` and `make install`. Note, you do not need sudo for these and on the HPC system, as the `./configure` command specified the local directory to install the system. Note, the `make` command can take quite some time (took me about 20 minutes or so) as it does the compilation of R and the base R packages that come with R base. 

## Ensure Compiled R Version is Default

One element that I had difficulties with when I compiled R 4.1.0 was ensuring that this version was the default R loaded on my HPC setup. Since the compiled R version was installed locally, I use a .bash_profile and .bashrc files to ensure that when I type `R` on the HPC system, my latest compiled version of R is launched. I believe you only need one of these files, I would start with the .bash_profile first, but I ended up creating both when I had problems with the R 4.1.0. 

The following is my .bashrc file:

*Note, in the .bashrc file, you will need to specify your own HawkID or more generally the local directory that was used to install R*

```bash
# .bashrc

# Source global definitions
if [ -f /etc/bashrc ]; then
	. /etc/bashrc
fi

# User specific aliases and functions
alias R="/Users/bleb/R-4.2/bin/R"
alias Rscript="/Users/bleb/R-4.2/bin/Rscript"
```

The following is my .bash_profile:

```bash
# .bash_profile

# Get the aliases and functions
if [ -f ~/.bashrc ]; then
	. ~/.bashrc
fi

# User specific environment and startup programs

PATH=$HOME/R-4.2/bin:$PATH:$HOME/.local/bin:$HOME/bin

export PATH
```

After creating these files in your root local HPC directory, I log out then back into my HPC system for these files to take effect. Then, the compiled R version should be accessible via the command, `R` or when submitting a job with the `RScript` command. 

Happy compiling!
