# Method and Approach
1. Loading the Data:

    - Features and labels are loaded from separate CSV files.
    - The datasets are merged on the respondent_id column to create a unified DataFrame.

2. Preprocessing:

    - Missing Values: Categorical columns have missing values filled with the mode (most frequent value), and numerical columns are filled with the median.
    - Separate Features and Targets: The features (X) and target variables (y) are separated after merging the datasets.

3. Feature Identification:

    - Categorical Features: Columns that contain categorical data such as age_group, education, etc.
    - Numerical Features: Columns that contain numerical data. These are identified as all columns not in the list of categorical features.

4. Preprocessor Setup:

    - Numerical Data: Standardized using StandardScaler.
    - Categorical Data: Encoded using OneHotEncoder, which converts categorical variables into a form that can be provided to ML algorithms to do a better job in prediction.

5. Model Definition:

    - A RandomForestClassifier is used within a MultiOutputClassifier to handle the multilabel classification problem where each target variable (vaccine) is predicted separately.
    - A pipeline is created to streamline the preprocessing and model training steps.

6. Training and Validation:

    - The data is split into training and validation sets.
    - The model is trained on the training data.
    - Predictions are made on the validation set, and the model’s performance is evaluated using the ROC AUC score, which measures the ability of the classifier to distinguish between classes.

7. Test Data Handling:

    - The test data is loaded and preprocessed similarly to the training data.
    - Predictions are made on the test data to generate probabilities for each target variable.

8. Submission Preparation:

    - A submission DataFrame is created with respondent_id and predicted probabilities for xyz_vaccine and seasonal_vaccine.
    - The submission is saved to a CSV file.
