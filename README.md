# Flight Price Prediction AWS Sagemaker

## Project Overview
This project focuses on predicting flight prices using machine learning techniques. The dataset used for this project includes various features such as airline, source, destination, departure time, and more. The model was trained using XGBoost on AWS SageMaker and deployed as a REST API using Flask, as well as a web application using Streamlit.

##  Live Demo
Flask APP and API : [click here](https://flask-ml-project-flight-price-prediction.onrender.com/)

Streamlit APP : [click here](https://flight-price-prediction-aws-sagemaker-machine-learning-project.streamlit.app/)

## Project Architecture
The project is divided into three major sections: **Data Preprocessing & Feature Engineering**, **Model Training**, and **Model Serving & Deployment**.

### 1. Data Preprocessing & Feature Engineering
- **Environment:** Local Machine
- **Files:** 
  - `data_cleaning.ipynb`: Handles missing values, duplicates, and basic data cleaning.
  - `EDA.ipynb`: Explores the data to understand the relationships between features and the target variable.
  - `feature_engineering.ipynb`: Constructs new features and transforms existing ones to improve model performance.
  - `eda_helper_functions.py`: Contains helper functions used in the EDA notebook.
  - **Data Folder:**
    - `train.csv`, `test.csv`, `validation.csv`: The split datasets used for training, validation, and testing.

### 2. Model Training
- **Environment:** AWS SageMaker
- **Files:**
  - `model_training.ipynb`: Trains the XGBoost model using the preprocessed data.
  - `train_preprocessed`, `test_preprocessed`, `validation_preprocessed`: Processed datasets used for training and evaluating the model.
  - `preprocessor.pkl`: The serialized preprocessor used for transforming new data.
  - `xgboost-model`: The final trained model.

### 3. Model Serving & Deployment
- **Environment:** Local Machine or Cloud
- **Files:**
  - `app.py`: Contains the Flask API to serve predictions.
  - `streamlit-app.py`: Contains the Streamlit App to serve predictions.
  - `custom_functions.py`: Custom preprocessing functions used in both Flask and Streamlit app.
  - `forms.py`: Manages the form inputs for the web interface.
  - `requirements.txt`: Lists all dependencies required to run the Flask app.
  - `streamlit-requirements.txt`: Lists all dependencies required to run the Streamlit app.
  - **Templates Folder:**
    - `home.html`, `layout.html`, `predict.html`, `api_guide.html`: HTML files for the Flask web interface.
  - **Streamlit App:** Deploys the model using Streamlit for easy interaction.

## Project Setup
### Prerequisites
- Python 3.8 or later
- Anaconda or any Python environment manager
- Jupyter Notebook
- AWS account with access to SageMaker
- Libraries mentioned in `requirements.txt`

### Installation
1. Clone the repository:
   ```bash
   git clone https://github.com/MJshah001/Tokyo-Olympics-DataAnalysis-Azure-DataEngineering-Project.git
   cd flight-price-prediction
2. Create a Virtual Environment
   ```bash
   conda create --name flight-price-env python=3.8
   conda activate flight-price-env
3. Install dependencies
   ```bash
   pip install -r requirements.txt

### Data Preprocessing & Feature Engineering
1. Run the `data_cleaning.ipynb` notebook to clean the data.
2. Perform exploratory data analysis using `EDA.ipynb`.
3. Generate and save new features with `feature_engineering.ipynb`.

### Model Training
1. Upload the preprocessed data to your AWS S3 bucket.
2. Open `model_training.ipynb` on SageMaker and train the XGBoost model.
3. Save the trained model and preprocessor to the S3 bucket for deployment.

### Deployment
1. To deploy using Flask, run:
   ```bash
   python app.py
2. To deploy using Streamlit, run:
   ```bash
   streamlit run app.py

## Flight Price Prediction API

This guide will help you understand how to interact with the API endpoint for predicting flight prices.

### API Endpoint

```bash
https://flask-ml-project-flight-price-prediction.onrender.com/api/predict
```

### Request Format
The request should have the following format and include the Content-Type: `application/json` in headers:

```bash
{
    "airline": "Air India",
    "date_of_journey": "2024-08-16",
    "source": "Delhi",
    "destination": "Cochin",
    "dep_time": "13:20:00",
    "arrival_time": "15:20:00",
    "duration": 2000,
    "total_stops": 10,
    "additional_info": "Business Class"
}
```
### Inputs

Here are the possible values and formats for each input field:

- **Airline**:
    - Air India
    - Jet Airways
    - Indigo
    - Multiple Carriers
    - Spicejet
    - Vistara
    - Air Asia
    - Goair
    - Trujet

- **Date of Journey**:
    - Format: `YYYY-MM-DD`

- **Source**:
    - Delhi
    - Kolkata
    - Banglore
    - Mumbai
    - Chennai

- **Destination**:
    - Cochin
    - Banglore
    - New Delhi
    - Delhi
    - Hyderabad
    - Kolkata

- **Departure Time**:
    - Format: `HH:MM:SS`

- **Arrival Time**:
    - Format: `HH:MM:SS`

- **Duration**:
    - Format: `Integer (in minutes)`

- **Total Stops**:
    - Format: `Integer`

- **Additional Info**:
    - No Info
    - In-flight meal not included
    - 1 Long layover
    - No check-in baggage included
    - Change airports
    - Red-eye flight
    - Business class
    - 1 Short layover
    - 2 Long layover


### Example Request Using curl :

`curl` is a command-line tool used for making HTTP requests. Here’s an example of how to use `curl` to send a request to the API:

```bash
curl -X POST https://flask-ml-project-flight-price-prediction.onrender.com/api/predict \
     -H "Content-Type: application/json" \
     -d '{
         "airline": "Air India",
         "date_of_journey": "2024-08-16",
         "source": "Delhi",
         "destination": "Cochin",
         "dep_time": "13:20:00",
         "arrival_time": "15:20:00",
         "duration": 2000,
         "total_stops": 10,
         "additional_info": "Business Class"
     }'

```

### Response Format

The API will return a JSON response with the predicted flight price. An example response might look like this:

```bash
{
    "prediction": 13435.7
}
```
Find more details on https://flask-ml-project-flight-price-prediction.onrender.com/api/help


## Flight Price Prediction using UI

Option 1. Flask app UI: https://flask-ml-project-flight-price-prediction.onrender.com/predict

Option 2: Streamlit app: https://flight-price-prediction-aws-sagemaker-machine-learning-project.streamlit.app/


## Challenges & Learnings

- **Data Cleaning:**Handling Inconsistent Data Formats missing Values and Anomalies
- **Feature Engineering:** Creating new features to capture important relationships.
- **Model Tuning:** Hyperparameter tuning to improve model performance.
- **Deployment:** Deploying the model as both an API and a web app using Flask and Streamlit.

## Future Work

- Improve model accuracy with additional features and data.
- Integrate with more advanced deployment options like Docker or Kubernetes.
- Develop an API endpoiont & user interface on the web app for model retraining with new training data.

## Conclusion

This project demonstrates the entire lifecycle of a data science machine learning project, from data preprocessing and model training to deployment and API integration. It served as a valuable learning experience in handling real-world data and deploying machine learning models.

## Author

- **Monil Shah** - _Master's Student in Data Science, NJIT_

## Acknowledgements

Special Thanks to [Mohammed Misbahullah Sheriff ](https://www.linkedin.com/in/mohammed-misbahullah-sheriff/) for beautifully explaining EDA & AWS Cloud Concepts which helped consistently throught the project.



