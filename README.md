#  Production-Ready GitOps CI/CD Platform on Amazon EKS

## Project Overview

A production grade gitops pipeline project deployed on Amazon EKS using Kubernetes,ArgoCD,GithubActions,Docker,Amazon ECR,Prometheus and Grafana for monitering.

The objective was to automate deployment pipeline where every git commit will be containerized by Docker and stored in ECR ,update Kubernetes manifests and Argo CD will synchronize the changes


## Architecture

                  Developer
                      │
                      ▼
                 GitHub Repository
                      │
          Push Source Code Changes
                      │
                      ▼
              GitHub Actions CI/CD
                      │
      ┌───────────────┴────────────────┐
      │                                │
      ▼                                ▼
 Build Docker Image             Update Kubernetes Manifest
      │                                │
      ▼                                ▼
 Push Image to Amazon ECR        Commit Updated Manifest
                │                       │
                └──────────────┬────────┘
                               ▼
                          Argo CD GitOps
                               │
                               ▼
                         Amazon EKS Cluster
                               │
               ┌───────────────┴───────────────┐
               ▼                               ▼
         Blue Deployment                Green Deployment
               │                               │
               └───────────────┬───────────────┘
                               ▼
                      Kubernetes Service
                               │
                               ▼
                      AWS Application Load Balancer
                               │
                               ▼
                           End Users

Prometheus
      │
      ▼
Scrapes Kubernetes & NGINX Metrics

Grafana
      │
      ▼
Visualizes Cluster and Application Metrics
```

---

# Technologies Used

### Cloud

- Amazon Web Services
- Amazon EKS
- Amazon ECR
- IAM
- VPC
- Application Load Balancer

### Containers

- Docker

### Orchestration

- Kubernetes

### GitOps

- Argo CD

### CI/CD

- GitHub Actions
- OIDC Authentication

### Monitoring

- Prometheus
- Grafana
- Node Exporter
- kube-state-metrics
- NGINX Prometheus Exporter

---

# Features

- Kubernetes on Amazon EKS
- GitOps deployment using Argo CD
- Automated CI/CD using GitHub Actions
- Secure AWS authentication using GitHub OIDC
- Automatic Docker image build
- Automatic push to Amazon ECR
- Automatic manifest update
- Automatic deployment to Kubernetes
- Blue/Green Deployment Strategy
- ALB Ingress
- Prometheus Monitoring
- Grafana Dashboards
- Application Metrics using NGINX Exporter

---

# CI/CD Workflow

1. Developer pushes code to GitHub
2. GitHub Actions starts automatically
3. OIDC authenticates with AWS
4. Docker image is built
5. Docker image is pushed to Amazon ECR
6. Kubernetes deployment manifest is updated
7. Manifest is committed back to GitHub
8. Argo CD detects Git changes
9. Argo CD deploys the latest version to Amazon EKS

---

# Blue-Green Deployment

The application consists of two deployments.

- Blue Deployment
- Green Deployment

Traffic switching is achieved by changing the Kubernetes Service selector.

Example:

Blue

```yaml
selector:
  version: blue
```

Green

```yaml
selector:
  version: green
```

No application downtime occurs while switching versions.

---

# Monitoring

The project includes complete Kubernetes monitoring.

Installed Components

- Prometheus
- Grafana
- Node Exporter
- kube-state-metrics
- NGINX Exporter
- ServiceMonitor

Metrics collected

- CPU Usage
- Memory Usage
- Pod Status
- Node Status
- Active Connections
- HTTP Requests
- Kubernetes Cluster Health

---

# Repository Structure

```
app/
Dockerfile
index.html

argocd/
application.yaml

manifests/
deploymentblue.yaml
deploymentgreen.yaml
service.yaml
ingress.yaml
nginx-exporter-service.yaml
nginx-servicemonitor.yaml

.github/
workflows/
deploy.yml
```

---

# Challenges Solved

- Configured GitHub OIDC authentication with AWS IAM
- Implemented GitOps deployment using Argo CD
- Automated Docker image versioning
- Configured Amazon ECR authentication
- Implemented Blue/Green deployment strategy
- Configured Prometheus Operator and ServiceMonitor
- Integrated Grafana dashboards for Kubernetes monitoring
- Troubleshot Kubernetes networking, ALB, and Git synchronization issues

---

# Future Enhancements

- Helm Charts
- Horizontal Pod Autoscaler
- Alertmanager
- Loki
- Promtail
- Argo Rollouts
- Canary Deployments

---

# Skills Demonstrated

- AWS
- Kubernetes
- Docker
- GitHub Actions
- GitOps
- Argo CD
- OIDC Authentication
- Amazon ECR
- CI/CD
- Blue-Green Deployment
- Prometheus
- Grafana
- Monitoring
- DevOps Automation

---

## Author

**Arunachalam**

DevOps Engineer

LinkedIn:
www.linkedin.com/in/m-kumareshan

GitHub:
https://github.com/arunak3103
