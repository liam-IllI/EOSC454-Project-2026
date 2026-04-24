# 3D Gravity Inversion of a Synthetic Geological Model in SimPEG

This repository contains my EOSC 454 course project on 3D gravity inversion using SimPEG. The project investigates how well gravity inversion can recover the geometry and density distribution of a known synthetic geological model, and how different inversion and weighting strategies affect that recovery.

## Project question

How well can 3D gravity inversion in SimPEG recover the geometry and density distribution of a known synthetic geological model, and how do sparse-norm inversion and different weighting strategies affect that recovery?

## Project overview

This project is designed as a closed-loop synthetic experiment. Starting from a known true geology model, I construct a density-contrast model, generate synthetic gravity anomaly data, and then invert those data using different inversion approaches. The recovered models are compared directly with the known truth.

The main workflow includes:
- defining the mesh, topography, and active cells,
- assigning a density-contrast model based on the true geology,
- forward-modelling synthetic gravity anomaly data,
- performing gravity inversion under different regularization and weighting strategies,
- comparing the recovered models with the true model.

## Methods and software

This project is implemented in Python using SimPEG, following the general workflow of the SimPEG gravity inversion tutorials.

The inversion approaches explored in this project include:
- baseline weighted least-squares (WLS) inversion,
- sparse-norm inversion using IRLS,
- depth weighting,
- sensitivity weighting.

In practical terms, the repository is centered on one main notebook that:
- loads the mesh, geology model, topography, and gravity observations,
- visualizes the synthetic geological model,
- runs several gravity inversions,
- compares recovered density models against the known synthetic truth.

## Data and model files

This project is based on a synthetic geological model adapted from the SimPEG PGI tutorial workflow.

Key files currently used in the repository include:
- `mesh_tutorial.ubc` — model mesh,
- `geology_true.mod` — true subsurface geology model,
- `CDED_Lake_warp.xyz` — topography used to define surface geometry and active cells,
- gravity data files generated or used during the workflow.

The true geology model is converted into a density-contrast model, which is then used to forward-model synthetic gravity anomaly data for inversion experiments.

## Repository structure

- `gravity/Geological_model_Inversion/`
  Core project directory containing the main notebook, geological model files, mesh, topography, gravity data, and VTK outputs.

- `gravity/Geological_model_Inversion/geological_model.ipynb`
  Main notebook and recommended starting point for understanding the full workflow.

- `gravity/Geological_model_Inversion/mesh_tutorial.ubc`
  Octree mesh used for the forward and inverse modelling workflow.

- `gravity/Geological_model_Inversion/geology_true.mod`
  True synthetic geology model used to construct the density-contrast model.

- `gravity/Geological_model_Inversion/gravity_data.obs`
  Gravity observation data used in the inversion experiments.

- `gravity/Geological_model_Inversion/CDED_Lake_warp.xyz`
  Topography file used to define the surface and active cells.

- `gravity/Tutorial/`
  Supporting tutorial notebooks for gravity forward modelling and inversion. These are references, not the main project entry point.

- `gravity/Plots/`
  Exported figures from the inversion experiments.

- `README.md`
  Project description and usage notes.

- `LICENSE`
  Repository license.

## Goals

The main goals of this project are:
- to build and run a complete synthetic 3D gravity inversion workflow in SimPEG,
- to perform a baseline WLS inversion,
- to perform a sparse-norm / IRLS inversion and compare it with the baseline result,
- to evaluate inversion results using observed versus predicted gravity anomaly maps, residual maps, and slices or cross-sections of recovered density,
- to compare recovered density models directly with the known true model,
- to discuss which subsurface features are recoverable from gravity data alone and which remain ambiguous because of smoothing, depth bias, and non-uniqueness.

## Stretch goals

Additional goals include:
- comparing depth weighting and sensitivity weighting under similar inversion settings,
- assessing which weighting strategy better reduces shallow bias,
- evaluating which approach improves recovery of deeper structure.

## How to use

If you are opening the repository for the first time, start here:

1. Open `gravity/Geological_model_Inversion/geological_model.ipynb`.
2. Run the notebook from top to bottom in that directory so the relative paths to the mesh, model, topography, and gravity files resolve correctly.
3. Use the notebooks in `gravity/Tutorial/` only as supporting references for the SimPEG workflow.

The repository contains multiple notebooks, but `gravity/Geological_model_Inversion/geological_model.ipynb` is the main project notebook and the best place to begin.

## Reproducibility

To make the project easier to understand and reproduce, this repository is being organized to include:
- notebooks with documented workflow steps,
- model, mesh, and topography files used in the experiments,
- code and data files required for forward modelling and inversion,
- a license for reuse permissions.

## Installation

It is recommended to use a dedicated conda environment.

Create the environment with:

```bash
conda env create -f environment.yml
conda activate simpeg_env
```

If `conda` is not available in your terminal, open an Anaconda Prompt first or add your Anaconda installation to `PATH` before running the commands above.

Notes:
- The environment name in `environment.yml` is `simpeg_env`, so that is the name to activate.
- The notebook depends on `discretize` and `simpeg`; if those imports fail, the environment is not active.
- Launch Jupyter from the repository root or change into `gravity/Geological_model_Inversion/` before running `geological_model.ipynb`, so relative file paths resolve correctly.
- The 3D visualization cell uses `pyvista`. If that backend is unavailable on your machine, the rest of the notebook can still be useful, but interactive 3D display may be limited.
