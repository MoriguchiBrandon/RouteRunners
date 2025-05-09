
# RouteRunners: Large-Scale Route Optimization

This project simulates and analyzes shortest pathfinding performance over randomly generated graphs using real-world distance data between cities. It supports Dijkstra's and A* algorithms and provides visual analysis tools for edge and city usage patterns.


## 🛠️ Setup

1. Upload `distance.csv` to your Google Drive under `RouteRunners/Large-Scale-Route-Optimization/`.
2. Mount Google Drive in your Colab notebook:
   ```python
   from google.colab import drive
   drive.mount('/content/drive')
   ```
3. Run the notebook to generate graphs, simulate routes, and analyze usage.

## 🔄 Core Workflow

1. **Graph Generation**: Random graphs are created from `distance.csv`, optionally excluding the direct edge between source and destination.
2. **Pathfinding**: A* and Dijkstra's algorithms compute shortest paths between selected cities.
3. **Simulation**: Run over hundreds of randomized graphs to test consistency and robustness.
4. **Analysis**:
   - Identify paths that fail (disconnected graphs).
   - Visualize edge/city usage via heatmaps and bar plots.
   - Compare performance and route differences between algorithms.

## 📊 Visualizations

- **Edge Heatmap**: How frequently each edge is used across all successful paths.
- **City Usage Heatmap**: Frequency of city appearances in shortest paths.
- **Failure Analysis**: Plots showing how graph connectivity impacts success rates.

## ✅ Features

- Support for directed and undirected graphs.
- Optional heuristic (coordinate-based) A* search.
- Edge and city frequency tracking.
- Path failure statistics and resilience analysis.
- Extensible structure for new algorithms or metrics.

## 📌 Requirements

- Python 3.x
- pandas, numpy, matplotlib, seaborn

## 📈 Example Usage

```python
generator = GraphGenerator(distances)
paths = generator.generate_random_graphs_and_paths(
    start='City_24',
    goal='City_47',
    num_graphs=300,
    exclude_direct_edge=True,
    directed=True
)

runner = RouteRunners(paths)
print("Number of failed paths:", runner.count_failed_paths())
edge_usage = runner.count_edge_usage()

viz = Visualizer(edge_counts=edge_usage)
viz.plot_edge_usage_heatmap()
viz.plot_city_usage_barplot(top_n=25)
```
