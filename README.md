# 3D Gravity Inversion Workflows in SimPEG

This repository contains my EOSC 454 course project on 3D gravity inversion using SimPEG. It is now organized around two related workflows collected under `Codes/`:

- a synthetic geological-model study used to test inversion behaviour in a controlled setting,
- a field-data application that adapts the same inversion logic to the TKC ground gravity dataset.

## Project focus

The main technical question behind the project is:

How well can 3D gravity inversion recover subsurface geometry and density structure, and how do different regularization and weighting strategies affect that recovery?

Across the two workflows, the repository compares:

- baseline weighted least-squares (WLS) inversion,
- sparse-norm / IRLS inversion,
- depth weighting,
- sensitivity weighting.

## Repository structure

The current working project content lives under `Codes/`.

- `Codes/Tutorial_and_Synthetic/`
  Synthetic-model workflow for the main EOSC 454 project.

- `Codes/Tutorial_and_Synthetic/Geological_model_Inversion/geological_model.ipynb`
  Main synthetic-case notebook. This is the best starting point for understanding the core SimPEG workflow used in the project.

- `Codes/Tutorial_and_Synthetic/Geological_model_Inversion/`
  Mesh, geology model, topography, gravity observations, and VTK outputs used by the synthetic inversion notebook.

- `Codes/Tutorial_and_Synthetic/Plots/`
  Exported figures for the synthetic study, including observed data, inversion outputs, and comparison plots.

- `Codes/Tutorial_and_Synthetic/Tutorial/`
  Supporting SimPEG tutorial materials kept as references for the gravity workflow.

- `Codes/Tutorial_and_Synthetic/454_presentation_Wu.pptx`
  Project presentation slides.

- `Codes/Field_application/`
  Field-data extension of the project based on the TKC ground gravity dataset.

- `Codes/Field_application/tkc_ground_gravity_field_inversion.ipynb`
  Main field-application notebook. It follows the overall inversion flow of the synthetic notebook, but applies it to field observations.

- `Codes/Field_application/TKC-ground-grav/`
  Input field data files used by the TKC inversion workflow.

- `Codes/Field_application/Plots/`
  Exported figures for the field-data workflow.

- `Codes/Field_application/int-2016-0142.1.pdf`
  Reference document associated with the field application.

- `environment.yml`
  Conda environment definition for the project.

## Suggested starting points

If you are opening the repository for the first time, use this order:

1. Start with `Codes/Tutorial_and_Synthetic/Geological_model_Inversion/geological_model.ipynb` to see the complete synthetic workflow.
2. Then open `Codes/Field_application/tkc_ground_gravity_field_inversion.ipynb` to see how the workflow is adapted to field data.
3. Use the materials in `Codes/Tutorial_and_Synthetic/Tutorial/` as background references rather than the main project entry point.

## Data and outputs

The synthetic workflow includes:

- the mesh file used for forward and inverse modelling,
- the true geology model used to build a density-contrast model,
- topography and gravity observation files,
- exported figures and VTK outputs for visualization.

The field workflow includes:

- processed TKC gravity data files,
- notebook-based inversion experiments,
- exported plan-view and section-view figures for method comparison.

## Installation

Create the conda environment with:

```bash
conda env create -f environment.yml
conda activate simpeg_env
```

The environment currently includes the main packages used in the notebooks:

- `python=3.11`
- `jupyter`
- `numpy`
- `scipy`
- `matplotlib`
- `discretize`
- `simpeg`
- `pyvista`

## Usage notes

- Run notebooks from the repository root or from their own directories so the relative file paths resolve correctly.
- The synthetic notebook is the main methodological reference for the project.
- The field notebook is a companion application built on the same general inversion logic.
- Exported figures are already included in the repository for quick inspection without rerunning the full notebooks.

## License

This repository is distributed under the terms of the `LICENSE` file in the project root.
