---

🚗 Car Price Prediction using Machine Learning, FastAPI & Streamlit

📌 Project Overview

This project is an end-to-end Car Price Prediction System that uses Machine Learning to estimate the selling price of a used car based on several features such as the car's name, company, manufacturing year, kilometers driven, and fuel type.

The project is built using a complete deployment pipeline consisting of:

🧠 Machine Learning (Linear Regression)

⚡ FastAPI (Backend API)

🎨 Streamlit (Interactive Frontend)

🐳 Docker (Containerization)


The main objective of this project is to provide users with a simple web application where they can enter car details and instantly obtain an estimated market price.


---

🎯 Project Objectives

✅ Predict the selling price of used cars accurately.

✅ Build a scalable Machine Learning application.

✅ Create a REST API using FastAPI.

✅ Develop an interactive user interface using Streamlit.

✅ Containerize the application using Docker.

✅ Demonstrate an end-to-end Machine Learning deployment workflow.


---

🏗️ Project Architecture

User
                   │
                   │
                   ▼
      🎨 Streamlit Frontend
                   │
                   │ API Request
                   ▼
        ⚡ FastAPI Backend
                   │
                   │
                   ▼
     🧠 Machine Learning Model
                   │
                   │
                   ▼
      💾 Predicted Car Price


---

📂 Project Structure

car-price-prediction-fastapi-streamlit/
│
├── app/
│   ├── main.py
│   └── model/
│
├── frontend/
│   └── app.py
│
├── notebook/
│   └── car_price_prediction.ipynb
│
├── artifacts/
│   ├── model.pkl
│   └── cleaned_car.csv
│
├── Dockerfile
├── requirements.txt
└── README.md


---

🛠️ Technologies Used

Technology	Purpose

🐍 Python	Programming Language
🧠 Scikit-Learn	Machine Learning Model
🐼 Pandas	Data Processing
🔢 NumPy	Numerical Computations
⚡ FastAPI	Backend API Development
🎨 Streamlit	Frontend User Interface
📦 Uvicorn	ASGI Server
🐳 Docker	Application Containerization



---

📊 Dataset Features

The model uses the following input features:

Feature	Description

🚘 Name	Name of the Car
🏢 Company	Manufacturer
📅 Year	Manufacturing Year
🛣️ Kms Driven	Total Kilometers Driven
⛽ Fuel Type	Type of Fuel



---

🧠 Machine Learning Workflow

The Machine Learning pipeline follows these steps:

1️⃣ Data Collection

Import the dataset.

Analyze the available features.


2️⃣ Data Cleaning

Remove missing values.

Standardize the dataset.

Convert data types.


3️⃣ Exploratory Data Analysis (EDA)

Analyze relationships between variables.

Identify important factors affecting price.


4️⃣ Feature Engineering

Select relevant features.

Encode categorical variables.


5️⃣ Model Training

The project uses:

Linear Regression

6️⃣ Model Evaluation

Performance is evaluated using:

Mean Absolute Error (MAE)

Mean Squared Error (MSE)

R² Score



---

⚡ FastAPI Backend

FastAPI is responsible for:

Receiving user input.

Validating data.

Passing input to the ML model.

Returning the predicted price.


API Endpoint

POST /predict


---

🎨 Streamlit Frontend

The Streamlit application provides a user-friendly interface where users can:

Select the car name.

Select the company.

Enter the manufacturing year.

Enter kilometers driven.

Select fuel type.

Predict the estimated car price instantly.



---

🐳 Docker Support

This project is containerized using Docker for easy deployment.

Build Docker Image

docker build -t car-price-prediction .

Run Docker Container

docker run -p 8000:8000 car-price-prediction


---

⚙️ Installation Guide

Step 1: Clone the Repository

git clone https://github.com/debasmita-sen/car-price-prediction-fastapi-streamlit.git

cd car-price-prediction-fastapi-streamlit


---

Step 2: Create Virtual Environment

Windows

python -m venv venv

venv\Scripts\activate

Mac/Linux

python3 -m venv venv

source venv/bin/activate


---

Step 3: Install Dependencies

pip install -r requirements.txt


---

Step 4: Run FastAPI Backend

uvicorn app.main:app --reload

FastAPI will run at:

http://127.0.0.1:8000


---

Step 5: Run Streamlit Frontend

streamlit run frontend/app.py

Streamlit will run at:

http://localhost:8501


---

💡 How to Use

1️⃣ Open the Streamlit application.

2️⃣ Enter:

Car Name

Company

Year

Kilometers Driven

Fuel Type


3️⃣ Click Predict Price.

4️⃣ View the estimated car price instantly.


---

🚀 Future Enhancements

Some possible improvements include:

📈 Use advanced models like XGBoost and Random Forest.

🌐 Deploy the application on AWS or Render.

🔐 Add user authentication.

📊 Create interactive dashboards.

📱 Make the UI mobile responsive.

☁️ Integrate cloud databases.



---

📷 Sample Workflow

User Input
     ↓

Streamlit UI

     ↓

FastAPI API

     ↓

ML Model Prediction

     ↓

Estimated Car Price


---

🎓 Learning Outcomes

This project demonstrates:

✔️ Data Cleaning

✔️ Exploratory Data Analysis

✔️ Feature Engineering

✔️ Machine Learning Model Building

✔️ API Development

✔️ Frontend Development

✔️ Docker Containerization

✔️ End-to-End ML Deployment


---

👩‍💻 Author

Debasmita Sen

📧 Email: debasmita.sen123@gmail.com

🐙 GitHub: [debasmita-sen](https://github.com/debasmita-sen?utm_source=chatgpt.com)

🔗 Repository: [Car Price Prediction - FastAPI & Streamlit](https://github.com/debasmita-sen/car-price-prediction-fastapi-streamlit?utm_source=chatgpt.com)


---

⭐ If you found this project useful, don't forget to star the repository!

Happy Coding 🚀
