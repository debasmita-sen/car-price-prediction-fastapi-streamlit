Car Price Prediction using FastAPI and Streamlit
A machine learning web application that predicts the estimated price of a used car based on details such as car model, company, manufacturing year, kilometers driven, and fuel type. The project uses a trained Linear Regression model, serves predictions through a FastAPI backend, and provides a simple Streamlit-based frontend for user interaction.
Project Overview
The main objective of this project is to build an end-to-end machine learning application for used car price prediction. Instead of keeping the model only inside a notebook, the trained model is integrated with a backend API and connected to a frontend interface.
The user selects or enters car details in the Streamlit application. These details are sent to the FastAPI backend through an HTTP POST request. The backend loads the trained machine learning model, processes the input, generates the predicted price, and returns the result to the frontend.
This makes the project more practical because it shows how a machine learning model can be deployed and used like a real application.
Features
Predicts used car price based on selected input features.
Uses a trained Linear Regression model.
FastAPI backend for serving the machine learning model.
Streamlit frontend for easy user interaction.
Input validation using Pydantic models.
Dataset included for model development and frontend dropdown values.
Dockerfile included for containerized deployment.
Jupyter notebooks included for model building and Docker/API testing.
Tech Stack
Technology
Purpose
Python
Main programming language
Pandas
Data handling and preprocessing
NumPy
Numerical operations
Scikit-learn
Machine learning model training
Joblib
Loading the saved trained model
FastAPI
Backend API development
Pydantic
Request data validation
Uvicorn
Running the FastAPI server
Streamlit
Frontend web application
Requests
Sending data from frontend to backend API
Docker
Containerizing the backend application
Jupyter Notebook
Model development and experimentation
Project Structure
car-price-prediction-fastapi-streamlit/
│
├── app/
│   ├── main.py
│   └── requirements.txt
│
├── frontend/
│   └── app.py
│
├── model/
│
├── Build_push_test_MLapi_docker_images.ipynb
├── predict-car-price.ipynb
├── Dockerfile
├── LinearRegressionModel.joblib
├── LinearRegressionModel.pkl
├── cars.csv
├── cleaned_car_data.csv
├── requirements.txt
└── README.md
Folder and File Explanation
app/main.py
This file contains the FastAPI backend code. It loads the trained machine learning model using Joblib and exposes API endpoints.
Important parts of this file:
Creates a FastAPI application with the title Car Price Prediction.
Loads the trained model from LinearRegressionModel.joblib.
Defines the input data structure using a Pydantic class.
Provides a health-check endpoint using / or /home.
Provides a prediction endpoint using /predict.
The backend expects the following input fields:
{
  "name": "car model name",
  "company": "company name",
  "year": 2015,
  "kms_driven": 45000,
  "fuel_type": "Petrol"
}
The /predict endpoint converts the received input into a Pandas DataFrame and passes it to the trained model to generate the predicted price.
frontend/app.py
This file contains the Streamlit frontend code. It creates a simple web interface where users can select or enter car details.
The frontend performs the following tasks:
Reads cleaned_car_data.csv to populate dropdown values.
Displays input fields for car model, company, year, kilometers driven, and fuel type.
Sends user input to the FastAPI backend using a POST request.
Displays the predicted car price returned by the backend.
The frontend sends the prediction request to:
http://127.0.0.1:8000/predict
So, the FastAPI backend must be running before using the Streamlit frontend.
predict-car-price.ipynb
This notebook is used for machine learning model development. It includes steps such as loading the dataset, cleaning the data, selecting features, training the Linear Regression model, and saving the trained model.
Build_push_test_MLapi_docker_images.ipynb
This notebook is related to testing or building the machine learning API with Docker. It is useful for understanding how the API can be containerized and tested.
cars.csv
This is the original dataset containing car-related information.
cleaned_car_data.csv
This is the cleaned version of the dataset. It is used by the frontend to display dropdown options such as car names, company names, and fuel types.
LinearRegressionModel.joblib and LinearRegressionModel.pkl
These are saved trained model files. The FastAPI backend currently loads the model using:
model = joblib.load("LinearRegressionModel.joblib")
The model is used to generate predictions from new input data.
requirements.txt
This file contains the Python libraries required to run the project.
Main dependencies include:
fastapi==0.79.0
joblib==1.0.1
numpy==1.19.4
pandas==1.2.4
pydantic==1.8.2
uvicorn==0.18.2
scikit-learn==0.24.1
The specific Scikit-learn version is important because machine learning models saved using one version may sometimes show compatibility warnings or errors when loaded with a different version.
Dockerfile
The Dockerfile is used to create a Docker image for the FastAPI backend. It uses a FastAPI-compatible base image and copies the backend application and model folder into the container.
Machine Learning Workflow
The project follows a standard machine learning workflow:
Data Collection
The project uses a car dataset containing information such as car name, company, manufacturing year, kilometers driven, fuel type, and price.
Data Cleaning
The raw dataset is cleaned to remove inconsistent, missing, or unsuitable values. The cleaned dataset is saved as cleaned_car_data.csv.
Feature Selection
The model uses the following input features:
Car name
Company
Manufacturing year
Kilometers driven
Fuel type
Model Training
A Linear Regression model is trained to learn the relationship between the input features and the car price.
Model Saving
The trained model is saved using Joblib/Pickle so that it can be reused without retraining every time.
API Integration
The saved model is loaded inside the FastAPI backend and exposed through the /predict endpoint.
Frontend Integration
A Streamlit frontend collects user input and sends it to the FastAPI backend for prediction.
How the Application Works
User Input in Streamlit
        ↓
