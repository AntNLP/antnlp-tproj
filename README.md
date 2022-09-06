# A Template of Organizing NLP/ML Projects 


We provide an example directory of NLP/ML projects filled with
data sets, source files, evaluation scripts, and model checkpoints.
The hierarchy has been practiced in our previous projects,
and it shows reasonable flexibility for the model development process
(e.g, tunning hyperparameters, stacking different model components, 
integrating third-party libraries while keeping the project separated).

## Overview

There are several principles we will follow,

> Keeping preprocessing and postprocessing steps clear.
>
> Separating data preparation with model source files.
>
> Separating evaluation scripts from model source files.
> 


The subdirectories are
- [data](data/) contains datasets, their preprocessing scripts, and intermediate results.
- [modules](modules) are basic blocks for building your model.
(encoders, decoders, our fancy modification of the Transformer).
- [models](models/) are glued modules which accomplish the NLP task.
- [configs](configs/) hosts configuration files.
- [eval](eval/) contains evaluation scripts.
- [util](util/) are helping tools.
- [ckpts](ckpts/) contains model checkpoints.
- [train.py](train.py) the training script.
- [run.py](run.py) the deploying script.



