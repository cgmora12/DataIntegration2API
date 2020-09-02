# AG + integration: Automatic API Generator to Access Integrated Open Data

This is an automatic API generator from open data resources that integrates them.

In order to solve the problem of accessing and reusing open data, our approach automatically generates Web APIs that access unionable and joinable tabular open data in an integrated manner. Once unionable and joinable open data is detected by using a table similarity measure based on word embeddings, the APIfication process creates APIs for accessing them as a unique dataset.

## Getting Started

First, to obtain similarity data between different CSV files, use the python program in the similarity folder. Then, use the tableunion.jar file in order generate APIs from CSV files and similarity data.


### Prerequisites

Programs needed

```
Python
NodeJS
Java
```

The following Python libraries are required:

numpy (https://pypi.org/project/numpy/)
python-Levenshtein (https://pypi.org/project/python-Levenshtein/)
scipy (https://pypi.org/project/scipy/)
gensim (https://pypi.org/project/gensim/)

The pre-trained models are available in the following links:

fastText: https://fasttext.cc/docs/en/english-vectors.html
Google word2vec: https://code.google.com/archive/p/word2vec/

The WikiTables files to build the task-specific model are available here: http://websail-fe.cs.northwestern.edu/TabEL/

### Installing and Deployment

Download the python program and the java program to start using the tool.
First, be sure that pip package-management system is present in your system. Otherwise install it following this instructions: https://pip.pypa.io/en/stable/installing/

Download the table_similarity module and run the following commands:

To install the libraries required: $ pip install -r requirements.txt

To install the table_similarity module: $ python setup.py install

### Configuring and running the module

The module reads the parameters from a configuration file (“config.ini”). This file contains four sections to define the model and alpha values (“Setup”), the directories where the models and input tables are stored (“Directories”), the output file with the similarity values (“Files”) and the filenames of the models (“Models”). This is an example of “config.ini”:

[Setup]
model_names = fasttext
model_contents = fasttext
alpha = 0.5

[Directories]
models = ./models
tables = ./tables

[Files]
output = ./similarity.json

[Models]
wikitables_names = wikitables_names.bin
wikitables_contents = wikitables_contents.bin
google = GoogleNews-vectors-negative300.bin
fasttext = wiki-news-300d-1M.vec

This example uses fastText for both column names (“model_names”) and content (“model_content”). The parameter alpha is set to “0.5” and the results are stored in a file named “similarity.json”.

To run the program, import the table_similarity module in your code or run from the command line:

$ python table_similarity.py

### Running the integration and API generation program

Once calculated the similarity, in order to perform the integration and generate the corresponding Web API run the Java tool (tableunion.jar) as follows:
```
java -jar tableunion.jar similarity_data.json operation threshold api
```

The operation parameter is optional and can be union or join, depending on user preferences.
The threshold parameter is optional and must be a number between 0 and 1 (default is 0.75).
The api parameter is optional and is used to create or not a web api to access integrated data.


## Authors

* **César González Mora** 
* **David Tomás** 
* **Irene Garrigós** 
* **Jose Zubcoff** 
* **Jose-Norberto Mazón** 