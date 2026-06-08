# Supply Chain Network Optimization

A Python project that finds the most optimal combination of factories and shipping routes across 5 countries using Linear Programming.

---

## Why I built this

I came across an article by **Samir Saci** on Towards Data Science that walked through how to use Python to optimize a global supply chain network. I used it as a learning project to understand how real-world operations research problems are modelled and solved with code.

Full credit and reference:
> Samir Saci — *Supply Chain Optimization with Python*
> https://towardsdatascience.com/supply-chain-optimization-with-python-23ae9b28fd0b

---

## The problem

A global manufacturing company operates factories in 5 countries ; USA, Germany, Japan, Brazil and India and sells to markets in those same 5 countries. The goal is to decide:

- Which factories to keep open (and at what capacity high or low)
- How many units to ship from each factory to each market

...all while minimizing total monthly cost, which includes fixed factory costs, variable production costs, and shipping costs.

---

## How the model works

The problem is set up as a **Mixed Integer Linear Program (MILP)** using Python. The solver finds the mathematically optimal answer; not just a good one, but the best possible one in under a second.

Two types of decision variables:
- `x` — how many units to ship from factory i to market j
- `y` — should factory i be open at all (0 = closed, 1 = open)

---

## Key result

Under the shipping crisis scenario (container costs × 5), the optimal solution costs **$92,981,000/month**. The model responded by reopening local factories in USA and Japan, showing that when shipping gets expensive enough, local production wins even at higher labour costs.

Open factories in the optimal solution:

| Factory | Capacity | Ships to |
|---|---|---|
| India | High | USA, India, Germany |
| Japan | High | Japan |
| USA | High | USA, Japan |
| Brazil | Low | Brazil |

---

## Libraries used

| Library | Purpose |
|---|---|
| `pandas` | Reading Excel data files, table operations |
| `pulp` | Building and solving the LP/MILP model |
| `matplotlib` | Generating all visualizations |
| `numpy` | Simulating demand variability across 50 cases |
| `os` | Managing file paths for saving outputs |

---

## Visualizations

I added few charts as well that are generated at the end of the notebook:

1. **Sankey chart** — shows production flow from each factory to each market, band width = volume
2. **Demand variability** — simulates how demand could fluctuate across 50 cases using normal distribution
3. **Factory heatmap** — shows which factories open or close across 50 simulated cases
4. **Combination donut** — shows which factory combination appears most often, identifying the most robust solution

---

## How to run

1. Clone this repo and make sure all 5 Excel files are in the same folder as the notebook
2. Install dependencies:
```
pip install pandas pulp matplotlib numpy openpyxl
```
3. Open `supply_chain_optimization.ipynb` and run all cells top to bottom

---

## Data files

| File | Contains |
|---|---|
| `variable_costs.xlsx` | Production cost per unit at each factory |
| `freight_costs.xlsx` | Shipping cost per container between locations |
| `fixed_cost.xlsx` | Monthly fixed cost to keep each factory open |
| `capacity.xlsx` | Max units each factory can produce per month |
| `demand.xlsx` | Monthly demand per market |

---

*Built while learning supply chain optimization and operations research with Python.*
