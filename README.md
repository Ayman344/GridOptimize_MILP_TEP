Strategic Grid Reinforcement: A MILP Optimization Approach on SciGRID
This repository contains the data, analysis scripts, and optimization models for the research paper:
“Optimal Grid Reinforcement Planning using DC Power Flow and MILP: A SciGRID Network Case Study”

This project presents a comprehensive, step-by-step methodology for identifying and mitigating congestion in power transmission networks through optimal line reinforcement. It demonstrates how large-scale data analysis can be effectively combined with targeted mathematical optimization for transmission expansion planning (TEP).

📊 Overview
Starting with open-source European SciGRID network data, the workflow proceeds as follows:

Perform DC Power Flow (DCPF) analysis on the full network to identify overloaded lines.

Extract a representative 30-node subset of the largest connected component (LCC) using a breadth-first search algorithm.

Solve a Mixed-Integer Linear Programming (MILP) model to determine cost-effective reinforcement strategies for the subset under a budget constraint.

This project serves as both a practical case study and a reusable framework for scalable grid reinforcement planning.

🗂️ Repository Structure
1. Data (Any questions about the data I can answer)
/data/raw/ — Original input Data

links_de_power_150601.csv
vertices_de_power_150601.csv

Data after basic processing(eg. Imputing missing values, Handling multiple data in a single cell(voltage) and dropping columns etc.)- 

nodes.csv — Node data from SciGRID (substations).

edges3.csv — Edge data from SciGRID (line parameters).

2. Analysis and Modeling Scripts
/src/ — Source code:

Power_Flow_Problem.ipynb — Python notebook for data processing, per-unit conversion, LCC extraction, DCPF analysis, subset selection.

gams_milp_model.gms — GAMS model implementing the MILP optimization, solved with CPLEX.

3. Generated Data and Results
/output_data/ — Intermediate and final results:

LCC Analysis:

all_edges_with_pu_values.csv

lcc_nodes_complete_data.csv

network_flows_results.csv

thermal_violations_details.csv

active_network_lcc.graphml

GAMS Inputs:

gams_input_nodes.csv

gams_input_edges.csv

gams_subset_data_block_*.txt

Optimization Results:

pyomo_milp_results.csv (for comparison)

4. Figures
/figures/ — Key visualizations:

active_network_lcc.png — LCC with overloads.

optimization_results_comparison_chart.png — Reinforcement impact.

Directed_Scigrid_Network.png — Optional directed graph visualization.

🔍 Methodology Workflow
Data Processing:
Convert SciGRID data to per-unit system (100 MVA base), prepare network parameters.

LCC Analysis:
Identify the 469-node LCC, apply a 10,000 MW synthetic scenario, perform DCPF, detect 225 overloaded lines.

Subset Creation:
Extract a 30-node, 37-line connected subset, compute reinforcement costs.

Optimization:
Solve MILP on the subset to minimize overload while respecting budget constraints, resulting in optimal reinforcement of 13 lines.

🚀 How to Use
Explore & Reproduce:
Run Power_Flow_Problem.ipynb for data processing and analysis.
Run gams_milp_model.gms in GAMS to replicate optimization results.

Analyze Results:
Output data and figures are available for further inspection and use.

📖 Citation
If you use this repository, please cite the accompanying paper:

A. S. Akash and M. S. Osman,
“Strategic Grid Reinforcement: A MILP Optimization Approach on SciGRID,”
in Proc. Interdisciplinary Conference on Electrics and Computer (INTCEC 2025), Chicago, USA, Sep. 2025.
