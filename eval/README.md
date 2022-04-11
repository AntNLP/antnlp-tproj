
# Model Evaluation 

We need to evaluate models both in training and testing.
It is crucial to understand evaluation metrics (it leads to an ACCEPT!!),
and writing evaluation scripts is, of course, a correct way to fully understand them.
On the other side, 
there are official (or highly optimized) scripts for many metrics.
They are the final judges and should be consulted in our projects.

> Separating evaluation scripts from model source files

## Overview 

This directory contains evaluation scripts (either from third parties or written by us).
We suggest using files to unify communication to thoes scripts, that is,

- Step 1. predict labels for samples 
- Step 2. write samples to a file 
- Step 3. call the script with the file arguments  
- Step 4. read outputs of the script

Consider that our models may be evaluated by different scripts 
(e.g., the model is applied to different datasets which have 
different official evaluation toolkits),
it is highly recommended that the model always outputs samples in a fixed format,
and writing helping scripts to adapt it to different evaluation scripts, that is,

- Step 2. write samples to a file (with the model's output format)
- Step 2'. transform the file to satisfy the script's requirement (using helping scripts)
- Step 3. call the script with the file arguments  
- Step 3'. transform the script's output back to the model's input format

>

## Tips

- since writing and reading files may course additional i/o cost 
(especially when evaluating on dev sets during training), a common
strategy is to issue asynchronized file i/o. For example, 

```
# example codes for asynchronized evaluating
```






