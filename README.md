# Dmel-sgRNA-Efficiency-Prediction

Python and R pipeline to predict sgRNA efficiency via a machine learning algorithm (Ridge regression) trained and optimized on CRIPSR pooled gene essentiality screens (see : https://www.biorxiv.org/content/early/2018/03/01/274464).   
The score returned ranges between 0 and 1, the higher the more effective the sgRNA is predicted to be.    
The details of the methods used to find the features and choose the machine learning model will be available "soon".    

### Requirements
Softwares : Python3 & R   
To install required Python packages, run in your terminal :   
```pip3 install -r /PATH/TO/utils/requirements.txt```
  
## Inputs
1/ _--seq_ : One raw 23 or 30mer sequence.   
Format of the raw sequence :  
**23mer** : 20mer sgRNA + PAM : **[20mer sgRNA sequence]NGG**   
**30mer** : 20mer sgRNA + PAM + context sequence : **NNNN[20mer sgRNA sequence]NGGNNN**   
      
2/ _--csv_ : .csv file with a header and the 23 or 30mer sgRNAs beneath   
Format of the **Comma delimited** .csv file

|  _Header_  |
| ------------- |
|  GGTTGCAGCTTTAGTGGTCGACAACGGATC  |
|  AAATCGCGACCGGCTAGATCCAAACGGAGG  | 
|              ...                 | 
|  GCCCAACCATGGGCAAGCGTCTGCAGGACA  | 

3/ _--out_ : (optional argument) Path and/or Name of the predictions output csv file. Default is PATH_TO_FOLDER/sgRNA_efficiency_prediciton/sgRNA_predictions.csv

## Outputs
The R Pipeline outputs the dataframe of the extracted features from the 23 or 30mer sequences in PATH_TO_FOLDER/sgRNA_efficiency_prediction/Rpreprocessing/R_Featurized_sgRNA.csv

The prediction score for each sgRNA is written in a csv file that can be specified via the _--out_ argument.    
By default, the scores are exported to PATH_TO_FOLDER/sgRNA_efficiency_prediction/sgRNA_predictions.csv

## Running the code
Preferably, make the "sgRNA_efficiency_prediction" folder your working directory.   
```cd PATH_TO_FOLDER/sgRNA_efficiency_prediction```

To run model prediction on a raw sgRNA, type in the terminal:   
```python3 dMel_CRIPSR_efficiency.py --seq <23 or 30mer sequence> [--out <PATH_TO_OUTPUT>]```   
   
To run model prediction on a csv file, type in the terminal:    
```python3 dMel_CRIPSR_efficiency.py --csv <PATH_TO_CSV_FILE> [--out <PATH_TO_OUTPUT>]```

### Examples
```python3 dMel_CRIPSR_efficiency.py --seq TGGAGGCTGCTTTACCCGCTGTGGGGGCGC```    
Output : ```Predicted efficiency score [0:1] for TGGAGGCTGCTTTACCCGCTGTGGGGGCGC =  [0.38789814] (the higher the better)```

The file TEST_sgRNA_to_predict.csv is provided as test file.   
```python3 dMel_CRIPSR_efficiency.py --csv TEST_sgRNA23mer_to_predict.csv```     
Output : ```DONE. Results exported to /home/.../sgRNA_efficiency_prediction/23mer_sgRNA_predictions.csv```

## Authors

**Pierre Merckaert** - [PierreMkt](https://github.com/PierreMkt)

## License

This project is licensed under the MIT License - see the [LICENSE.md](LICENSE.md) file for details

## Acknowledgments

**Perrimon Lab** (https://perrimon.med.harvard.edu/)    
**DRSC** (https://fgr.hms.harvard.edu/)

