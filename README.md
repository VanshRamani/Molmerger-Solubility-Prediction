# MolMerger Solubility Prediction

![MolMerger Pipeline](https://i.ibb.co/wFKR7szF/image.png)
## Overview
This repository contains the implementation of *MolMerger*, a Graph Neural Network (GNN)-based approach for predicting solubility in diverse solvents by incorporating explicit solute-solvent interactions. The method is described in the paper:

> **Graph Neural Networks for Predicting Solubility in Diverse Solvents Using MolMerger Incorporating Solute–Solvent Interactions**  
> *Vansh Ramani and Tarak Karmakar*  
> Journal of Chemical Theory and Computation, 2024, 20 (15), 6549-6558  
> DOI: [10.1021/acs.jctc.4c00382](https://doi.org/10.1021/acs.jctc.4c00382)

The *MolMerger* approach captures solute-solvent interactions using Gasteiger charges to construct molecular graphs, which are then processed by a graph neural network to predict LogS values.

## Repository Structure
```
├── MolMergerModel.ipynb   # Jupyter Notebook with implementation and usage details
├── FinalTrainedModel.pt   # Pretrained model for inference
├── trainset.csv           # Training dataset
├── EvalData.csv           # Evaluation dataset
├── Results.csv            # Model predictions
├── README.md              # This file
```

## Getting Started
All necessary steps to run the model, including data preprocessing, model training, and inference, are provided in **MolMergerModel.ipynb**. Please follow the instructions in the notebook to reproduce the results.

## Dataset
The dataset used in this study was compiled from multiple sources, including **BigSolDB**, **BNNLabs Solubility**, and **ESOL**. The dataset consists of **6,975 solute-solvent pairs**, carefully curated to ensure high-quality data. The dataset was split into:
- **Train-Test Set** (5,493 pairs): Used for training and validation.
- **Robust Evaluation Set** (1,482 pairs): Used to assess the generalization ability of the model, ensuring that predictions are reliable for unseen solvents.

The dataset includes a variety of solvents, both aqueous and organic, covering a broad range of solubility conditions. The features used include molecular structure representations, Gasteiger charges, and solute-solvent interaction descriptors.

## Model Architecture
The *MolMerger* model leverages **AttentiveFP**, a graph attention-based neural network optimized for molecular graph processing. The key components include:
- **Graph Construction:** Molecules are represented as graphs, where atoms form the nodes, and chemical bonds form the edges.
- **Feature Encoding:** Atom-level features (such as atomic number, hybridization, charge) and bond-level features (such as bond type and conjugation) are incorporated.
- **Attention Mechanism:** The model applies attention-based message passing to highlight critical interactions within solute-solvent pairs.
- **Prediction Layer:** The final embedding is processed through fully connected layers to predict **LogS (log solubility)** values.

## Results
The *MolMerger* model demonstrated **state-of-the-art performance** in predicting solubility across diverse solvent environments. Key findings include:
- **Test Set Performance:** The model achieved an **R² score of 0.767** and a **Mean Absolute Error (MAE) of 0.78**, showing strong predictive accuracy.
- **Robust Evaluation Performance:** Across 65 unseen solvents, the model maintained an **average MAE of 0.79**, with 46 solvents having an MAE below 1.0.
- **Comparison with Experimental Data:** Predictions for widely used pharmaceutical compounds, such as **paracetamol, alprazolam, and aspirin**, closely matched experimental solubility values.

### Sample Predictions
| Molecule   | Solvent  | Predicted LogS | Experimental LogS |
|------------|---------|----------------|-------------------|
| Paracetamol | Water  | -1.982         | -2.179            |
| Metformin  | Water  | -1.589         | -1.744            |
| Diazepam   | Methanol | -2.891         | -2.699            |
| Aspirin    | Water  | -3.177         | -2.699            |

## Citation
If you use this repository in your research, please cite:

```
@article{Ramani2024MolMerger,
  author = {Vansh Ramani and Tarak Karmakar},
  title = {Graph Neural Networks for Predicting Solubility in Diverse Solvents Using MolMerger Incorporating Solute–Solvent Interactions},
  journal = {Journal of Chemical Theory and Computation},
  year = {2024},
  volume = {20},
  number = {15},
  pages = {6549-6558},
  doi = {10.1021/acs.jctc.4c00382}
}
```

## License
This repository is for research purposes only. Please refer to the original paper for details on the methodology and usage rights.

## Contact
For any queries, please contact **Vansh Ramani** or **Tarak Karmakar** via their respective institutional affiliations.

