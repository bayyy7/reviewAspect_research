# Sentiment of Aspect Review
> Based on our research

This repo contains code and implementation of classification on International Conference on Learning Representations (ICLR) 2017-2020 paper dataset.

# Paper
***"Predicting the Sentiment of Review Aspects in the Peer Review Text using Machine Learning"*** <br>
You can access via this link down below:<br>

[Paper](#)

# Abstract
<p align="justify"> This paper develops a Machine Learning (ML) model to classify the sentiment of review aspects in the peer review text. Reviewers use review aspect as paper quality indicators such as motivation, originality, clarity, soundness, substance, replicability, meaningful comparison, and summary during the review process. The proposed model addresses the critique of existing peer review process, including a high volume of submitted papers, limited reviewers, and reviewer bias. This paper uses citation functions, representing the reason why author of scientific papers cites previous works, as the main predictor. Specifically, the predictor comprises citing sentence features created based on labeling scheme of citation functions, regular sentence features created by applying the label of citation functions to non-citation text, and reference-based features obtained by identifying the source of citation. This paper utilizes the International Conference on Learning Representations (ICLR) 2017-2020 paper dataset, which includes sentiment values (positive or negative) for all review aspects. Our experiment on combining XGBoost, oversampling, and hyper-parameter optimization revelaed that not all review aspects can be effectively estimated by the ML model. The highest results were achieved when predicting Replicability sentiment with 97.74% accuracy. It also demonstrated accuracies of 93.93% for Meaningful Comparison and 94.03% for Motivation. However, the model exhibited lower effectiveness on Originality and Substance (85.21% and 79.94%) and performed less effectively on Clarity and Soundness with accuracies of 61.22% and 61.11%, respectively. Additionally, while the regular sentence is the top predictor only for Replicability, the combination predictor is most effective in achieving the best results for Meaningful Comparison, Motivation, and Substance.</p>

# Dataset
<p align="justiify">This paper uses dataset for both papers and its review results from ICLR 2017-2020 containing 5,156 papers (Yuan et al., 2022) as shown in Table I. While the final decision of paper acceptance is already available in the dataset and is determined by the ICLR’s editor, the paper quality (good/poor) is adopted from the research conducted in our previous research (Basuki & Tsuchiya, 2022b).</p>

**TABLE II.** DISTRIBUTION OF ICLR PAPERS USED IN THE PREDICTION SYSTEM

<p align="center"></p>

| Year | Accepted Papers | Rejected Papers | Total Papers | Good Papers | Poor Papers | Total Papers |
|---|---|---|---|---|---|---|
| 2017 | 198 | 502 | 686 | 416 | 71 | 487 |
| 2018 | 289 | 1048 | 1337 | 769 | 138 | 907 |
| 2019 | 336 | 1526 | 1862 | 1275 | 275 | 1550 |
| 2020 | 571 | 1722 | 2293 | 1115 | 1097 | 2212 |
| **Total** | **1404** | **4798** | **6208** | **3575** | **1581** | **5156** |

# Experiment Scenario
<p align="center">
    <img src="architecture.png" width="572" height="292" />
</p>
<p align="justify">The prediction system is seen as classification problem with two target sentiment classes, i.e., positive and negative. Since this paper uses four predictors, the experiments are performed based on four scenarios. Each of the scenario involves three prediction settings, i.e., original dataset with feature selection, balanced dataset with feature selection, and balanced dataset with feature selection and hyper-parameter optimization. This paper uses Chi-Square for feature selection and random over sampling for data balancing. Since the format of generated features are tabular, the XGBoost is the most appropriate option for classification algorithm due to the superior performances in many experiments. Notably, all scenarios will be applied to all review aspects and the classification performance of each paper is measured using accuracy and the number of features for obtaining the best results.</p>

# Results

| Aspect Review | Predictors | N | Acc. (%) | N | Acc. (%) | N | Acc. (%) |
|------|---|---|---|---|---|---|---|
| Clarity | citing sentence | 12 | 57.25 | 7 | 55.51 | 18 | 57.79 |
| | regular sentence | 1 | 55.29 | 20 | 57.03 | 19 | 54.37 |
| | reference-based | 9 | 56.08 | 6 | 58.94 | 11 | 59.70 |
| | combination | 63 | 60.78 | 41 | 61.22 | 46 | 60.46 |
| Meaningful Comparison | citing sentence | 2 | 87.98 | 15 | 92.01 | 20 | 92.97 |
| | regular sentence | 12 | 86.34 | 10 | 92.97 | 10 | 93.61 |
| | reference-based | 7 | 85.25 | 15 | 92.01 | 15 | 92.01 |
| | combination | 62 | 86.34 | 58 | 93.93 | 62 | 93.61 |
| Motivation | citing sentence | 1 | 67.08 | 18 | 76.92 | 15 | 65.02 |
| | regular sentence | 6 | 69.55 | 15 | 76.92 | 15 | 71.19 |
| | reference-based | 5 | 71.19 | 13 | 79.29 | 13 | 77.43 |
| | combination | 43 | 83.73 | 44 | 93.08 | 41 | 78.06 |
| Originality | citing sentence | 22 | 94.07 | 20 | 96.38 | 14 | 94.07 |
| | regular sentence | 18 | 91.65 | 19 | 96.38 | 18 | 94.07 |
| | reference-based | 14 | 85.31 | 15 | 92.36 | 21 | 96.38 |
| | combination | 49 | 97.29 | 49 | 97.29 | 50 | 97.74 |
| Replicability | citing sentence | 26 | 57.83 | 2 | 54.76 | 20 | 52.21 |
| | regular sentence | 38 | 67.10 | 20 | 59.44 | 17 | 58.33 |
| | reference-based | 15 | 77.12 | 15 | 72.73 | 16 | 57.43 |
| | combination | 61 | 57.79 | 56 | 55.56 | 54 | 51.59 |
| Soundness | citing sentence | 54 | 54.37 | 59.70 |  |  |  |  |
| | regular sentence | 17 | 70.56 | 19 | 76.18 | 20 | 61.11 |
| | reference-based | 19 | 79.62 | 14 | 70.56 | 19 | 57.54 |
| | combination | 24 | 78.06 | 61 | 79.94 | 53 | 79.62 |
| Substance | citing sentence |  |  |  |  |  |  |  |
| | regular sentence |  |  |  |  |

