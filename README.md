# The Healthcare Data Hub: A Centralized Platform for Informed Decision-Making

This project involves containerizing a Streamlit application using Docker, then deploying it on a Kubernetes cluster using deployment and service configuration files. The Dockerfile ensures that the application runs in a consistent environment, while the Kubernetes configuration files manage the deployment and networking aspects, making the application accessible to users.

# Healthcare Data Pipeline

## Modular Code Overview
```sh
healthcare-data-pipeline/
├── app/
│   ├── app.py
│   ├── requirements.txt
│   ├── data/
│   │   ├── fetch_patients.py
│   │   ├── fetch_facilities.py
│   │   ├── generate_healthcare_data.py
│   │   ├── generate_medication_data.py
│   ├── transform/
│   │   ├── transform_patients.py
│   │   ├── assign_services_to_patients.py
│   │   ├── assign_medications_to_patients.py
│   ├── visualize/
│   │   ├── visualize_service_cost_distribution.py
│   │   ├── visualize_medication_cost_distribution.py
│   │   ├── visualize_service_count_by_type.py
│   │   ├── visualize_medication_cost_over_time.py
├── docker/
│   ├── Dockerfile
│   ├── requirements.txt
├── kubernetes/
│   ├── deployment.yaml
│   ├── service.yaml
├── utils/
│   ├── utils.py
├── README.md
```

### 1. Application (`healthcarepipeline.py`)

The `app.py` file contains the Python code for the Streamlit application.

#### Data Fetching

* `fetch_patients()`: Retrieves 50 random patient records from an external API.
* `fetch_facilities()`: Retrieves healthcare facility data from an external API.

#### Data Generation

* `generate_healthcare_data(num_records)`: Generates random healthcare service data.
* `generate_medication_data(num_records)`: Generates random medication data.

#### Data Transformation

* `transform_patients(data)`: Transforms raw patient data into a structured format.
* `assign_services_to_patients(patients, services)`: Assigns healthcare services to patients.
* `assign_medications_to_patients(patients, medications)`: Assigns medications to patients.

#### Visualizations

* Bar charts for service cost distribution, medication cost distribution, and service count by type.
* A line chart for medication cost over time.


### 2. Docker Setup (`Dockerfile`)

The `Dockerfile` is used to containerize the Streamlit application. The following elements are typically included:

#### Dockerfile Specifications

```dockerfile
# Specifies the base image (usually a Python image)
FROM python:3.9-slim

# Installs the required Python packages
COPY requirements.txt .
RUN pip install -r requirements.txt

# Copies the application files into the Docker image
COPY . .

# Exposes the necessary port for the Streamlit application
EXPOSE 8501

# Command to start the Streamlit app
CMD ["streamlit", "run", "app.py"]
```
