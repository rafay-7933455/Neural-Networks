# Neural Networks Assignment 1

## Overview

This repository contains the completed Jupyter notebook for a neural-networks assignment using Fashion-MNIST.

The notebook covers:

1. Manual neural-network forward propagation and backpropagation
2. Activation-function and architecture experiments
3. Classification loss comparison and regression
4. Optimizer comparison and learning-rate tuning
5. Overfitting and bias/variance analysis
6. Regularization and generalization techniques
7. Random hyperparameter search, 5-fold cross-validation, and final evaluation

## Repository contents

```text
.
├── a1_ready_to_submit.ipynb
├── README.md

```

> Keep the dataset path consistent with the notebook, or update the loading cell if your local folder structure is different.

## Requirements

Recommended environment:

- Python 3.10+
- Jupyter Notebook or JupyterLab
- NumPy
- pandas
- matplotlib
- scikit-learn
- PyTorch

Install the dependencies with:

```bash
pip install numpy pandas matplotlib scikit-learn torch jupyter
```

## How to reproduce the results

1. Clone the repository:

```bash
git clone https://github.com/rafay-7933455/Neural-Networks.git
cd Neural-Networks
```

2. Make sure the dataset is available at:

```text
https://www.kaggle.com/datasets/zalando-research/fashionmnist (fashion-mnist_train.csv)
```

3. Start Jupyter:

```bash
jupyter notebook
```

4. Open:

```text
a1.ipynb
```

5. Run all cells from top to bottom.

The notebook fixes random seeds to `42` in the main experiments to improve reproducibility.

## Part 4

Four optimizers are compared:

- SGD
- SGD + Momentum
- RMSProp
- Adam

The notebook first compares them using the same learning rate and then uses optimizer-specific learning rates. The reported tuned experiment obtained the following validation accuracies:

| Optimizer | Learning Rate | Final Validation Accuracy |
|---|---:|---:|
| SGD | 0.010 | 13.14% |
| SGD + Momentum | 0.010 | 19.50% |
| RMSProp | 0.001 | 70.85% |
| Adam | 0.001 | 66.83% |

None of these four runs reached 85% validation accuracy within 20 epochs.

## Part 5

A high-capacity network with at least four hidden layers of 512 units is trained on 2,000 samples to demonstrate overfitting. The notebook reports training/validation loss, marks the separation epoch, calculates the generalization gap, and provides a numerical bias/variance diagnosis.

## Part 6

The notebook compares:

- L2 regularization
- L1 regularization
- Dropout
- Batch normalization
- Early stopping
- Data augmentation
- Increasing the training set to 10,000 and 20,000 samples

The results are summarized in a single table and the L2/dropout generalization gaps are plotted against regularization strength.

## Part 7

Random search evaluates 12 hyperparameter configurations using 5-fold cross-validation on the Part 7 training split. The top five configurations are displayed with their mean and standard-deviation CV scores.

The best configuration is then retrained on the full Part 7 training split and evaluated once on the held-out evaluation split using:

- Accuracy
- Macro precision
- Macro recall
- Macro F1
- Confusion matrix

The notebook also compares the final model with a Part 2-style baseline and reports the improvement in percentage points.

## Important evaluation note

The original dataset-loading section uses `fashion-mnist_train.csv` and creates `X_train` and `X_val` using a train/validation split. It does **not** load a separate official Fashion-MNIST test CSV.

Therefore, Part 7 reports its final result on `X_val/y_val` as a **held-out evaluation set**. It should not be described as an untouched official test-set result unless a separate test dataset is added.

## Final result

After running the complete notebook, record these values in the one-page Word summary:

- Final held-out evaluation accuracy
- Macro precision
- Macro recall
- Macro F1
- Selected hyperparameter configuration
- The Part 6 method that produced the largest improvement
- Improvement over the Part 2-style baseline

## Reproducibility checklist

- [ ] Dataset path is correct
- [ ] Dependencies are installed
- [ ] Random seed is 42
- [ ] Notebook is executed from first cell to last
- [ ] Part 4 tables and plots are generated
- [ ] Part 5 bias/variance results are generated
- [ ] Part 6 summary table and plots are generated
- [ ] Part 7 top-5 CV table is generated
- [ ] Final metrics and confusion matrix are generated
- [ ] Word summary is updated with the actual final numbers
