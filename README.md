# Fairness in Skin Lesion Classification for Skin Cancer Detection
Deep Learning in Medicine (BMSC-GA 4493, BMIN-GA 3007) Final Project

**Author**: Annabelle Huether

**Abstract**: Many successful deep learning models have been developed for the task of skin lesion classification and diagnosis. However, since these models involve detection of lesions on the surface of the skin, they are susceptible to bias due to the varying amounts of melanin in the skin of patients. This study explores the impact of various methodological techniques applied during model selection and training to determine which approaches provide the best fairness outcomes across skin type. The results of this study demonstrate that general underfitting, lighter models, and weight decay achieve on average the lowest false negative rate difference across skin types for the task, suggesting that the accuracy-fairness trade-off plays a major role in the optimization of state of the art deep learning models.

**Keywords**: Skin Cancer, Fairness, Algorithmic Bias, Skin Lesion Classification, HAM10000

The files are run in the following order:

1. `Download_Data.ipynb` downloads the HIBA .csv files and images from ISIC-CLI (following https://github.com/piashiba/HIBASkinLesionsDataset.git) and the HAM10000 data was downloaded from the web at https://dataverse.harvard.edu/dataset.xhtml?persistentId=doi:10.7910/DVN/DBW86T, download these images and .csv files to a working directory of choice
2. `Data_Preprocessing.ipynb` loads in the .csv files (make sure to change the file paths to your working directory where the images and .csv files are located) and performs some EDA and preprocessing steps before splitting the data and saving the necessary .csv files for training to the current directory: `train.csv`, `validation.csv`, `test.csv` and `HIBA_dataset_skin_type.csv`
3. `InceptionV3_Models.ipynb` performs hyperparameter tuning (creating samples of the training, validation and testing data: `sample_train.csv`, `sample_validation.csv`, `sample_test.csv`) and runs experiments 1-4 on the InceptionV3 architecture on GPU (2 core, 32GB), and saves them to a directory `Inception_Models_F1` (create this folder in the current directory if running and saving the models)
4. `InceptionV3_Model_Evaluation.ipynb` uses the saved models and evaluates the InceptionV3 experiments on `test.csv` and `HIBA_dataset_skin_type.csv`
5. `MobileNetV2_Models.ipynb` performs hyperparamter tuning using the same samples as used for InceptionV3 and runs experiments 1-4 on the MobileNetV2 architecture on GPU (2 core, 32GB), and saves them to a directory `MobileNetV2_Models_F1` (create this folder in the current directory if running and saving the models)
6. `MobileNetV2_Model_Evaluation.ipynb` uses the saved models and evaluates the MobileNetV2 experiments on `test.csv` and `HIBA_dataset_skin_type.csv`
7. The results from evaluation were then collected to `Evaluation_Metrics.csv` and loaded into `Results_Analysis.ipynb` for analysis and visualization
