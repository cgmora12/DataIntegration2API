# AG + integration: Automatic API Generator to Access Integrated Open Data

This is an automatic API generator from open data resources that integrates them.

In order to solve the problem of accessing and reusing open data, our approach automatically generates Web APIs that access unionable and joinable tabular open data in an integrated manner. Once unionable and joinable open data is detected by using a table similarity measure based on word embeddings, the APIfication process creates APIs for accessing them as a unique dataset.

## Getting Started

First, to obtain similarity data between different CSV files, use the python program in the similarity folder. Then, use the tableunion.jar file in order generate APIs from CSV files and similarity data. The Python table similarity module can be run as a standalone program to obtain the similarity between a set of tables, regardless of their later use for API generation.


### Prerequisites

Programs needed

```
Python
NodeJS
Java
```

The following Python libraries are required:
- numpy (https://pypi.org/project/numpy/)
- python-Levenshtein (https://pypi.org/project/python-Levenshtein/)
- scipy (https://pypi.org/project/scipy/)
- gensim (https://pypi.org/project/gensim/)

The pre-trained models are available in the following links:
- fastText: https://fasttext.cc/docs/en/english-vectors.html
- Google word2vec: https://code.google.com/archive/p/word2vec/

The WikiTables files to build the task-specific model are available here: http://websail-fe.cs.northwestern.edu/TabEL/

### Installing and Deployment

Download the python program and the java program to start using the tool. 

First, be sure that pip package-management system is present in your system. Otherwise install it following this instructions: https://pip.pypa.io/en/stable/installing/

Download the table_similarity module and run the following commands:
- To install the libraries required: $ pip install -r requirements.txt
- To install the table_similarity module: $ python setup.py install

### Configuring and running the similarity module

The module reads the parameters from a configuration file (“config.ini”). This file contains four sections to define the model and alpha values (“Setup”), the directories where the models and input tables are stored (“Directories”), the output file with the similarity values (“Files”) and the filenames of the models (“Models”). This is an example of “config.ini”:

```
[Setup] 
model_names = fasttext
model_contents = fasttext
alpha = 0.5

[Directories]
models = ./models
tables = ./tables

[Files]
output = ./similarity_data.json

[Models]
wikitables_names = wikitables_names.bin
wikitables_contents = wikitables_contents.bin
google = GoogleNews-vectors-negative300.bin
fasttext = wiki-news-300d-1M.vec
```

This example uses fastText for both column names (“model_names”) and content (“model_content”). The parameter alpha is set to “0.5” and the results are stored in a file named “similarity.json”.

To run the program, import the table_similarity module in your code or run from the command line:
```
$ python table_similarity.py
```

### Running the integration and API generation program

Once calculated the similarity, in order to perform the integration and generate the corresponding Web API run the Java tool (tableunion.jar) as follows:
```
java -jar tableunion.jar similarity_data.json operation threshold api
```

The operation parameter is optional and can be union or join, depending on user preferences.

The threshold parameter is optional and must be a number between 0 and 1 (default is 0.75).

The api parameter is optional and is used to create or not a web api to access integrated data.


## Example datasets

In order to test our approach, we have selected different datasets:

- Salmonella tests (https://data.gov.uk/dataset/7b7f30d7-6226-4a49-a1ca-b2ab405db2ce/salmonella-testing-programme)
- Population (https://datos.alcobendas.org/dataset/poblacion-empadronados-totales-y-grupos-de-edad-y-sexo-historico)
- Travel data (https://data.gov.uk/dataset/b6b63ea3-c7be-4f60-81f5-3c8f5236f5f7/travel-data-transparency-agenda-and-foi-request)
- Biodiversity (https://catalog.data.gov/dataset/biodiversity-by-county-distribution-of-animals-plants-and-natural-communities)
- Street lights (https://data.gov.uk/dataset/3b1b594f-e1a3-495b-a6c0-221fff9d1ffd/street-lights)
- International payments (https://open.canada.ca/data/en/dataset/823899ab-3cca-4484-a420-13bf0d0d0226)
- Traffic state (https://datos.gob.es/es/catalogo/l01080193-informacion-del-estado-del-transito-en-los-tramos-de-la-ciudad-de-barcelona)
- Voter data (https://catalog.data.gov/dataset/voter-history-data)
- Wholesale trade sales (https://open.canada.ca/data/en/dataset/45d747d8-8abf-49d9-a76c-84c01156c04b)
- Employee earnings (https://open.canada.ca/data/en/dataset/d4c86aaf-6d6b-4da8-a41e-6f96dbec982e)


## Authors

* **César González Mora** 
* **David Tomás** 
* **Irene Garrigós** 
* **Jose Zubcoff** 
* **Jose-Norberto Mazón** 
