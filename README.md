# CONP Experiments

CONP Experiments is a DataLad dataset containing the experiments available in the
Canadian Open Neuroscience Platform. It leverages
[DataLad](http://datalad.org) to store metadata and references to
data files distributed in various storage spaces and accessible depending on each experiment owner's
policy.

The instructions below explain how to find and get experiment information from this DataLad dataset.
You can also add an experiment by following the instructions in our [contribution
guidelines](https://github.com/CONP-PCNO/conp-experiments/blob/master/.github/CONTRIBUTING.md).
We welcome your feedback! :smiley:

## Dataset structure

`projects` contains a sub-dataset for each experiment.

Experiment maintainers are responsible for the management and curation
of their own sub-datasets.

## Installing required software

### git

`sudo apt-get install git`

It is useful to configure your `git` credentials to avoid having to enter them repeatedly:

`git config --global user.name "yourusername"`
`git config --global user.email "your.name@your.institution.ca"`

### git-annex

First install the neurodebian package repository:

`sudo apt-get install neurodebian`

Then install the version of git-annex included in this repository:

`sudo apt-get install git-annex-standalone`

The version of git-annex installed can be verified with:

`git annex version`

As of May 12 2020, this installs git annex v 8.20200330, which works with CONP datasets. Earlier versions of git-annex may not.

### DataLad:

`sudo apt-get install datalad`

## Getting the data

Install the main CONP dataset on your computer:

```console
datalad install -r http://github.com/CONP-PCNO/conp-experiments
```

Get the files you are interested in:

```console
datalad get <file_name>
```

This may require authentication depending on the data owner's configuration.

You can also search for relevant files and sub-datasets:

```console
datalad search T1
```

## Coding standards

To keep the Python code maintainable and readable a suite of QA pipelines is testing the code assuring code standards.
Pull requests will trigger a GitHub workflow executing pre-commit.

To execute pre-commit locally, you will need to [install pre-commit](https://pre-commit.com/#installation) using your favorite method.
Then, run:
```bash
pre-commit install

pre-commit run --all-files
```
Pre-commit won't let you commit until reported issue are fixed.
If problematic, you can optionally skip the pre-commit for a local commit using the `--no-verify` flag when commiting, however this will still perform QA test on your PR.
