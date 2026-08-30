# 🚀 Machine Learning Model Deployment with CI/CD

A complete simple end-to-end Machine Learning project demonstrating the development, continuous integration, continuous deployment, and production deployment of a machine learning model.

The project uses **GitHub Actions** to automate the CI/CD pipeline and deploys the trained machine learning application to **Hugging Face Spaces**.

## 📌 Project Overview

This project demonstrates a complete Machine Learning workflow, from model development to automated deployment.

The main objectives of the project are:

* Build and train a Machine Learning model.
* Develop an application for interacting with the trained model.
* Implement automated testing and validation.
* Configure Continuous Integration (CI) using GitHub Actions.
* Implement Continuous Deployment (CD).
* Automatically deploy the application to Hugging Face.

## 🛠️ Technologies Used

* **Python** – Core programming language.
* **Machine Learning Libraries** – Used for data processing, model development, and evaluation.
* **GitHub** – Version control and source code management.
* **GitHub Actions** – Continuous Integration and Continuous Deployment automation.
* **Hugging Face Spaces** – Deployment and hosting platform.

## 🤖 Machine Learning Workflow

The Machine Learning pipeline consists of the following stages:

### 1. Data Preprocessing

The raw dataset is cleaned and transformed before being used for training. This may include:

* Handling missing values.
* Encoding categorical variables.
* Feature scaling.
* Feature selection.
* Splitting the dataset into training and testing sets.

### 2. Model Training

The processed dataset is used to train the Machine Learning model.

```bash
python train.py
```

The trained model is then saved and used by the application for predictions.

### 3. Model Evaluation

The trained model is evaluated using appropriate performance metrics.

These include:

* Accuracy
* Precision

## ⚙️ CI/CD Pipeline

The project uses **GitHub Actions** to automate the Continuous Integration and Continuous Deployment workflow.

The pipeline is triggered when changes are pushed to the repository.

### Continuous Integration

The CI pipeline performs tasks such as:

* Installing project dependencies
* Train model
  
Example workflow:

```yaml
name: Continuous Integration
on: 
  push:
    branches: [ "main" ]
  pull_request:
    branches: [ "main" ]
  workflow_dispatch:

permissions: write-all
jobs:
  build:
    runs-on: ubuntu-latest
    # container: docker://ghcr.io/iterative/cml:0-dvc2-base1
    steps:
      - uses: actions/checkout@v4
      - uses: actions/setup-python@v5
        with:
          python-version: '3.10' 
          architecture: 'x64' 
      - name: Install Packages
        run: make install
      - name: Format
        run : make format
      - name: Train
        run: make train
      - name: Evaluation
        env:
          REPO_TOKEN: ${{ secrets.GITHUB_TOKEN }}
        run: make eval
      - name: Update-Branch
        env:
          NAME: ${{ secrets.USER_NAME }}
          EMAIL: ${{ secrets.USER_EMAIL }}
        run: make update-branch USER_NAME=$NAME USER_EMAIL=$EMAIL
          
```

### Continuous Deployment

After successful integration, the application is automatically deployed to **Hugging Face Spaces**.

This ensures that the latest validated version of the project is deployed without requiring manual intervention.

```text
Code Push
    │
    ▼
GitHub Actions Triggered
    │
    ▼
Install Dependencies
    │
    ▼
Build Application
    │
    ▼
Deploy to Hugging Face
```

## 🤗 Deployment on Hugging Face

The Machine Learning application is deployed using **Hugging Face Spaces**.

Hugging Face provides an easy way to host and share Machine Learning applications.

The deployment process is automated through GitHub Actions.

### Deployment Steps

1. Push changes to the `main` branch.
2. GitHub Actions automatically starts the CI/CD workflow.
3. If the workflow succeeds, the latest version is deployed to Hugging Face.
4. The updated application becomes available online.

## 💻 Installation

Clone the repository:

```bash
git clone <repository-url>
```

Navigate to the project directory:

```bash
cd <project-name>
```

Create a virtual environment:

```bash
python -m venv venv
```

Activate the virtual environment.

**Windows:**

```bash
venv\Scripts\activate
```

**Linux/macOS:**

```bash
source venv/bin/activate
```

Install the required dependencies:

```bash
pip install -r requirements.txt
```

Run the application:

```bash
python train.py
```

## 🎯 Key Features

* 🤖 End-to-end Machine Learning workflow.
* 🧹 Automated data preprocessing.
* 📊 Model training and evaluation.
* 🔄 Continuous Integration using GitHub Actions.
* 🚀 Continuous Deployment automation.
* 🤗 Deployment on Hugging Face Spaces.
* 🔐 Secure management of deployment credentials using GitHub Secrets.

## 🔮 Future Improvements

Potential improvements for the project include:

* Adding experiment tracking.
* Adding automated testing.
* Implementing model versioning.
* Adding data validation.
* Integrating monitoring for model performance.
* Adding Docker containerisation.
* Supporting multiple machine learning models.
* Implementing automated model retraining.
* Adding API endpoints for predictions.

Machine Learning | MLOps | Data Science

⭐ If you found this project useful, consider giving the repository a star!

** Note this was done for study purposes and care should be taken when code or some aspect of the project is to be used.**

## Resources
https://www.datacamp.com/tutorial/ci-cd-for-machine-learning
