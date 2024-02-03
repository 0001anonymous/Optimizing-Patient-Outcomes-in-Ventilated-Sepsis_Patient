# Optimizing Patient Outcomes in Ventilated Sepsis Patients: An Interactive Machine Learning-Based Model


## Abstract
This study focuses on optimizing ventilator parameter settings for patients using mechanical ventilation and predicting the success or failure of weaning. While previous research has primarily concentrated on predicting weaning outcomes or identifying optimal weaning timing, there has been a lack of effective recommendations for clinicians on adjusting ventilator parameters. In response, we propose a novel approach that leverages the interactive application of three distinct models to provide clinicians with valuable medical assistance suggestions. These models are the doctor model, patient model, and event model. The doctor model aims to learn from successful weaning cases, providing insights into how clinicians should adjust ventilator settings for favorable outcomes. The patient model is responsible for predicting corresponding changes in vital signs based on the ventilator settings given by the clinician. The event model predicts the likelihood of successful weaning for the current patient, while successful weaning is defined by no reintubation or death in 48 hours after weaning. To validate our approach, we utilized the MIMIC dataset, specifically focusing on a cohort of patients with sepsis. Our event model achieved an AUROC of 0.82 on the test data and an accuracy of 80.66\%. Additionally, when using the doctor model to re-treat all patients in test data 12 hour before weaning, based on the prediction results, the fail rate decreased from the initial 36.5\% to 23\%. Our findings present a promising method for enhancing clinical decision-making regarding ventilator management in critically ill patients.

## Code
- BigQuerySQL.md: SQL for cohort selection, feature selection, and ground truth selection.
- data_generator.ipynb: Generate n (default n = 24) rows for each stay_id
- group_data_generator.ipynb: Generate group data by hour for doctor model and patient model
- models.ipynb: Including doctor model (A model) and Patient model (B model)
- run_model.ipynb load and run model C
- ABC_iterate.ipynb combine model ABC together
- modelC.ipynb train model C
## CSV
- data_by_table: query result from BigQuery, group by table on the MIMIC IV database
- model_data: data for the Doctor model and Patient model
- split_cohort_stay_id: train, val, and test stay_id
## EDA and Visualization
- DH_tableone.Rmd: Print out the table one and the skim summary for dataset.
- DH_project_pairplot.ipynb: Print out the feature pairplot for figuring out the feature importance pair by pair.
- 4_model_SHAP.ipynb: Print out the SHAP value visulization of four models other than our event model.
## four_model
Some experiments for Decision Tree, Random Forest, SVM, XGBoost.
 - run_model_output_inputdata_csv.ipynb: generate 0109tryinputmodelC.csv file which contains total data set (c1, c2, and c3). I add some code from run_model.ipynb provided by Han-Jay Shu. 
 - run_model_output_nnroccurve_csv.ipynb: generate nn_for_roc.csv file to print ROC curve for NN model. I add some code from run_model.ipynb provided by Han-Jay Shu. 
 - c1_c2.ipynb: generate 0108tryc3_stayid.csv file which contains only c1 set and c2 set, without c3 set. And generate Tableone of before_weaning_hr = 0 and before_weaning_hr = 23. 
 - 4_model_using_C_input_with_0108newdata.ipynb: train four models (Decision Tree, Random Forest, SVM, XGBoost) with the total data set containing c1, c2, and c3. And can print accuracy, feature importance for the four models, and ROC curve for the five models. 
 - 4_model_using_C_input_only_contain_c1c2.ipynb: train four models (Decision Tree, Random Forest, SVM, XGBoost) with the total data set containing c1, c2, without c3. And can print accuracy, feature importance, and ROC curve for the four models. 
 - ground_truth: containing the ground truth for each stay_id

