# LinkedIn Social Network Analysis: Exploring Professional Mobility and Cross-Functional Roles

![Python](https://img.shields.io/badge/Python-3.8%2B-blue)
![NetworkX](https://img.shields.io/badge/NetworkX-Graph_Analysis-orange)
![Pandas](https://img.shields.io/badge/Pandas-Data_Manipulation-150458)
![Status](https://img.shields.io/badge/Status-Completed-success)

## 📌 Project Overview
This project performs an advanced Social Network Analysis (SNA) on a real-world professional network (exported from LinkedIn). 

Analyzing personal social media data often results in a simplistic "Ego Network" (where the user is the center and all other nodes are isolated). To solve this, this project utilizes a **Bipartite Projection methodology**. By mapping individuals to their employers and projecting that bipartite graph into a **Position-to-Position** network, we can mathematically analyze how different job titles interact, which roles act as organizational "bridges", and how professional clusters evolve over time.

## 🎯 Objectives
* **Avoid the Ego Network Trap:** Transform standard connection data into a sparse, structurally significant network of job titles.
* **Identify Hubs and Bridges:** Use Centrality measures to find universally common roles vs. cross-functional gatekeepers.
* **Detect Functional Communities:** Apply the Louvain method to see if distinct professional sectors naturally cluster together.
* **Analyze Scale-Free Properties:** Compare empirical degree distributions to theoretical models (Erdős-Rényi and Barabási-Albert).
* **Track Temporal Evolution:** Analyze how network density and clustering coefficients shift quarter-over-quarter as the professional network matures.

## 🔬 Methodology: Bipartite Projection
1. **Data Source:** A raw `.csv` export of LinkedIn connections (`First Name`, `Last Name`, `Company`, `Position`, `Connected On`).
2. **The Setup:** A bipartite graph is constructed linking **People** to **Companies**.
3. **The Projection:** The graph is projected onto **Positions**. Two job titles (e.g., "Data Analyst" and "Software Engineer") only form an edge connecting them *if* the dataset contains people holding both specific titles at the exact same company. 

## 📊 Key Analyses Performed
* **Network Topology:** Calculation of Network Density, Average Shortest Path Length, and Size of the Giant Component.
* **Centrality Metrics:**
  * *Degree Centrality:* Identifying highly collaborative "Hubs" (e.g., HR, General Management).
  * *Betweenness Centrality:* Identifying "Bridges" that connect siloed departments (e.g., Data Analysts, Project Managers).
* **Assortative Mixing:** Measuring degree assortativity to determine core-periphery structures.
* **Community Detection:** Utilizing the Louvain heuristic for modularity optimization to detect isolated functional groups.
* **Theoretical Benchmarking:** Side-by-side visual and mathematical comparison of the real network against generated ER (Random) and BA (Preferential Attachment) random graphs.
* **Temporal Dynamics:** Cumulative quarter-over-quarter time-series tracking of network growth and clustering.

## 💻 Technologies Used
* **Python** (Core language)
* **NetworkX** (Graph construction, algorithms, and metric calculation)
* **Pandas** (Data wrangling, temporal grouping, and text cleaning)
* **Matplotlib & Seaborn** (Data visualization and degree distribution plotting)
* **NetworkX Community** (Louvain modularity)

## 🚀 How to Run the Project

### 1. Clone the repository
git clone https://github.com/VinayAttri10/LinkedIn-Social-Network-Analysis.git

### 2. Install dependencies
It is recommended to use a virtual environment.
pip install pandas networkx matplotlib seaborn numpy

### 3. Add your data
Request your connection data from LinkedIn (Settings & Privacy -> Data Privacy -> Get a copy of your data -> Connections).
Save the resulting file as Connections.csv in the root directory. (Note: The script automatically handles the standard 3 rows of notes LinkedIn places at the top of the CSV).

### 4. Run the Jupyter Notebook
jupyter notebook Project_Confirmation.ipynb

📝 Findings Summary
Scale-Free Structure: The network's degree distribution heavily follows a power-law curve, proving it is a scale-free network governed by preferential attachment, completely distinct from a random Poisson distribution.

Small-World Phenomenon: Despite low density, the average path length between any two job titles across the giant component is incredibly short, accompanied by a remarkably high clustering coefficient.

Cross-Functional Bridges: Specific roles (such as Data Analysts) score disproportionately high in Betweenness Centrality compared to their Degree Centrality, proving their structural necessity in connecting distinct business units.

🤝 Contributing
Contributions, issues, and feature requests are welcome! Feel free to check the issues page.

📄 License
This project is MIT licensed.
