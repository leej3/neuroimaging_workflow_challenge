Integration testing: [![CircleCI](https://circleci.com/gh/agt24/workflow_challenge.svg?style=shield&circle-token=742274cfd7bd81d4c33df1ce864b2f6ba5ecf894)](https://circleci.com/gh/agt24/worflow_challenge)

## Imaging data science and sharing team challenge

This code base was written to demonstrate a reproducible workflow. The script downloads some MRI data from a shared data repository, performs some processing, then compares the output against a set of reference files to determine if the output matches.

For the purpose of this exercise, we've broken the code such that integration testing fails (as indicated by the badge on this page).  Your task is to troubleshoot the workflow to find the bug and try to fix it. Generate a passed circleci build (which should turn the badge above from red to green). Ideally this passed build would be using your own circleci account in a forked repository, but an easier way would be to push the fix directly to the master branch in this repo. Remember we're interested equally in your approach and your process as much or more than getting to the solution. Please log your approach and your process in the google doc.





#### In order to run the workflow:

To run on one subject (which is all that circleci tests):
```bash
python run_demo_workflow.py --key 11an55u9t2TAf0EV2pHN0vOd8Ww2Gie-tHp9xGULh_dA -n 1
```

#### Prerequisites
1. Make sure FSL is available in your environment and accessible from the command line.

2. If you already have a `conda` environment, please follow the detailed steps below. 

3. 
    
a) If you do not have a conda environment, the following step will download and install a Python 2 conda environment with the appropriate python packages. 

```bash
curl -Ok https://raw.githubusercontent.com/agt24/workflow_challenge/master/Simple_Prep.sh
source Simple_Prep.sh
```

or

b) Do the following:


Install miniconda if you do not have it.

For Linux:

```bash
curl -o miniconda.sh  http://repo.continuum.io/miniconda/Miniconda2-latest-Linux-x86_64.sh
```

For OS X:

```bash
curl -o miniconda.sh  http://repo.continuum.io/miniconda/Miniconda2-latest-MacOSX-x86_64.sh
```

Next setup miniconda (both OS X or Linux).

```bash
chmod +x miniconda.sh
./miniconda.sh -b
conda config --add channels conda-forge
```

If you did not add miniconda to your environment (`.bash_profile`), execute to add to your current environment:

```bash
export PATH=$HOME/miniconda2/bin:$PATH
```

Download the Workflow repository and create the specific versioned Python environment:

```bash
curl -OsSL https://github.com/agt24/workflow_challenge/archive/master.zip
unzip master.zip
cd workflow_challenge
conda env create -f environment.yml
source activate workflow_env
pip install https://github.com/satra/prov/archive/enh/rdf-1.x.zip
```