Frontend sends JSON data to FastAPI
        ↓
FastAPI validates the input using Pydantic
        ↓
Input is converted into a Pandas DataFrame
        ↓
Trained Linear Regression model predicts price
        ↓
Prediction is returned to Streamlit
        ↓
User sees the estimated car price
Installation and Setup
1. Clone the Repository
git clone https://github.com/debasmita-sen/car-price-prediction-fastapi-streamlit.git
cd car-price-prediction-fastapi-streamlit
2. Create a Virtual Environment
For Windows:
python -m venv venv
venv\Scripts\activate
For macOS/Linux:
python -m venv venv
source venv/bin/activate
3. Install Dependencies
pip install -r requirements.txt
If Streamlit is not included in the requirements file, install it separately:
pip install streamlit requests
Running the Project
Step 1: Start the FastAPI Backend
From the root project directory, run:
uvicorn app.main:app --reload
The backend will start at:
http://127.0.0.1:8000
You can test whether the backend is running by opening:
http://127.0.0.1:8000/home
Expected response:
{
  "message": "System is healthy"
}
You can also check the automatic FastAPI documentation at:
http://127.0.0.1:8000/docs
Step 2: Start the Streamlit Frontend
Open another terminal and run:
cd frontend
streamlit run app.py
The frontend will usually open at:
http://localhost:8501
Now enter/select the car details and click on the Predict button to get the estimated price.
API Endpoint Details
Health Check Endpoint
GET /
GET /home
Response:
{
  "message": "System is healthy"
}
Prediction Endpoint
POST /predict
Sample request body:
{
  "name": "Maruti Suzuki Swift",
  "company": "Maruti",
  "year": 2016,
  "kms_driven": 45000,
  "fuel_type": "Petrol"
}
Sample response:
350000
The actual output depends on the trained model and the input values.
Running with Docker
The project includes a Dockerfile for containerizing the FastAPI backend.
Build Docker Image
docker build -t car-price-prediction-api .
Run Docker Container
docker run -p 8000:80 car-price-prediction-api
After running the container, the API should be accessible at:
http://127.0.0.1:8000
Example Use Case
Suppose a user wants to estimate the resale value of a used car. The user enters:
Car model: Swift
Company: Maruti
Year: 2016
Kilometers driven: 45,000
Fuel type: Petrol
The Streamlit frontend sends this information to the FastAPI backend. The trained Linear Regression model processes the input and returns an estimated resale price.
This type of application can be useful for:
Used car buyers
Used car sellers
Automobile dealerships
Online car resale platforms
Price comparison systems
Advantages of the Project
Demonstrates an end-to-end machine learning workflow.
Shows how to convert a notebook-based ML model into a usable web application.
Uses FastAPI for fast and clean API development.
Uses Streamlit for a simple and beginner-friendly frontend.
Includes Docker support for easier deployment.
Useful for understanding real-world ML application architecture.
Limitations
The prediction accuracy depends on the quality and size of the dataset.
Linear Regression may not capture complex pricing patterns as effectively as advanced models.
The model may not perform well for car models or companies not present in the training dataset.
External factors such as car condition, accident history, location, insurance status, and market demand are not considered.
The frontend currently depends on the backend running locally at 127.0.0.1:8000.
Future Improvements
Add more features such as transmission type, owner type, mileage, engine capacity, and location.
Improve prediction accuracy using advanced models such as Random Forest, XGBoost, or Gradient Boosting.
Add proper error handling in the frontend and backend.
Display the predicted price in a cleaner currency format.
Deploy the backend and frontend online.
Add a database to store user prediction history.
Add model performance metrics such as R² score, MAE, MSE, and RMSE in the README.
Improve the UI design of the Streamlit application.
Add unit testing for API endpoints.
Conclusion
This project demonstrates how machine learning can be integrated with backend and frontend technologies to create a practical prediction system. The Linear Regression model predicts used car prices, FastAPI serves the model as an API, and Streamlit provides a user-friendly interface. Overall, the project is a good example of deploying a machine learning model as a simple web-based application.
Author
Debasmita Sen
GitHub: debasmita-sen
