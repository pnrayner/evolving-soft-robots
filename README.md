Portia Rayner

Since the objective of this project was to explore the limits of an existing framework, this repository is a branch of the original. The tested parameters are described in the final report.


## Installation

The code relies on [Docker](https://www.docker.com/get-started) and the docker wrapper [cpk](https://github.com/afdaniele/cpk) to manage its dependencies.

To use this codebase, follow these installation steps:

1. Intstall Docker.
2. Install cpk: `python -m pip install cpk`
3. Clone this repository.
4. From the top level directory, run `cpk build` to build the docker container.

Git clone the repository, then enter the appropriate evolving-soft-robots directory

run cpk build -f

start a new tmux session

## Testing the Learned and Baseline Models

We provide code to visualize a pretrained model and our baseline.

- To visualize the pretrained model, run: `cpk run -M -f -X -L viz_pretrained`
- To visualize the baseline, run: `cpk run -M -f -X -L viz_baseline`

## Running a Co-optimization Experiment

The training was run with 96 parallel SOFA environments for training on a Ubuntu 32-core [AMD EPYC 7502](https://www.amd.com/en/products/cpu/amd-epyc-7502) with Python.
The cpu load can be adjusted by editing the config file `configs/coopt.yaml`.

- To launch a training job, run: `cpk run -M -f -n train -L train`
- To launch the eval job, run: `cpk run -M -f -n eval -L eval`

To modify the material and environmental parameters, the values of the appropriate .ym and friction values were modified in the config.yaml file. The entropy schedule was changed by editting the config.gin file. 


The eval jobs on the final step on the training were run locally on Dell laptop running Ubuntu. The eval job will search for checkpoints in the `exps` directory and generate videos and evaluation performance.



