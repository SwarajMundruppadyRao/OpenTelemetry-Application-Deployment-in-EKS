# OpenTelemetry-Application-Deployment-in-EKS

> **Deploying a Secure and Scalable OpenTelemetry Application in AWS EKS with Helm, Prometheus, CI/CD, and Email Alerting**

---

## Overview

This project demonstrates the end-to-end deployment of the [OpenTelemetry Demo Application](https://github.com/open-telemetry/opentelemetry-demo) in a production-grade environment on Amazon EKS. It includes Kubernetes-native observability using Prometheus, Grafana, and Jaeger, robust Helm-based lifecycle management, custom email alerting for pod restarts, and a GitHub Actions-driven CI/CD pipeline with automated rollback capability.

---

## Architecture



---

## Project Phases

### **Phase 1: Environment & Docker-Based Validation**
- Provisioned EC2 instance on AWS
- Deployed the OpenTelemetry Demo using `docker-compose`
- Validated microservices functionality and observability UIs (Grafana, Jaeger)

### **Phase 2: Kubernetes Deployment on EKS with Helm**
- Provisioned EKS cluster using `eksctl`
- Deployed app using split YAML manifests (Kubernetes best practices)
- Integrated Helm charts for maintainability
- Implemented Helm upgrades and rollbacks (e.g., Jaeger replica scaling)

### **Phase 3: Monitoring, Alerting & Notifications**
- Prometheus used to collect `kube_pod_container_status_restarts_total`
- Custom alert rule created to monitor high pod restarts
- AlertManager configured to send **email notifications** (SMTP)
- Screenshot of triggered alert email provided in deliverables

### **Phase 4: CI/CD Integration**
- Built CI/CD pipeline using **GitHub Actions**
- Automates:
  - Docker image build and push
  - Helm-based deployment to EKS
  - Rollback to previous release on failure
- Securely manages secrets using GitHub Secrets

---

## Tech Stack

| Layer         | Technology                                      |
|---------------|--------------------------------------------------|
| Cloud         | AWS (EKS, EC2, VPC, IAM, NAT, IGW)              |
| Container     | Docker, Docker Compose                          |
| Orchestration | Kubernetes, Helm                                |
| Observability | OpenTelemetry, Prometheus, Grafana, Jaeger      |
| CI/CD         | GitHub Actions                                  |
| Notification  | AlertManager + Email (SMTP)                     |

---

## 📁 Folder Structure

```
.
├── CloudFormationTemplates/         # VPC & networking setup
├── modified_yaml/kuber_custom/     # Split Kubernetes manifests
├── helm/                           # Helm values.yaml for deployment
├── .github/workflows/              # GitHub Actions CI/CD workflow
├── alertmanager/                   # AlertManager configuration files
├── screenshots/                    # UI and alerting validation images
└── README.md
```

---

## 🔐 Secrets & Security

- Secrets (DockerHub credentials, SMTP password, kubeconfig) managed using **GitHub Secrets**
- Network access restricted via **AWS Security Groups**
- Private subnets used for all application workloads

---

## 📬 Contact

Project by Group 9 - ENPM818N Spring 2025  
Contributors:  
- Bolla Sai Saketh  
- Fahad Shaker  
- Shiv Ramolia  
- Swaraj M Rao  

GitHub Repo: [OpenTelemetry-Application-Deployment-in-EKS](https://github.com/SwarajMundruppadyRao/OpenTelemetry-Application-Deployment-in-EKS)

---

## 🏁 Final Notes

This project reflects best practices in infrastructure as code, observability, Kubernetes management, and DevOps. It can serve as a foundation for production-grade telemetry pipelines in cloud-native environments.
