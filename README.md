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

## Data and model files

This project is based on a synthetic geological model adapted from the SimPEG PGI tutorial workflow.

Key files currently used in the repository include:
- `mesh_tutorial.ubc` — model mesh,
- `geology_true.mod` — true subsurface geology model,
- `CDED_Lake_warp.xyz` — topography used to define surface geometry and active cells,
- gravity data files generated or used during the workflow.

The true geology model is converted into a density-contrast model, which is then used to forward-model synthetic gravity anomaly data for inversion experiments.

## Repository structure

- `gravity/Geological_model/`
  Geological model files, mesh files, topography, and notebooks related to model setup.

- `gravity/Tutorial/`
  Tutorial and workflow notebooks for gravity forward modelling and inversion.

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

A good place to start is with the notebooks in:
- `gravity/Geological_model/`
- `gravity/Tutorial/`

These notebooks document the project workflow, including model setup, forward modelling, and inversion.

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
conda activate eosc454-gravity