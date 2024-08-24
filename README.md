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

The `Dockerfile` is a critical component of the containerization process, serving as a blueprint for building a Docker image that encapsulates the Streamlit application.

#### Dockerfile Elements

```markdown
### Base Image Specification
Specifies the foundation of the Docker image, typically leveraging a Python-based image as the starting point for the build process.

### Dependency Installation
Ensures the installation of requisite Python packages, satisfying the application's dependencies and facilitating seamless execution.

### Application File Inclusion
Copies the application's source files into the Docker image, ensuring that all necessary components are present for successful execution.

### Port Exposure
Exposes the requisite port, enabling communication with the Streamlit application and facilitating user interaction.

### Run Command Specification
Defines the command invoked to initiate the Streamlit application, orchestrating the execution of the app within the containerized environment.
#### Dockerfile Specifications

```dockerfile
FROM python:3.9   
WORKDIR /app
COPY . /app
RUN pip install streamlit pandas requests
EXPOSE 8501
CMD ["streamlit","run","app.py","--server.port=8501","--server.address=0.0.0.0"]
```
