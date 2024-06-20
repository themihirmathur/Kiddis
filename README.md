# Kidney Disease Classification with MLflow and DVC

This project leverages deep learning for the classification of kidney disease using a combination of MLflow and DVC for experiment tracking, versioning, and orchestration. The project encompasses a structured workflow, facilitating both experimentation and production-grade deployment.

![image](https://github.com/themihirmathur/Kiddis/assets/92594107/259ebb73-f060-4864-8b34-ed188e67a50e)

## Workflows

### Configuration Files
- **config.yaml**: General configuration settings.
- **secrets.yaml**: Optional file for sensitive information.
- **params.yaml**: Parameters for model training and evaluation.

### Source Code Updates
1. Update the entity definitions.
2. Enhance the configuration manager in the `src` config directory.
3. Revise the components for improved functionality.
4. Update the pipeline to reflect changes.
5. Modify `main.py` to incorporate new logic.
6. Amend `dvc.yaml` for Data Version Control.

### Application Entry Point
- `app.py`: Main application file to run the project.

## Running the Project

### Clone the Repository
```sh
git clone https://github.com/krishnaik06/Kidney-Disease-Classification-Deep-Learning-Project
cd Kidney-Disease-Classification-Deep-Learning-Project
```

### Create and Activate Conda Environment
```sh
conda create -n cnncls python=3.8 -y
conda activate cnncls
```

### Install Requirements
```sh
pip install -r requirements.txt
```

### Run the Application
```sh
python app.py
```
Now, open your local host and port to access the application.

## MLflow Integration

MLflow is used to track experiments, log models, and facilitate model deployment.

### Starting MLflow UI
```sh
mlflow ui
```

### Setting up MLflow with DagsHub
```sh
export MLFLOW_TRACKING_URI=https://dagshub.com/entbappy/Kidney-Disease-Classification-MLflow-DVC.mlflow
export MLFLOW_TRACKING_USERNAME=entbappy 
export MLFLOW_TRACKING_PASSWORD=6824692c47a369aa6f9eac5b10041d5c8edbcef0
python script.py
```

## DVC Commands

DVC is utilized for lightweight experiment tracking and pipeline orchestration.

### Initialize DVC
```sh
dvc init
```

### Reproduce DVC Pipeline
```sh
dvc repro
```

### Visualize DVC Pipeline
```sh
dvc dag
```

## About MLflow & DVC

### MLflow
- **Production Grade**: Suitable for production environments.
- **Experiment Tracking**: Logs and tags models and experiments.

### DVC
- **Lightweight**: Ideal for proof-of-concept projects.
- **Experiment Tracker**: Manages and tracks experiments.
- **Pipeline Orchestration**: Enables creation and management of pipelines.

## AWS CI/CD Deployment with GitHub Actions

This section describes the steps to deploy the application using AWS services and GitHub Actions for continuous integration and continuous deployment.

### Steps to Deploy

1. **Login to AWS Console**: Access your AWS management console.
2. **Create IAM User for Deployment**: Assign specific access permissions:
   - EC2 Access
   - ECR Access

### Deployment Description
1. **Build Docker Image**: Create a Docker image of the source code.
2. **Push Docker Image to ECR**: Store the Docker image in AWS Elastic Container Registry (ECR).
3. **Launch EC2 Instance**: Create an EC2 instance to host the application.
4. **Pull Docker Image from ECR**: Retrieve the Docker image from ECR in the EC2 instance.
5. **Run Docker Image in EC2**: Deploy and run the Docker container in the EC2 instance.

### IAM Policies Required
- `AmazonEC2ContainerRegistryFullAccess`
- `AmazonEC2FullAccess`

### Create ECR Repository
```sh
aws ecr create-repository --repository-name kidney-disease-classification
```

### Create EC2 Instance
1. **Launch EC2 Instance (Ubuntu)**
2. **Install Docker on EC2**
   ```sh
   sudo apt-get update -y
   sudo apt-get upgrade
   curl -fsSL https://get.docker.com -o get-docker.sh
   sudo sh get-docker.sh
   sudo usermod -aG docker ubuntu
   newgrp docker
   ```

### Configure EC2 as Self-Hosted Runner
1. Go to `Settings > Actions > Runners` in GitHub.
2. Add a new self-hosted runner and follow the instructions to configure it.

### Setup GitHub Secrets
```sh
AWS_ACCESS_KEY_ID=<your_aws_access_key_id>
AWS_SECRET_ACCESS_KEY=<your_aws_secret_access_key>
AWS_REGION=us-east-1
AWS_ECR_LOGIN_URI=566373416292.dkr.ecr.us-east-1.amazonaws.com
ECR_REPOSITORY_NAME=kidney-disease-classification
```

---

This project demonstrates a comprehensive approach to developing, experimenting, and deploying a deep learning model for kidney disease classification using modern MLOps tools and practices.
