
---

# 🚀 Full-Stack-MLOps

This project demonstrates an **end-to-end Machine Learning (ML) pipeline** with full **MLOps integration** — from data ingestion to deployment and monitoring on **AWS EKS**, with experiment tracking, version control, CI/CD, and observability.

---

## 📂 Project Structure

* **Cookiecutter Data Science Template**

* **src/**

  * `logger/` – Logging utilities
  * `data_ingestion.py` – Data collection & ingestion
  * `data_preprocessing.py` – Data cleaning & transformation
  * `feature_engineering.py` – Feature extraction
  * `model_building.py` – Model training
  * `model_evaluation.py` – Model performance evaluation
  * `register_model.py` – Model registry

* **DVC Pipeline**

  * `params.yaml` – Configurable parameters
  * `dvc.yaml` – DVC pipeline definition

* **flask\_app/** – REST API for model serving

* **tests/** & **scripts/** – CI/CD tests and helper scripts

* **.github/workflows/** – CI/CD pipeline configs

* **Dockerfile** – Containerization setup

---

## ⚙️ Setup Instructions

### 🔧 1. Environment Setup

```bash
conda create -n atlas python=3.10
conda activate atlas
pip install cookiecutter dagshub mlflow dvc[s3] awscli flask
```

### 📦 2. Project Initialization

* Clone repo & apply Cookiecutter template
* Initialize Git & push changes
* Configure MLflow tracking via [DagsHub](https://dagshub.com)

### 📊 3. Experiment Tracking & Data Versioning

* MLflow for experiment tracking
* DVC for dataset & pipeline versioning
* Remote storage: **AWS S3**

### 🐳 4. Containerization

* Generate `requirements.txt` & `pipreqs`
* Build Docker image:

  ```bash
  docker build -t capstone-app:latest .
  docker run -p 8888:5000 -e CAPSTONE_TEST=<your_token> capstone-app:latest
  ```

### 🔄 5. CI/CD with GitHub Actions

* Automated build & test pipeline
* Push Docker images to **AWS ECR**

### ☸️ 6. Deployment on AWS EKS

* Install & configure `awscli`, `kubectl`, `eksctl`
* Create EKS cluster:

  ```bash
  eksctl create cluster --name flask-app-cluster --region us-east-1
  ```
* Deploy Flask app with Kubernetes manifests
* Expose via LoadBalancer & test using external IP

### 📈 7. Monitoring & Observability

* **Prometheus** – Metrics scraping from Flask app
* **Grafana** – Interactive dashboards for monitoring

---

## 📡 Tech Stack

* **Languages & Frameworks:** Python, Flask
* **Experiment Tracking:** MLflow (via Dagshub)
* **Data Versioning:** DVC + AWS S3
* **Containerization:** Docker
* **Orchestration:** Kubernetes (EKS)
* **CI/CD:** GitHub Actions + AWS ECR
* **Monitoring:** Prometheus & Grafana

---

## 🔐 Secrets & Environment Variables

* **AWS\_ACCESS\_KEY\_ID**
* **AWS\_SECRET\_ACCESS\_KEY**
* **AWS\_REGION**
* **ECR\_REPOSITORY**
* **AWS\_ACCOUNT\_ID**
* **CAPSTONE\_TEST** (Dagshub Token)

---

## 📊 Monitoring Dashboard

* **Prometheus:** `http://<EC2-Public-IP>:9090`
* **Grafana:** `http://<EC2-Public-IP>:3000` (Default: `admin/admin`)

---

## 🧹 AWS Resource Cleanup

```bash
kubectl delete deployment flask-app
kubectl delete service flask-app-service
kubectl delete secret capstone-secret
eksctl delete cluster --name flask-app-cluster --region us-east-1
```

---

## 📘 Additional Notes

* **CloudFormation**: EKS relies on AWS CloudFormation to provision infrastructure.
* **PVCs**: Persistent Volume Claims manage storage for Kubernetes pods.
* **Fleet Requests**: Ensure quota is not exceeded during NodeGroup creation.

---

## 🌟 Key Features

✅ Reproducible ML pipeline with **DVC**
✅ Experiment tracking using **MLflow**
✅ End-to-End **CI/CD pipeline** with GitHub Actions
✅ Scalable deployment with **AWS EKS**
✅ Real-time monitoring using **Prometheus + Grafana**

---

## 🚀 Future Enhancements

* Add automated hyperparameter tuning
* Expand monitoring with alerting (Grafana Alerts / AWS CloudWatch)
* Integrate with Terraform for IaC

---

🔗 **Author:** *\[Your Name]*
📌 **GitHub Repository:** *\[Link to your repo]*

---

Do you want me to make this **README more visual** (badges, workflow diagram, architecture diagram placeholders, shields for tech stack), so that it looks like a polished **open-source style project**?
