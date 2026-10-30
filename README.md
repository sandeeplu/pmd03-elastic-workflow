# pmd03-elastic-workflow


##Elastic constants calculation workflow using pyiron and ASE


## 1. Overview

This repository contains a computational workflow for calculating the elastic properties of crystalline gold (Au) using atomistic simulations.

The workflow is based on `pyiron_workflow`, the Atomic Simulation Environment (ASE), and the Effective Medium Theory (EMT) interatomic potential.

It demonstrates how to construct and execute an atomistic workflow for calculating the elastic stiffness tensor and bulk modulus of a crystalline material.

## 2. Scientific Objective

The objective is to calculate the elastic properties of bulk gold, including:

- Elastic stiffness tensor (6 × 6 matrix).
- Bulk modulus.
- Stress–strain response.

The workflow uses atomic structure relaxation, strain application, and stress calculations to determine the elastic properties.

## 3. Workflow Description

The main workflow is implemented in:

`ex1-elastic.ipynb`

The calculation consists of the following steps:

1. Initialize the atomistic simulation engine using ASE.
2. Define the EMT interatomic potential.
3. Construct the workflow using pyiron-workflow.
4. Generate the bulk crystal structure of gold.
5. Relax the initial atomic structure.
6. Apply independent normal and shear strains.
7. Calculate the corresponding stresses.
8. Fit the elastic stiffness tensor.
9. Calculate the Voigt–Reuss–Hill bulk modulus.

## 4. Software Requirements

The workflow uses:

- Python 3.13
- pyiron-workflow
- pyiron-workflow-atomistics
- ASE
- EMT
- NumPy
- pandas
- Semantikon
- flowrep

The complete dependency configuration is provided in `pyproject.toml` and `environment.yml`.

## 5. Installation

Clone this repository:

```bash
git clone https://github.com/sandeeplu/pmd03-elastic-workflow.git

cd pmd03-elastic-workflow
```

Create the Conda environment:

```bash
conda env create -f environment.yml
```

Activate the environment:

```bash
conda activate pmd03-elastic
```

Start JupyterLab:

```bash
jupyter lab
```

Open `ex1-elastic.ipynb` in JupyterLab.

## 6. Execution

Execute the notebook cells sequentially.

The workflow initializes the ASE engine with the EMT calculator and constructs the elastic tensor calculation using:

```python
elastic_wf = pwf.node(pmd03.unary_elastic_tensor)
```

The calculation returns:

- Elastic stiffness tensor.
- Voigt–Reuss–Hill bulk modulus.

## 7. Repository Structure

```text
pmd03-elastic-workflow/
│
├── ex1-elastic.ipynb
├── environment.yml
├── pyproject.toml
├── meta.json
├── README.md
│
└── pmd03/
    ├── __init__.py
    ├── api.py
    ├── elastic_nodes.py
    ├── gb_nodes.py
    ├── gibbs_nodes.py
    ├── patches.py
    ├── shared.py
    └── uris.py
```

## 8. Original Source and Attribution

This demonstrator is based on the original implementation from:

https://github.com/pyiron-node-store/pmd03_demonstrators

The original implementation and its supporting Python package are acknowledged as the source of this workflow.

The present repository provides a separate distribution focused on Example 1: Elastic Constants Calculation.

## 9. Notes

The elastic properties calculated using EMT are model-dependent. The results should be interpreted in the context of the approximations and applicability of the EMT potential.

The workflow is intended as a demonstrator of atomistic simulation and pyiron-workflow capabilities.

