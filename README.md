# Network Science Toolkit

A small Python package containing reusable network science functions developed in my network science course.

## Installation

Clone the repository and install it with pip:

```bash
git clone https://github.com/jiaao-yu/network-science-toolkit.git
cd network-science-toolkit
python3 -m pip install .
```


## Functions

### `degree_distribution(G, number_of_bins=15, log_binning=True, density=True, directed=False)`

Calculates the degree distribution of a NetworkX graph.

Parameters:

- `G`: a NetworkX graph.
- `number_of_bins`: number of histogram bins.
- `log_binning`: use logarithmic bins when `True`.
- `density`: return probability density when `True`.
- `directed`: use `"in"` or `"out"` for a directed graph.

Returns:

- Bin locations and degree probabilities as NumPy arrays.

### `all_shortest_from(G, node_i)`

Uses breadth-first search to calculate the shortest-path distance from one source node to every node.

Parameters:

- `G`: a NetworkX graph.
- `node_i`: source node.

Returns:

- A dictionary in the form `{node: distance}`.
- Unreachable nodes have distance `-1`.

### `closeness_centrality_from_scratch(G)`

Calculates closeness centrality for every node. It also adjusts the result when the graph is disconnected.

Parameters:

- `G`: a NetworkX graph.

Returns:

- A dictionary in the form `{node: centrality}`.

### `eigenvector_centrality_from_scratch(G, max_iter=100, tol=1e-08)`

Calculates eigenvector centrality using power iteration.

Parameters:

- `G`: a NetworkX graph.
- `max_iter`: maximum number of iterations.
- `tol`: convergence tolerance.

Returns:

- A dictionary in the form `{node: centrality}`.

### `calculate_modularity(G, partition)`

Calculates the modularity of a graph partition.

Parameters:

- `G`: a weighted or unweighted NetworkX graph.
- `partition`: community membership represented as a dictionary, label list, or list of communities.

Returns:

- The modularity score as a float.

### `girvan_newman(H, output="dict")`

Detects communities by repeatedly removing the edge with the highest edge-betweenness centrality.

Parameters:

- `H`: a NetworkX graph.
- `output`: output format, which can be `"dict"`, `"list"`, or `"lists"`.

Returns:

- The partition with the highest modularity found by the algorithm.

## Example

```python
import networkx as nx
from network_toolkit import all_shortest_from

G = nx.path_graph(5)
distances = all_shortest_from(G, 0)

print(distances)
```

Expected output:

```text
{0: 0, 1: 1, 2: 2, 3: 3, 4: 4}
```

## Dependencies

- Python 3.9 or later
- NetworkX
- NumPy
