# CS410_Project_Biomedical Concept Normalization


Search the concept based on the given entity name.

## Overview

This repository contains the implementation of two methods for biomedical concept normalization. It is a tool to link the biomedical entity mentions in the text to a concept identifier in a controlled vocabulary. The two methods we implemented are (1) dictionary look-up, (2) pairwise learning to rank. We tested our method on a BioCreative V CDR corpus and used Medical Subject Headings (MeSH) 2018 as the concept ontology. Biomedical concept normalization can group synonym entity mentions together and produce a more structured output for downstream applications, such as relation extraction and knowledge base completion.



## Implementation
Two methods are developed to search for the concept of the corresponding entity. The first method is dictionary look up. The second is pair-wise learning to rank. For first method, four dictionaries have been built from the raw data to search for concept of entity. In this method, corresponding concept would be returned based on the dictionary look up. For the second method, we used pair-wise learning to ranking method. We firstly collect the corpus from raw data sets and express the text features by using bag-of-words. All the words from the source data sets were put together to get the corpus. After this, we got 264854 feature dimensions, we used "TruncatedSVD" package from SKlearn to reduce the dimension for our feature vectors. Then, we trained our model using CVXPY package, we simutaneously trained three models with 25, 100, 1000 negative sampled instances. We got the model from 25 nagetive sampled instances in around 50 hours.  

## Usage
1. The packages required for running the code are listed in the "required_package.txt ", make sure to install the package before running the code. 
2. Before running the code, make sure the files in the "required_file.txt" have been put in the Project directory. All the large files that cannot be pushed onto github have been uploaded in the google drive. MAKE SURE to follow the link in "required_file.txt" to access the large files and download them to the working directory before running the code. The large files are the intermediate result from the code, two of them requires almost one week to run. Therefore, we save them into txt file in order for your testing the code.

For dictionary look up method method:

3. Select entity from "List of entity.txt" to search for the corresponding concept.
4. To run the "dictionary look up" method, under the Project folder, run the following command in Terminal, and follow the instruction in API, the result would be returned in terminal
```
python Dictionary.py
```

5. When running Dictionary.py, the default function is API() funtion, you can also open the Dictionary.py file and scroll down to the bottom of the file and uncomment other funtions and run the above commend line to get the precision, recall or F1 for all the data sets.

For pair-wise learning to rank method:

3. open the pair_wise_learning2rank.py file with a text editor, scroll down to the bottom of the file, uncomment the funtion that you want to run. There are detailed explanation above each function. It is worth pointing out that "get_entire_corpus_counts()" function returns the all data records as TF-IDF vector in our corpus; "dense()" function returns the feature vectors for all the data records after dimension reduction; "optimization()" function returns the trained model.
4. In the working directory, run the following command in the terminal
```
python pair_wise_learning2rank.py 
```


## Contributing
All the team members contributed equallu for the project.


