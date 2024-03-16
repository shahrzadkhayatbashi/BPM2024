# Material for the research paper submitted to BPM 2024
<!-- This part explains the paper briefly-->

In the paper **Transforming Object-Centric Event Logs to Temporal Event Knowledge Graphs** we introduce and formalize the concept of Temporal Event Knowledge Graphs (tEKGs), which are designed to record object-centric event data. This approach facilitates the tracking of changes in entity attributes over time. We implemented the transformation tool in Python and used three publicly available log files presented in OCEL 2.0 to transform into the tEKG format. We developed the transformation tool in three modes: batch import, live import, and hybrid mode. All three modes of the transformation tool are compared in terms of time taken for conducting the transformation. This repository provides material for this paper, including the source code for transforming OCEL 2.0 to tEKG, a running example test file, and experiment results.

<!-- This part explains OCEL 2.0 datasets-->

## Step 1. Getting the datasets
In this paper, we used three OCEL 2.0 data sets, which are all publicly available. In the links below, you can download each of theese files. 

**1.** **[Container Logistics Object-centric Event Log](https://zenodo.org/records/8428084)**: This is an artificial event log according to the OCEL 2.0 Standard, simulated using CPN-Tools.
**2.** **[Order Management Object-centric Event Log](https://zenodo.org/records/8428112)**: This is a simulation of an extension of the order management log in the former OCEL standard.

**3.** **[Procure-To-Payment (P2P) Object-centric Event Log](https://zenodo.org/records/8412920)**: This simulation extensively uses genuine SAP transactions and object types to offer a realistic representation of the P2P process.

Once you have download all the datasets, you can place them in the directory **[ocel2](./ocel2)**. Additionally, we have provided an OCEL 2.0 file as a running example that we used in the paper, named **[runningExample-course.jsonocel](./ocel2/runningExample-course.jsonocel)**.


## Step 2. Setting Up

 The transformation tool is developed in three modes of batch, live, abd hybrid in **[Python 3.11.8](https://www.python.org/downloads/release/python-3118/)**. To use this tool, you need to take the following steps:
 
**1.** Make sure you have **installed** Python on your computer.


**2.** **install all the packages**, which are available in **requirements.txt**. You can install all the packages using the following command:

```bash
pip install -r requirements.txt
``` 
 **3.** Once you installed all the packages, lunch the **jupyter lab** using the following command:

 ```bash
 jupyter lab
 ```


## Step 3. Transformation

Once you lunch the jupyter lab, you can see there are three python notebooks, namely: **[import batch.ipynb](./import%20batch.ipynb)**, **[live import.ipynb](./import%20live.ipynb)**, and **[hybrid import.ipynb](import%20hybrid.ipynb)**. 

**- [import batch.ipynb](./import%20batch.ipynb)** notebook is a tool which generates nodes and edges as distinct CSV files, which then can be imported into Neo4j.

**- [live import.ipynb](./import%20live.ipynb)** notebook is a tool which creates tEKGs in real-time using a Cypher query language.

**- [hybrid import.ipynb](./import%20hybrid.ipynb)** nootebook is a combined approach of batch and live mode.

Depending on the mode you wish to use for the transformation, open the corresponding notebook. For instance, if you choose to execute the batch mode tool, open the **[import batch.ipynb](./import%20batch.ipynb)** notebook. Before running any cells, in the setup cell of the notebook, specify the experiment_name. Assuming you want to transform the file **[runningExample-course.jsonocel](./ocel2/runningExample-course.jsonocel)** from the **[ocel2](./ocel2/)** directory, you need to set the experiment_name as follows:


 ```Python
experiment_name = 'runningExample-course'
 ```

Once **[import batch.ipynb](./import%20batch.ipynb)** finished, some CSV files are generated in the **[export](./export/)** directory, which you can load them into Neo4j as instructed in this **[link](https://neo4j.com/docs/operations-manual/current/tools/neo4j-admin/neo4j-admin-import/)**.

For executing **[live import.ipynb](./import%20live.ipynb)** and **[hybrid-import.ipynb](./import%20hybrid.ipynb)**, make sure Neo4j is up before running the code. For setting up Neo4j, you can check the **[documentation](https://neo4j.com/docs/operations-manual/current/docker/)**. Additinally, it is important to note that, while creating a docker image, you can utilize the usage of memory. For configuration, you can check the instructions provided in the **[documentation](https://neo4j.com/docs/operations-manual/current/performance/memory-configuration/)**.



 ## 3. Evaluation
 As an evaluation for the implemented tools, we compared the running time for transformation of OCEL 2.0 log to tEKG for each of the modes and created a table matrix, which is demonstrated in the evaluation section of the paper. The experiment results can be found in the directory of **[experiments](./experiments/)**. As an instance, **[batch_runningExample-course.json](./experiments/batch_runningExample-course.json)** is the result of the experiment for the running example indicating time for transforming and importing OCEL 2.0 log file into tEKG for **[runningExample-course.jsonocel](./ocel2/runningExample-course.jsonocel)**. 



