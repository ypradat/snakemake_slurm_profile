# Snakemake profile v7-

## General

This repository holds the configuration files for setting up a snakemake profile. In a nutshell, a profile allows to
specify default values for the (many) options of the [snakemake command line
interface](https://snakemake.readthedocs.io/en/stable/executing/cli.html). For instance the first line of the
`config.yaml` file, namely `restart-times: 1`, specifies the value `1` for the option `--restart-times`. This value can
be overwritten by the user of the snakemake command by specifying `--restart-times [value]` in the command. 
Read the [snakemake documentation](https://snakemake.readthedocs.io/en/stable/executing/cli.html#profiles) to learn more about profiles.

## HPC configuration

Among the important configurations provided by the profile is the configuration of how to submit job on the HPC you are
running your snakemake command on. Up to snakemake versions v7, the configurations of how to submit jobs on a cluster
were provided to snakemake via the options `--cluster` and `--cluster-status`.

Configurations vary according to the scheduler that the HPC rely on. Consequently, there are multiple ready-to-use
profiles for the most commonly used schedulers such as slurm. You may find profiles on the following github repository
<https://github.com/Snakemake-Profiles>. In short, the profile is simply a folder that you add to your `$HOME/.config/snakemake` folder.
This profile was set up by following the instructions in the README of the [slurm cookiecutter
profile](https://github.com/Snakemake-Profiles/slurm). Additional modifications were performed on the file
`slurm-submit.py` to customize the naming of the HPC output file.

## Your configuration

To install this profile, add it as a folder `$HOME/.config/snakemake/<profile_name>`. Then when
running the snakemake command, make sure to specify `--profile <profile_name>`.

If using this profile, make sure to replace the values of `conda-prefix` and `apptainer-prefix` with your own folders
where you would have your conda/apptainer environments stored. Make sure also to install the executor plugin.
