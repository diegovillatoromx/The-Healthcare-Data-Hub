# The Healthcare Data Hub: A Centralized Platform for Informed Decision-Making

This project involves containerizing a Streamlit application using Docker, then deploying it on a Kubernetes cluster using deployment and service configuration files. The Dockerfile ensures that the application runs in a consistent environment, while the Kubernetes configuration files manage the deployment and networking aspects, making the application accessible to users.

# Healthcare Data Pipeline

## Modular Code Overview

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

The `Dockerfile` is used to containerize the Streamlit application.

#### Base Image

* Specifies the base image (usually a Python image) to build upon.

#### Dependency Installation

* Installs the required Python packages.

#### Copy Application Files

* Copies the application files into the Docker image.

#### Port Exposure

* Exposes the necessary port for the Streamlit application.

#### Run Command

* Specifies the command to start the Streamlit app.

### 3. Kubernetes Deployment Configuration (`deployment.yaml`)

The `deployment.yaml` file is used to define the Kubernetes deployment.

#### Metadata

* Information such as the deployment name.

#### Spec

* Details about the replicas, Docker image to use, and the ports.

#### Containers

* Defines the container specifications, including image and ports.

### 4. Kubernetes Service Configuration (`service.yaml`)

The `service.yaml` file configures how the application is exposed to the network.

#### Metadata

* Information such as the service name.

#### Spec

* Details about the service type (ClusterIP, NodePort, or LoadBalancer) and the ports.
