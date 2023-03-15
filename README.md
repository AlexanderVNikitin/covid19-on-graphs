# covid19-on-graphs

This repo contains datasets for spatio-temporal prediction of COVID-19 distribution over the US. The US is represented as a graph where the nodes are associated with states, and edges represent the adjacency of the states. 

## How to use it?
1. Download raw data from the NY times using [this link] and put it to `./data`.
2. Install dependencies: 
```python
pip install networkx==2.8.8 pandas==1.3.5
```
3. Use `datasets.covid_adjacencies_graph_dataset()` to get graph and temporal data.
```python
import datasets
graph, temp_data = datasets.covid_adjacencies_graph_dataset()
```
4. Enjoy your experiments!


## Format
### Graph
A graph is stored as `nx.Graph` object. Read more about it in [networkx documentation](https://networkx.org/documentation/stable/reference/introduction.html#graphs).

### Temporal data
The data are aggregated weekly and in the following format:
```python
temp_data[date][state] = {
    "deaths": INT, # The number of deaths during the week
    "cases": INT,  # The number of cases during the week
    "deaths_normalized": FLOAT,  # The number of deaths normalized by the state population
    "cases_normalized": FLOAT,   # The number of cases normalized by the state population
}
```