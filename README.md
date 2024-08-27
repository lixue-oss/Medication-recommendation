# Implementation of the paper: Trans-GAHNet: Medication Recommendation with Transformer Based Representation Learning from a Multiple Graph Perspective
# Folder Specification
- mimic_env.yaml
- src/
    - Trans-GAHNet.py: our model
    - train/test baselines:
        - Leap.py
        - Other code of train/test baselines can be find [here](https://github.com/ycq091044/SafeDrug).
    - models.py: baseline models
    - util.py
    - layer.py
- data/ (For a fair comparision, we use the same data and pre-processing scripts used in [Safedrug](https://github.com/ycq091044/SafeDrug))
    - input/
        - drug-atc.csv: drug to atc code mapping file
        - drug-DDI.csv: this a large file, could be downloaded from https://drive.google.com/file/d/1mnPc0O0ztz0fkv3HF-dpmBb8PLWsEoDz/view?usp=sharing
        - drugbank_drugs_info.csv: drug information table downloaded from drugbank here https://www.dropbox.com/s/angoirabxurjljh/drugbank_drugs_info.csv?dl=0, which is used to map drug name to drug SMILES string.
        - ndc2RXCUI.txt: NDC to RXCUI mapping file.
        - RXCUI2atc4.csv: this is a NDC-RXCUI-ATC4 mapping file
    - output/
        - ddi_A_final.pkl: ddi adjacency matrix
        - atc3toSMILES.pkl: drug ID (we use ATC-3 level code to represent drug ID) to drug SMILES string dict
        - ddi_mask_H.pkl: H mask structure 
        - ehr_adj_final.pkl:if two drugs appear in one set, then they are connected
        - records_final.pkl:the final diagnosis-procedure-medication EHR records of each patient
        - voc_final.pkl:diag/prod/med dictionary
        - Under MIMIC Dataset policy, we are not allowed to distribute the datasets. Practioners could go to https://physionet.org/content/mimiciii/1.4/ and request the access to MIMIC-III dataset
    - dataset processing scripts
        - processing.py: is used to process the MIMIC original dataset.
# Step 1: Data Processing
  - Go to https://physionet.org/content/mimiciii/1.4/ to download the MIMIC-III dataset, and then run our processing script to get the complete preprocessed dataset file.
  - go into the folder and unzip three main files (PROCEDURES_ICD.csv.gz, PRESCRIPTIONS.csv.gz, DIAGNOSES_ICD.csv.gz)
  - change the path in processing.py and processing the data to get a complete records_final.pkl
# Step 2: Package Dependency
  - First, install the [conda](https://www.anaconda.com/)
  - Then, create the conda environment
  - To install all necessary packages
# Step 3: run the code
  - Trans-GAHNet.py
        