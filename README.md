# nbwrapper
toolbox to run ipython notebooks as command line script with parameters

When working on bioinformatics projects, I often start off trying out stuff in a ipython notebook.
I usually end up having a whole data-processing pipeline in the notebook. To run this pipeline on a cluster or on different datasets, it would be nice to have it as a command line script with input parameters. 

Based on [runipy](https://github.com/paulgb/runipy) this toolbox helps building such command line wrapper scripts. 

## Installation
Simply `pip install nbwrapper`. 
`python setup.py install` also works. 

## Build the wrapper script
Use e.g. `argparse` to parse the command line arguments, use `nbwrapper` to run the notebook. 

test-wrapper.py: 
```python
#!/usr/bin/env python
# -*- coding: utf-8 -*-
from nbwrapper import nbwrapper
import argparse


argp = argparse.ArgumentParser()
argp.add_argument("--foo", '-a', help="foo arg")
argp.add_argument("--bar", '-b', help="bar arg")

args = argp.parse_args()
nb = nbwrapper(args, "test.ipynb")
nb.run()
```

## Retrieve arguments in the notebook
`nbwrapper.getargs()` returns a dict containing the arguments. 

test.ipynb
```python
# IN[0]:
    from nbwrapper import getargs
    args = getarts()
    print(args)
```



