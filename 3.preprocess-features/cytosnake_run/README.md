# Using CytoSnake to preprocess Single-cell morphology features

In this tutorial, we will be using the dataset produced in module `2.extract-features/features` folder and process it with `CytoSnake`.

## Using CytoSnake

### installing CytoSnake

> **note**: This sction will be updated once mamba is [fixed](https://github.com/mamba-org/mamba/issues/2882#issuecomment-1746314832) . There are some current issues when installing cytosnake via conda/mamba in the bioconda channel.

First, we need to download and install `CytoSnake` into our python environment.
It is recommended to use `conda` as your Python package manager.

Install `CytoSnake` via GitHub:

```bash
git clone https://github.com/WayScience/CytoSnake.git
```

Go into the `CytoSnake` folder

```bash
cd CytoSnake
```

Install `cytosnake`'s dependencies and create an environment

```bash
conda env create -f cytosnake.yaml
```

Switch to the created environment:

```bash
conda activate cytosnake
```

Install `cytosnake` source code locally to your `conda` environment.
Then take you out of the `CytoSnake` folder.

```bash
pip install -e && cd ..
```

### Setting up your data with CytoSnake

First you need to initalize the current directory into a `ProjectDirectory`.
This helps `CytosSnake` know that there is a project within the current directory and no other datasets should be accounted with using the directory.
This is a great way to prevent overwriting directories with other datasets.
To execute, type:

```bash
cytosnake init -d ../../2.extract-features/features/*.sqlite -m ../../2.extract-features/features/metadata -b ../../2.extract-features/features/barcode_platemap.csv
```

Now that the data is initialized into the `ProjectDirectory`, you can select a workflow to run your analysis.

```bash
cytosnake run cp_process
```