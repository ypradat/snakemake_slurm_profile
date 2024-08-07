# Snakemake profile v8+

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
were provided to snakemake via the options `--cluster` and `--cluster-status`. These options were replaced by the
`--executor` option starting from snakemake v8.

NOTE: If you are using snakemake v7 or an earlier version, switch to the `snakemake-v7` branch of this repository.

Read the snakemake documentation about [executor
plugins](https://snakemake.readthedocs.io/en/stable/tutorial/additional_features.html#cluster-or-cloud-execution) to
learn more about this feature. As for snakemake v7 and earlier, the configuration varies according to the scheduler that
your HPC rely on, and there are ready-to-use plugins for the most commonly used schedulers such as slurm. Check the
[slurm snakemake executor plugin
documentation](https://snakemake.github.io/snakemake-plugin-catalog/plugins/executor/slurm.html) or the [github
code](https://github.com/snakemake/snakemake-executor-plugin-slurm).
In short, the plugin is a python package that you should install in the environment alongside your snakemake command. To
use the plugin, you should specify the option `--executor [name_of_your_plugin_python_package]` within the snakemake
command.

I have adapted a snakemake slurm executor plugin which was already adapted by T. Dayris for Gustave Roussy HPC cluster.
The plugin by T. Dayris is available at <https://snakemake.github.io/snakemake-plugin-catalog/plugins/executor/slurm-gustave-roussy.html>
while my plugin is available at <https://github.com/ypradat/snakemake-executor-plugin-slurm-gustave-roussy>
This latter plugin was not deposited on `pip` so you will have to locally install it via `pip install -e
/path/to/plugin` from the environment where snakemake is installed.

## Your configuration

If using this profile, make sure to replace the values of `conda-prefix` and `apptainer-prefix` with your own folders
where you would have your conda/apptainer environments stored. Make sure also to install the executor plugin.
