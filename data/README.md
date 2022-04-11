
# Data Processing

When we struggle to build the world's best model, 
a correct, consistent data processing pipeline should never be ignored.
Handling real-world datasets usually makes our hands dirty, 
thus a clear, easy-to-debug procedure can greatly reduce the risk 
of getting a wrong dataset.


## Data Persistency

We suggest dividing a single data processing pipeline into 
managable and reusable steps.
All intermediate results can be saved and reviewed for debugging.
We concrete the procedure in the following example, 

```
data
├── dataset-name
│   ├── 00-raw
│   │   └── change_encoding.py
│   ├── 01-unicode
│   │   └── wordseg.py
│   └── 02-wordsegemented
└── README.md

```

- each dataset has one directory (`dataset-name`)
- directory `00-raw` contains the raw dataset without any preprocessing.
- `01-unicode` contains the intermediate dataset after the first preprocessing
 step (changing the encoding). 
 The job is done by calling `change_encoding.py` script in `00-raw`.
- `02-wordsegmented` contains the intermediate dataset after the second preprocessing 
 step (segmenting sentences into word sequences using `01-unicode\wordseg.py`) 


The idea is to keep intermediate results accessible for debugging the data 
processing pipeline.
How to split the pipeline depends on the data
(e.g., one may prefer merging `01-unicode` and `02-wordsegmented`
into a single step). 
In general,
we would recommend placing a new split if

- third party tools are included, 
- extracting new features
- special editing of datasets

> Keeping preprocessing and postprocessing steps clear.

## Single Input Format

Our model should handle datasets with different original formats.
The principle here is 

> Separating data preparation with model source files.

Therefore, we need a single input format, and the final 
output of the above data processing pipeline should be in that format.

## Tips

- popular input formats including column files 
(e.g., conll format for sequential labeling, parsing),
json (e.g., information extraction, event detection)
- (TODO, we can build a script hub so that preprocessing scripts could be shared.)
