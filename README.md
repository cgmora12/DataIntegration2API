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

### Installing and Deployment

Download the python program and the java program to start using the tool as follows:

Java Tool:
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