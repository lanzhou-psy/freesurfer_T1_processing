# freesurfer_T1_processing
This repository contains Python scripts to process T1-weighted MRI data into morphometry outputs using FreeSurfer’s recon-all .  The main script automates batch processing of .nii and .nii.gz files in a given folder, handling FreeSurfer subject directory creation, overwrite options, and multithreading.


## Features

Automatically finds all .nii and .nii.gz T1 files in a folder.

Runs recon-all for each subject.

Smart overwrite handling (--overwrite).

Uses all available CPU threads minus one by default (configurable with --openmp).

Reports elapsed time

## Requirements

Python 3.7+

FreeSurfer installed and sourced (SetUpFreeSurfer.sh).


## Input data
Prepare one T1-weighted NIfTI scan per subject. Including the participant ID in the filename is recommended.
For example, under the T1 folder:
'''
sub001_memprage.nii.gz
sub002_memprage.nii.gz
'''
## Run the scripts

'''
python3 freesurfer_T1.py /path/to/T1_directory [--overwrite] [--openmp N]
python fs2csv.py /path/to/T1_directory
'''

Arguments:

t1_dir → Folder containing T1 NIfTI files (*.nii or *.nii.gz).

--overwrite → If a subject folder already exists, remove and re-run.

--openmp N → Number of threads for FreeSurfer’s -openmp flag (default: CPUs - 1).

## Output data

For each T1 file, a new subject directory will be created inside t1_dir containing FreeSurfer’s standard morphometry outputs (surfaces, volumes, stats).





