# Interpretable Monocular Depth Estimation
Project 1: Neuron Selectivity for Efficient Monocular Depth Estimation

The project is to study the impact of neuron selectivity [1] on lightweight monocular depth estimation (MDE) models. We want to explore whether this interpretability strategy can also be effective on efficient MDE network, as it has been for deep MDE networks.

## Dataset

We use the **NYU Depth V2 dataset**, a collection of indoor scenes recorded by the RGB and the Depth cameras.

* **Dataset Link:** [https://www.kaggle.com/datasets/soumikrakshit/nyu-depth-v2](https://www.kaggle.com/datasets/soumikrakshit/nyu-depth-v2)
  
Note: The dataset is directly loaded within our notebook on Kaggle.

## Code Notebook

Our notebook implements:

* **METER-XXS Model:** A lightweight variant of the METER model.
* **Baseline Loss Function:** The original balanced loss function from the METER paper.
* **Neuron Selectivity Loss:** The baseline loss function with selectivity regularizer.
* **Selectivity Evaluation:** Dissecting the mean selectivity for selected model layers.

### Configuration

The notebook includes several global variables to control model training and evaluation:

* `neuron_selective`:
    * Set to `False` to train a baseline METER model.
    * Set to `True` to train a METER model with neuron selectivity.
* `imde_alpha`: Adjusts the influence of the selectivity on baseline loss. A lower value of `imde_alpha` (default -0.1) will lead to a lower loss when selectivity is higher.
* `cfg_layers`: A list of layers where we want to enhance the depth selectivity of all neurons. For a detailed description of the METER network architecture, please refer to the METER paper[2].

For evaluation, you can modify:

* `layers_to_compute_selectivity`: A list of layers for which to compute mean selectivity.
* parameter `viz_plot`: Set to `True` to visualize the distribution of depth selectivity for each neuron within the specified layer(s).

### Kaggle Notebook

* **Kaggle Notebook Link:** [https://www.kaggle.com/code/technahuynh/interpretable-mde](https://www.kaggle.com/code/technahuynh/interpretable-mde)
  
Note: Previous versions of the notebook contain the best models and performance plots from our setups.

## References

This project builds upon the following papers:

1.  You, Z., Tsai, Y.-H., Chiu, W.-C., and Li, G. (2021). **Towards Interpretable Deep Networks for Monocular Depth Estimation**. *arXiv*.
2.  Papa, L., Russo, P., and Amerini, I. (2023). **METER: A Mobile Vision Transformer Architecture for Monocular Depth Estimation**. *IEEE Transactions on Circuits and Systems for Video Technology, 33*(10), 5882–5893.
