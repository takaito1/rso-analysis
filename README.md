# rso-analysis
## getting started
### access
- If you have account at NCAR cheyenne/casper, access the jupyterhub via copying this URL to your browser, https://jupyterhub.hpc.ucar.edu
- You can also install anaconda on your PC/laptop and run jupyterlab locally
### setting up python environment (do this only once)
- Start jupyterlab
- From the select "+" to start a new launcher, and from "other" start a "terminal" to open a command line terminal. 
- First download "miniconda Linux 64bit" from https://docs.conda.io/en/latest/miniconda.html 
- This can be done using wget command, or first download it to your computer and use the upload icon on the jupyterhub to upload the Miniconda3-XXXX.sh file to your home directory
- Execute the shell script by typing as follows and set up base of miniconda3
> bash Miniconda3-XXXX.sh
- Follow the prompts. It will ask for the destination to install miniconda3. I suggest you follow the prompt and use your $HOME.   
- It will ask "Do you wish the installer to initialize Miniconda3?". Answer no to this one. 
- You can manually initialize miniconda3 by typing at the command prompt as follows: 
> source $HOME/miniconda3/etc/profile.d/conda.sh
> 
> conda activate
- You should see (base) before the prompt now. Now you are in the "base" environment. First update the base environment and follow the prompts to completion. 
> conda update --all
- Next install mamba. This is a parallel version of conda. 
> conda install mamba -c conda-forge
- you will copy the env-calc.yml file from this repository. Try: 
> mkdir -p /glade/work/$USER
>
> cd /glade/work/$USER
> 
> git clone https://github.com/takaito1/rso-analysis.git
> 
> cd rso-analysis
- Create a new "calc" environment. (This might take a while, please be patient)
> mamba env create -f env-calc.yml
- Make the new "calc" environment accessible from jupyter notebook
> conda activate calc
> 
> python -m ipykernel install --user --name calc --display-name Calc
- Now your python environment is ready!
## RSO analysis example
- 5km resolution model output is stored in /glade/campaign/univ/ugit0018/rso/ecoDrake.64t.5km.100lev/'
- 10km resolution model output is stored in '/glade/p/univ/ugit0016/rso/ecoDrake.64t.10km.42lev/ver8/'
- SeaFlux (Fay et al., 2021) observation is stored in '/glade/work/ito/dataset/ocean/'
### Calculating and visualizing the Drake Passage pCO2 time series climatology
- Tutorial: regional pCO2 time series [tutorial1_pco2_timeseries.ipynb](https://github.com/takaito1/cori-shared-notebook/blob/main/tutorial1_sst_maps.ipynb). This tutorial shows basic I/O with xarray, calculation of regional pCO2 data, and basic plotting 
