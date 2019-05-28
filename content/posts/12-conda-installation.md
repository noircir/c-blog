---
title: Anaconda (conda) and virtualenv on Mac
date: 2019-05-26
description: Troubleshooting.
tags: 
- virtualenv
- conda
- anaconda
- Jupyter
- installation
---
### virtualenv and conda (Anaconda, Miniconda) compatibility

If you have Anaconda installed, then the usual `virtualenv` activation from the command line doesn't work (bash doesn't recognize `virtualenv` command). It is now done with conda. 
```
conda -v
conda update conda
conda search "^python$"   ## optionally check available Python versions 
conda create -n yourenvname
``` 
You also can specify Python version of virtualenv: 

`conda create -n yourenvname python=x.x anaconda`

Press `Y` to proceed. This will install the Python version and all the associated anaconda packaged libraries at `path_to_your_anaconda/anaconda3/envs/yourenvname`.

How to activate, deactivate, and remove virtualenv on Mac (on Windows, don't use the word `source`):

```
conda info -e
source activate yourenvname
source deactivate  ## -> deprecated. Use 'conda deactivate'
conda remove -n yourenvname -all
```
To see a list of all your environments, use this command:

`conda info -e`

More:

[Getting started with Conda](https://conda.io/projects/conda/en/latest/user-guide/getting-started.html#)

[Create virtual environments for python with conda](https://uoa-eresearch.github.io/eresearch-cookbook/recipe/2014/11/20/conda/)

[Error “virtualenv : command not found” but install location is in PYTHONPATH](https://stackoverflow.com/questions/39964635/error-virtualenv-command-not-found-but-install-location-is-in-pythonpath?noredirect=1&lq=1)


###Jupyter notebook fails to start on Mac
If you see a response:

`-bash: command jupyter is not found`

  it means that anaconda3 is not in your PATH. To fix:
```
export PATH=~/anaconda3/bin:$PATH
conda --version
which jupyter
which python
```
### To check package versions:
```
import sklearn
import numpy
print(sklearn.__version__)
print(numpy.__version__)
```