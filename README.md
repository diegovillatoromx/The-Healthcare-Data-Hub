# The Healthcare Data Hub: A Centralized Platform for Informed Decision-Making

This project involves containerizing a Streamlit application using Docker, then deploying it on a Kubernetes cluster using deployment and service configuration files. The Dockerfile ensures that the application runs in a consistent environment, while the Kubernetes configuration files manage the deployment and networking aspects, making the application accessible to users.

# Modular Code Overview

The Healthcare Data Pipeline project is divided into the following modules:

### 1. `app`

* `app.py`: Main application file
* `requirements.txt`: Dependencies required to run the application

### 2. `data`

* `fetch_patients.py`: Fetches patient data from external API
* `generate_healthcare_data.py`: Generates synthetic healthcare data
* `generate_medication_data.py`: Generates synthetic medication data
* `fetch_facilities.py`: Fetches healthcare facility data from external API

### 3. `transform`

* `transform_patients.py`: Transforms raw patient data into structured format
* `assign_services_to_patients.py`: Assigns healthcare services to patients
* `assign_medications_to_patients.py`: Assigns medications to patients

### 4. `visualize`

* `visualize_service_cost_distribution.py`: Visualizes service cost distribution
* `visualize_medication_cost_distribution.py`: Visualizes medication cost distribution
* `visualize_service_count_by_type.py`: Visualizes service count by type
* `visualize_medication_cost_over_time.py`: Visualizes medication cost over time

### 5. `utils`

* `utils.py`: Utility functions for data processing and visualization
