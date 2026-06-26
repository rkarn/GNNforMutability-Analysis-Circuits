## GNNs for Structural Manipulation on Circuit Netlists

This repository contains a topology-driven framework for structural manipulation surface analysis of gate-level netlists by defining a composite manipulability metric derived from path participation, k-core embedding, symmetry, and centrality. Modeling netlists as directed graphs, we formulate node-level regression to predict structural manipulability using graph neural networks (GNNs).

### Code Structure:
1.  The ISCAS85 and EPFL benchmark gate-level netlists (circuits) are available in the `verilog_benchmark_circuits` folder. You can obtain these netlists from `https://github.com/jpsety/verilog_benchmark_circuits`.
2.  The calculation of **structural manipulability M(v)** metric using several GNNs is performed in notebooks named `<GNN-type>_mutability_prediction.ipynb`. The notebook `gcn_mutability_prediction.ipynb` has parsing script that parses each netlist from `verilog_benchmark_circuits` folder and create graph data which is then used to calculate the `M(v)`. It then stored the graph dataset named `gnn_structural_netlist_dataset.pt` which are used in other `<GNN-type>_mutability_prediction.ipynb` notebookes. Ten GNN architectures are used in total:
    - GCN (Graph Convolutional Networks): `gcn_mutability_prediction.ipynb`
    - GraphSAGE (Graph SAmple and aggreGatE): `GraphSAGE_mutability_prediction.ipynb`
    - GIN (Graph Isomorphism Networks): `GIN_mutability_prediction.ipynb`
    - GAT (Graph Attention Networks): `GAT_mutability_prediction.ipynb`
    - MPNN (Message Passing Neural Networks): `MPPNP_mutability_prediction.ipynb`
    - APPNP (Approximate Personalized Propagation of Neural Predictions): `APPNP_mutability_prediction.ipynb`
    - g-U-Net (Graph U-Net): `GraphUNet_mutability_prediction.ipynb`
    - HetGNN (Heterogeneous Graph Neural Networks): `HetGNN_mutability_prediction.ipynb`
    - SGNN (Signed Graph Neural Networks): `SGNN_mutability_prediction.ipynb`
    - GTN (Graph Transformer Networks): `GTN_mutability_prediction.ipynb`
  3. The notebook `Some_analysis.ipynb` contains several analysis of `M(v)` that are part of the paper. They are:
     - Per-Circuit Spearman Correlation Analaysis 
     - Ablation Study on Structural Components of M(v)
     - Correlation with Circuit Structural Statistics
     - Robustness Across Design Styles and Circuit Sizes
  5. The notebook titled `Trojan_Injection.ipynb` contains the source code to inject three types of Trojan to each netlist of `verilog_benchmark_circuits` folder. The templates are obtained from Trusthub `https://trust-hub.org/`. THe generated netlist will be saved in `verilog_benchmark_circuits_Trojan` folder The Trojan names are:
     - ANDXOR
     - CounterMUX
     - FSMOR
  7. The notebook `M(v) on Trojanized Netlist.ipynb` contains the source code to calculate structural manipulation metric on netlist obtained from Trojan injection, i.e. from `verilog_benchmark_circuits_Trojan` folder.
  8. `reviewer's concern address.ipynb` contains the additional analyses performed in response to the journal reviewers' comments after the initial submission. Rather than modifying the primary experimental pipeline, this notebook reuses the preprocessed graph dataset to conduct supplementary experiments, including component-weight sensitivity analysis, comparison between the composite structural manipulability score and its individual structural components, and other reviewer-requested validation studies. It also generates the tables and figures incorporated into the revised manuscript, providing a reproducible record of all experiments added specifically to address the review process while leaving the original methodology and main results unchanged.

#### To start the experiment, please follow the order above.

### Results:
1.  Consolidated M(v) results for each GNN are available in the `consolidated_outcome.txt` file.
