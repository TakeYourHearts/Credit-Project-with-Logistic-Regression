1. Business Understand.

    The objective of this project is to design and implement a credit scoring model capable of ranking clients according to their probability of default. The model will be developed using logistic regression as the primary statistical method. Model performance will be evaluated and validated through discriminatory power metrics, specifically the Area Under the Receiver Operating Characteristic Curve (AUC) and the Kolmogorov-Smirnov (KS) statistic.

2. Data Understanding.

    The dataset employed in this project is the Give Me Some Credit dataset, publicly available on Kaggle (https://www.kaggle.com/c/GiveMeSomeCredit). Kaggle provides multiple files associated with the competition, including training, test, sample entry, and submission files. For the purposes of this study, emphasis is placed on the test.csv file.
    The test.csv file contains over 100,000 observations and 12 predictor variables. The key target variable is SeriousDlqin2yrs, a binary indicator denoting whether an individual has experienced a 90-day past-due delinquency or worse within a two-year horizon. This variable serves as the dependent feature for model training and evaluation, enabling the construction of a supervised learning framework for credit risk prediction.


3. Data Preparation.

    Before applying any data‑processing steps, we first perform a train–test split to avoid data leakage. This ensures that all transformations are learned exclusively from the training set and only applied to the test set afterward.

    The variable NumberOfTimes90DaysLate is preserved because it reflects historical delinquency behavior, one of the strongest predictors of credit risk.

    Due to the asymmetric distribution of the income variable, and to prevent the short tail from distorting the model, we apply normalization and a logarithmic transformation to stabilize its distribution.

    For DebtRatio, we adjust the variable to better reflect realistic financial behavior. Extremely high values—representing abnormal debt levels—are capped to reduce the influence of outliers.

    Similarly, the IncomeNotProvided flag carries behavioral information: clients who voluntarily report income often have a different relationship with the institution. For this reason, we combine this indicator with the income variable to strengthen the model’s predictive power.

    Finally, variables with low contribution or unstable behavior are removed to improve the model’s robustness, interpretability, and overall performance.

4. Modeling. 

    Logistic Regression

    The choice of logistic regression follows directly from the nature of the problem. We do not only need to identify who will default; we also need to estimate how likely each client is to default and understand how each variable contributes to that risk.

    Logistic Regression is suitable for this purpose because it provides transparent interpretability: it quantifies how much each factor influences the predicted outcome, which helps resolve the challenge of understanding the impact of each variable or category. Another important advantage is the stability of the model. Logistic Regression is less prone to severe overfitting and is generally more resilient to noise compared to more complex algorithms.

    For these reasons, logistic regression has become a market standard in credit risk modeling. It allows organizations to extract insights from the data, understand variable relationships, and generate direct, interpretable probability estimates that support credit decision‑making.

    KS + AUC :

    The AUC (Area Under the ROC Curve) provides a global assessment of model performance. It indicates how well the model discriminates between classes across all possible cutoff points. Because it is robust, cutoff‑independent, and summarizes the model’s overall discriminatory power, it is the natural choice for evaluating the model at a strategic level.

    The KS (Kolmogorov–Smirnov statistic), on the other hand, is particularly effective for separating good and bad clients. It is widely used in credit risk because it reflects how well the model supports operational credit decisions, which may vary depending on each organization’s credit policy.

    Using both metrics is important because they serve complementary purposes:

    AUC offers a strategic, holistic view of model performance across the entire client base.

    KS provides an operational perspective, showing how effectively the model distinguishes risk segments in alignment with credit policy.


5. Evaluation. 

    This project demonstrates the development of a credit risk model focused on ranking clients according to their probability of default.

    From a business perspective, such models are essential for financial institutions, as they support decisions related to credit approval, pricing, and risk management.

    Even with a relatively simple and interpretable model (logistic regression), the results show consistent discriminatory power (AUC ≈ 0.66 and KS ≈ 0.24), which is aligned with baseline models commonly used in credit scoring.

    A key strength of this project is the emphasis on methodological correctness, particularly the avoidance of data leakage and the use of appropriate evaluation metrics (AUC and KS), ensuring that the model reflects realistic performance in production scenarios.

    Additionally, the project highlights the importance of feature engineering and economic interpretation, reinforcing that in credit risk modeling, understanding the drivers of default is as important as predictive performance.
