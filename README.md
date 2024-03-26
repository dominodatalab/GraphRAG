# Graph RAG

## About this project

This project shows three ways in which LLMs can be used to interact with graphs using a graph database (Neo4j Aura).
* The first way is to create a graph, use few shot learning to teach an LLM to generate (Cypher) queries and get results back.
* The second way is to use an LLM to construct a graph and then use another LLM to generate the (Cypher) queries. 
* The third method uses langchain and is a way to perform hybrid RAG. In addition to constructing the graph using an LLM, text is stored in "Document" nodes and an embedding property is computed from the "text" field of the "Document" node and added as a property. An "__Entity"  label is also added to the node if its relevant. Once a query submits a query, entities are extracted and matched and a neighbourhood of nodes is extracted. The relationship information is then combined with semantic search information from the "Document" nodes to provide a final answer.

For the first approach the data and graph schema from [here](https://www.kaggle.com/code/yclaudel/analyze-netflix-data-using-graphs-neo4j) was used. For the second and third approaches, code and infographics is available at https://blog.langchain.dev/enhancing-rag-based-applications-accuracy-by-constructing-and-leveraging-knowledge-graphs/

## License
This template is licensed under Apache 2.0 and contains the following components: 
* langchain 0.1.8 [MIT License (MIT)](https://github.com/langchain-ai/langchain/blob/34284c25d4de4352bede97724fc1ef0bf10460bb/LICENSE)
* langchain-openai [MIT License (MIT)](https://github.com/langchain-ai/langchain/blob/34284c25d4de4352bede97724fc1ef0bf10460bb/LICENSE)
* langchain-experimental [MIT License (MIT)](https://github.com/langchain-ai/langchain/blob/34284c25d4de4352bede97724fc1ef0bf10460bb/LICENSE)

* The assets available in this project are:

*1_1_create_kg.ipynb* - 
*1_2_query_kg.ipynb* -
*2_construct_graph_from_llm.ipynb* -
*3_langchain_hybrid_rag.ipynb* -
*neo4j_query_ft_examples.ipynb* -

* ## Set up instructions

This project requires the following [compute environments](https://docs.dominodatalab.com/en/latest/user_guide/f51038/environments/) to be present. Please ensure the "Automatically make compatible with Domino" checkbox is selected while creating the environment.

### Environment Requirements

**Environment Base**

***base image :*** `5.9 Domino Standard Environment - ubuntu20-py3.9-r4.3`

Any DSE with Python 3.9 will also work

***Dockerfile instructions***
```
RUN pip install neo4j==5.16.0 langchain-community==0.0.14 openai==1.9.0 langchain==0.1.2 langchain-openai==0.0.3 pypdf==4.1.0 wikipedia==1.4.0
```
***Pluggable Workspace Tools** 
```
jupyterlab:
  title: "JupyterLab"
  iconUrl: "/assets/images/workspace-logos/jupyterlab.svg"
  start: [  "/opt/domino/workspaces/jupyterlab/start" ]
  httpProxy:
    internalPath: "/{{ownerUsername}}/{{projectName}}/{{sessionPathComponent}}/{{runId}}/{{#if pathToOpen}}tree/{{pathToOpen}}{{/if}}"
    port: 8888
    rewrite: false
    requireSubdomain: false
```
Please change the value in `start` according to your Domino version.

### Hardware Requirements

This project will run on any CPU and RAM (> 8GB prefered). A hardware tier such as a `small` or `small-k8s` on Domino will work well too for this project
