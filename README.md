# General info:
This repository is associated with the paper [paper title, etc here].

# About analyze_files.py
***Please note: this program is intended to allow for reviewers/other researchers to examine the methodology in the paper [TITLE]. It has not been validated for clinical use. Please DO NOT use it for any medical purposes.***
This script is designed to take in user-provided EEG data (along with auxiliary data from other files included in this repository), apply artefact rejection and filtering, extract parameters and statistics of interest, and record parameter/statistic information in an Excel file for the user to utilize in their own analyses. 

# Before starting
## Initializing parameters:
In analyze_files.py, the user can designate if they would like to process intraoperative or postoperative data. Before running the script, the user will need to do 2 things:
  1. Update the setting variable on line 83. Valid values are "intraop", if the user is processing intraoperative data, and "postop", if the user is processing postoperative data. Respectively, these point to processing_parameters_intraop.py and processing_parameters_postop.py in the utils folder.
  2. Update processing_parameters_intraop.py or processing_parameters_postop.py. The default values in these dictionaries are the ones that were used for the analysis in [paper title, etc here]. It is recommended that the user not touch the variables under #File structure variables. The other variables can be changed to customize the analysis; descriptions of these variables are included in the respective dictionaries
## Importing EEG data:
In the interest of portability, the provided code does not natively support data import from .edf or other files; instead, it allows the user to populate an array (files_arr) of file arrays that will then be analyzed. Each array in files_arr should be in the format [id, EEG_signal, sampling_rate], where id is the integer ID of the patient (will be synced up with IDs in the data files), EEG_signal is an array of voltage values from a single channel, and sampling_rate is the signal's ampling rate in Hz. This can be found on line [LINE NUM] of analyze_files.py
## Other necessary files:
There are two Excel files in the data folder for the user to fill out. The first is file_times.xlsx, which is meant to contain recording time data, and the second is surgery_time_data.xlsx, which is meant to contain surgery time data. The details for the data to be input and their appropriate formats can be found in the respective files.

## Dependencies
This pipeline has been validated on Python 3.12.7, 64-bit, with the following dependencies: 
 - numpy 1.26.4
 - scipy 1.11.4
 - pandas 2.2.3
 - matplotlib 3.10.0
 - mne 1.9.0
 - neurokit2 0.2.11
 - pyEDFlib 0.1.40
 - pyGetWindow 0.0.9
 - pyAutoGUI 0.9.54
 - openpyxl 3.1.5
 - nolds 0.6.1
 - statsmodels 0.14.4
 - EntropyHub 2.0
 - PyPDF2 3.0.1
 - NEURAL_py_EEG 0.1.4 (NB: I also have a locally downloaded and managed/edited NEURAL_py_EEG folder in utils. This folder should be left untouched, while the dependency here would also need downloaded.)

