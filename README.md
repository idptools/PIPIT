PIPIT
==============================

# **P**roteins **I**nto s**P**ecific random**I**zed segmen**T**s

## What is PIPIT?

**PIPIT** is a simple package to design shuffled protein sequences to interupt function.

How does it work?
PIPIT can be used within Python or from the terminal. Documentation for Python usage is coming soon


## Installation:

From PyPi, just use

    $ pip install idptools-pipit

To clone the GitHub repository and gain the ability to modify a local copy of the code, run

    $ git clone https://github.com/allOfTheGoodUsernamesWereTaken/PIPIT.git
    $ cd PIPIT
    $ pip install .

This will install GOOSE locally.

## Terminal usage - 

To use PIPIT from the terminal just use the **pipit-shuffle** command. There are 3 required pieces of information that must be supplied in this order.
**Required**
1. The sequence to be shuffled
2. The starting residue of the region of the sequence to either shuffle **which is default** or hold constant **if inverse is specified**
3. The ending residue of the region of the sequence to either shuffle **which is default** or hold constant **if inverse is specified**
**Optional**
*Number of blocks* 
If you use the -n or --number flag, you can specify a number of of blocks to break up the shuffled regions into. When you specify a number, PIPIT will return all possible shuffled sequences. By default, if the block number is not compatible with the size of the region that you are shuffling, PIPIT will add the remainder to the fewest possible blocks. Furthermore, PIPIT will let you know.
*Inverse*
If you want to specify a region to keep constant rather than a region to shuffle, simply use the -i flag.


### Copyright

Copyright (c) 2021, Ryan Emenecker Washington University School of Medicine


#### Acknowledgements
 
Project based on the 
[Computational Molecular Science Python Cookiecutter](https://github.com/molssi/cookiecutter-cms) version 1.5.
