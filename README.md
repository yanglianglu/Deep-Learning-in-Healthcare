# CS 598 Deep Learning in Healthcare: Characterizing personalized effects of family information on disease risk
## Setting Up Environment
1. Open https://github.com/yanglianglu/Deep-Learning-in-Healthcare/blob/main/DL4H_Team_0.ipynb in Google Colab
2. Check python version and dependencies under Methodology - Environment section
3. pip install -r requirements.txt

## Understanding the Data
1. Run code under Data Section for visualization
2. Run code under Data Preprocessing and Data Loading to prepare data
3. Data used for training is located here https://github.com/yanglianglu/Deep-Learning-in-Healthcare/tree/main/family-EHR-graphs/test
## Model Training
1. Make sure the csv files exist at the correct location (e.g. "test/featfiles/featfile_A1.csv")
2. Run code under Training Section
3. Training results are avaliable under https://github.com/yanglianglu/Deep-Learning-in-Healthcare/tree/main/family-EHR-graphs/results if you don't want to retrain the models
## Evaluation
1. Make sure the result csv files exist at the correct location (e.g. 'results/a1_TestDisease_results.csv')
2. Run code under Evaluation Section

## Results
When comparing the performance of each model between the original and the reproduced versions, we can analyze the trends and differences to understand the impact of the various components used in the models:

1. **Age and sex MLP**
   - **Original**: 0.696 AUC-ROC
   - **Reproduced**: 0.632 AUC
   - The original model performs better than the reproduced version.

2. **Age, sex, family history MLP**
   - **Original**: 0.710 AUC-ROC
   - **Reproduced**: 0.770 AUC
   - Including family history data enhances performance in both cases. Nevertheless, the improvement is more noticeable in the reproduced version, which might due to seeding.

3. **Age, sex, graph connectivity MLP**
   - **Original**: 0.696 AUC-ROC
   - **Reproduced**: 0.770 AUC
   - With the inclusion of graph connectivity over the age and sex model, both case does not demonstrate any improvement.

4. **Age, sex, and longitudinal EHR data LSTM**
   - **Original**: 0.763 AUC-ROC
   - **Reproduced**: 0.643 AUC
   - The original study found that the use of longitudinal EHR data resulted in a significant improvement in performance. However, the reproduced version of the study showed only a slight improvement over the age and sex model. This difference in results could be attributed to the training process of the LSTM models.

5. **Age, sex, family history, and longitudinal EHR data LSTM**
   - **Original**: 0.771 AUC-ROC
   - **Reproduced**: 0.768 AUC
   - Combining family history with longitudinal EHR data in an LSTM framework seems to yield better results than using either alone. The original model shows a greater improvement.

6. **Graph model, with longitudinal data**
   - **Original**: 0.775 AUC-ROC
   - **Reproduced**: 0.796 AUC
   - The graph model incorporating longitudinal data achieves the highest performance in both the original and reproduced studies, underscoring the model's robustness. However, the original version's performance is notably lower.
     
- The ablation study trend suggests that each additional data type, such as family history, graph connectivity, and longitudinal EHR data, contributes incrementally to the model's predictive power. This observation is consistent with the original paper's claims and is supported by the reproduced results, albeit to varying degrees.

- Both the original and reproduced studies indicate that models utilizing more sophisticated data representations, particularly those using graph structures, tend to perform better. Although there are differences in the exact performance metrics, such as the poor performance of LSTM in the reproduced version, the overall trend remains similar. This underscores the importance of graph-based models for complex data integration tasks, such as those involving medical histories and familial relationships, as suggested by the original paper.
  
## Conclusion
Key findings from the experiments indicate that the graph-based model not only outperformed all baselines in predicting the onset of complex diseases over a ten-year period but also provided actionable insights through explainability features, identifying key familial relations and medical history factors that contribute to disease risk.

## Reference
1. Original Github link https://github.com/dsgelab/family-EHR-graphs
2. Original Paper https://arxiv.org/pdf/2304.05010
