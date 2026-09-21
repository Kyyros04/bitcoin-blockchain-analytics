# Bitcoin Miner Deanonimization & Blockchain Analytics

A comprehensive data engineering and cyber-forensics tool designed to analyze the early Bitcoin blockchain (Genesis block to block 214,562), deanonymize mining pool rewards, and perform recursive taint analysis on transactional flows. 

Developed as a final project for the **Web Scraping & Data Analysis Laboratory** (A.Y. 2023/24).

---

## Core Features & Technical Stack

The architecture is divided into three analytical pipelines combining high-performance data manipulation, dynamic web scraping, and graph theory:

### 1. Blockchain Congestion & Fee Analysis (`Pandas` & `Matplotlib`)
* **Large-Scale Data Ingestion:** Processes highly dense relational tracking data across millions of rows from underlying blockchain transaction logs (`transactions.csv`, `inputs.csv`, `outputs.csv`, `mapping.csv`).
* **Dynamic Content Sizing:** Implements low-level sizing estimation formulas (\(Size = InputSize \times N_{in} + OutputSize \times N_{out} + ScriptSize\)) to correlate transactional network congestion against market fee behaviors.
* **Historical Script Auditing:** Tracks historical usage shifts in standardized Bitcoin script configurations across early protocol epochs.

### 2. Automated Mining Pool Deanonimization (`Selenium WebDriver`)
* **Dynamic Crawler Execution:** Implements an automated browser pipeline using ChromeDriverManager to parse asynchronous DOM tables on `WalletExplorer.com`.
* **Anti-Bot Evacuation Tactics:** Utilizes dynamic, randomized waiting intervals (`random.uniform(2, 5)`) and experimental browser option profiles (cookie handling) to simulate human browsing habits and mitigate server throttling.
* **Target Mapping:** Cross-references crawled endpoints to identify ownership distributions among dominant historical mining clusters (*DeepBit*, *Eligius*, *BTC Guild*, *BitMinter*), segregating outliers into custom data classifications.

### 3. Recursive Taint Analysis & Network Science (`NetworkX`)
* **Recursive Flow Tracking:** Executes a depth-constrained recursive algorithm (`f_rec`) to programmatically track the downstream movement of newly minted coinbase rewards over \(K\) operational transactional hops.
* **Graph Modeling:** Populates an oriented directed graph (`nx.DiGraph`) modeling address-to-address interactions.
* **Topological Metrics:** Calculates structural graph behaviors including average clustering coefficients and degree distributions to evaluate local connection densities and transaction flow resistance.

---

## Theoretical Findings & Visualization Sample

| Metric | Analysis Value | Network Consequence |
| :--- | :--- | :--- |
| **Avg. Clustering Coefficient** | ~0.229 (23%) | Low local density; indicates linear/daisy-chained coin split streams rather than tight circular clusters. |
| **Node Degree Distribution** | Uniform (1 to 4) | Absence of dominant central structural hubs; demonstrates structural network resiliency during early transaction history. |
| **2012 Halving Correlation** | Verified Epoch Split | Captures the strict block reward halving mechanism from 50 BTC down to 25 BTC while block frequencies scaled. |

---

## Prerequisites & Installation

### Core Libraries
The project requires Python 3.8+ along with the following data and automation frameworks:
```bash
pip install pandas numpy selenium webdriver-manager networkx matplotlib seaborn
```

### Execution Flow
1. Place the required blockchain `.csv` data structures inside a localized `Dataset/` folder directory.
2. Launch the master execution framework:
```bash
python main_analysis.py
```

---

## 📄 License
This project is licensed under the **MIT License** - see the `LICENSE` file for details.
