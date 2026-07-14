Rising Waters: Flood Prediction System
Rising Waters focuses on addressing the growing risk of floods, which have become increasingly frequent and severe due to factors such as climate change, unpredictable weather patterns, rapid urbanization, deforestation, and inadequate drainage and water management systems. Floods can have devastating consequences, including loss of human life, displacement of communities, destruction of homes and infrastructure, agricultural damage, economic losses, and long-term environmental impacts. As populations continue to grow and weather conditions become more extreme, the need for accurate flood prediction and effective disaster preparedness has become more critical than ever.

This project aims to leverage the power of data analysis and machine learning to develop a flood prediction system capable of identifying potential flood risks before they occur. By analyzing historical weather data, rainfall patterns, water levels, and other relevant environmental factors, the system can detect trends and generate predictions that support early warning mechanisms. These insights enable government agencies, disaster management authorities, and local communities to take proactive measures, such as issuing alerts, planning evacuations, and implementing preventive strategies.

In addition to improving disaster response, flood prediction systems contribute to better resource allocation, infrastructure planning, and environmental management. Early identification of high-risk areas helps reduce damage, minimize economic losses, and improve public safety. The integration of intelligent prediction models into disaster management frameworks can significantly enhance preparedness and resilience against flood-related events.

Ultimately, Rising Waters demonstrates how data-driven technologies can be used to tackle real-world environmental challenges. By providing timely and reliable flood risk assessments, the project supports informed decision-making and helps protect lives, property, and ecosystems from the increasing threats posed by flooding in a changing world.

The system compares classification algorithms such as Decision Tree, Random Forest, K-Nearest Neighbors, and XGBoost. The best-performing trained model is saved and connected to a Flask web application, where users can enter weather values and receive an instant flood-risk prediction. The application is prepared for deployment on Render, so it can be accessed online after being pushed to GitHub.

It includes:

Data generation and loading
Data exploration and visualization
Data preprocessing
Model training and comparison
Final model saving
Flask web application
SQLite database schema
ER diagram source
Project Scenarios
Scenario 1: Early Flood Warning
A meteorologist enters current temperature, humidity, cloud cover, annual rainfall, and June to September rainfall values for a flood-prone area. The system analyses the inputs and predicts whether flood risk is likely, helping authorities take early action.

Scenario 2: Disaster Response Planning
A disaster relief coordinator enters weather data for different regions one by one. The prediction results help compare flood risk levels and support better resource planning during monsoon season.

Scenario 3: Model Validation
An analyst can retrain and compare multiple machine learning models using the training script. The final selected model and evaluation results are stored in the models/ folder for review and deployment.

Project Structure
ai-ml/
  app.py
  requirements.txt
  README.md
  data/
    flood_dataset.csv
  diagrams/
    er_diagram.mmd
  models/
    floods.save
    transform.save
    metrics.json
  notebooks/
    beginner_workflow.py
  scripts/
    create_sample_dataset.py
    train_model.py
  sql/
    schema.sql
  static/
    main.css
    main.js
  templates/
    home.html
    index.html
    chance.html
    no_chance.html
1. Install Python Packages
py -3.13 -m pip install -r requirements.txt
Use Python 3.13 for this project. Python 3.14 is installed on this machine, but some data-science packages may not have stable wheels for it yet.

2. Create the Dataset
py -3.13 scripts/create_sample_dataset.py
This creates data/flood_dataset.csv.

3. Train the Models
py -3.13 scripts/train_model.py
This trains and compares:

Decision Tree
Random Forest
K-Nearest Neighbors
XGBoost
Gradient Boosting fallback
The best model is saved as models/floods.save.

The fitted scaler is saved as models/transform.save.

4. Run the Flask App
py -3.13 app.py
Open this URL in your browser:

http://127.0.0.1:5000/
Deploy on Render
Push this project to GitHub, then create a Render Web Service from that repository.

Use these settings:

Language: Python 3
Build Command: pip install -r requirements.txt
Start Command: gunicorn app:app
This project also includes render.yaml, so Render can detect the same settings automatically.

Important files for Render:

requirements.txt installs Flask, Gunicorn, scikit-learn, XGBoost, and other packages.
.python-version and render.yaml request Python 3.13.5 because Python 3.14 can cause package build problems for this project.
render.yaml defines the web service build and start commands.
models/floods.save and models/transform.save must be pushed to GitHub because the deployed app loads them at startup.
Input Features
The web app asks for:

Temperature
Humidity
Cloud cover
Annual rainfall
June to September rainfall
The model predicts whether flood risk is likely or not.

Database Design
The database schema is in:

sql/schema.sql
The ER diagram source is in:

diagrams/er_diagram.mmd
You can paste the Mermaid ER diagram into https://mermaid.live to view it visually.

The running Flask app stores prediction history in:

%TEMP%\rising_waters\flood_prediction.db
This avoids SQLite write problems in OneDrive-backed folders. To choose another location, set the FLOOD_DATABASE environment variable before starting app.py.

Beginner Notes
The file notebooks/beginner_workflow.py is written like a notebook. Run it step by step to understand the project workflow.

Important Correction
Your report text mentions "Loan Approval Prediction System" in one place, but the actual project is a Flood Prediction System. This project consistently uses flood prediction entities, fields, and model outputs.
