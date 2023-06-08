\1;5202;0c### Conda-forge: Setting up all your needs

We will use a conda environment to keep all versions in sync, and save us the headache of trying to keep ROOT up-to-date with the rest of the universe. These directions are based on Bob Hirosky's directions for the University of Virginia's 56XX computational physics courses. The reasoning behind using conda, what it is, and all that jazz is found [there](https://raw.githubusercontent.com/UVaCompPhys/PHYS56xx-setup/master/notebooks/FAQ/WorkingEnv.ipynb).

To get started, we will install minconda.

```bash
wget https://repo.anaconda.com/miniconda/Miniconda3-latest-Linux-x86_64.sh
chmod +x Miniconda3-latest-Linux-x86_64.sh
./Miniconda3-latest-Linux-x86_64.sh

```

This edits your ```.bashrc``` file, so either restart your shell or ```source ~/.bashrc```. The defailt is to start a ```(base)``` conda envoriment upon startup, as indicated from your now altered PS1. I despise this, so to turn off this startup feature, execute

```conda config --set auto_activate_base false```

Now we can begin setting up the useful environment. We will be using the conda-forge repository as the base.

```bash
conda config --add channels conda-forge
conda config --show channels
conda config --set channel_priority strict
```

Setup the conda environment to run this analysis.

```bash
conda create -n ZpAnomalon
conda env list
conda activate ZpAnomalon
```

To deactivate the environment, simply use ```conda deactivate ZpAnomalon```. Leave it activated for the remainder of the steps in this README. Whenever you want to run any scripts, or use any of the programs we have installed, you can skip directly to activating the environment.

Next, we want to check the versions of python and gcc we are running. To do this run:

```
python --version
gcc --version
```

If the version of python is >= 3.7 and the version of gcc is >= 4.6 we are good to go. If either of these are lower, we will need o delete the conda environment and start again. If the versions are OK, install the following packages:

```bash
conda install --yes scipy matplotlib seaborn sympy scikit-learn
conda install --yes root
conda install -c conda-forge uproot
```
To see what you have installed, ```conda list```. The python environment is ready.

