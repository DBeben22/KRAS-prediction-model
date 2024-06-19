# KRAS-prediction-model

This repository contains the code and datasets for predicting the pIC50 value of FDA approved drugs for the KRAS protein through Machine Learning Models.
These were used in *"insert article name here! and add DOI"*

The code was authored by:

Bebensee, David <br>
Fuschi, Gianluca <br>
Moawad, Christophe Mina Fahmy <br>
St. Germain, Julia <br>

### Instructions on use

All of the outputs are already available as .csv files so there is no need to rerun any of the code.
But if you would want to, here is the order and what each file does:

1. Run the data_fetch_ChEMBL_KRAS.ipnyb file to get the training_descriptors.csv.
   This code accesses a ChEMBL webclient and saves all molecules that have a recorded IC50 with the GTPase KRas molecule (CHEMBL2189121).
   Then using the RDkit Library we generate 209 descriptors from the SMILES code of each molecule.
   Before being exported the IC50 are being standardized to pIC50.

2. run the removing_outliers.ipnyb and remove the outliers from the training_descriptors.csv and output training_descriptors_no_outliers.csv
   This code runs for 50 iterations and identifies outliers that occur multiple times.
   The top 8 outliers will then be removed from the dataset.

4. run the transform_fda.ipnyb file on the fda.csv file which we got from the ChEMBL databast by filtering approved and 1 or less Rule of 5 violations,
   you will end up with the FDA_features.csv.
   This code runs the same function that generates 209 descriptors with RDkit as data_fetch_ChEMBL_KRAS.ipnyb

6. run the prediction_code.ipnyb file with the FDA_features.csv and training_descriptors_no_outliers.csv,
   you will receive the all_results.csv.
   This code outputs a file which contains the best 13 molecules that appeared over 50 iterations of runs.
