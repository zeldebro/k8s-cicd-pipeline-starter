<!-- ============================= HEADER ============================= -->
<div align="center">

  <img src="https://raw.githubusercontent.com/kubernetes/kubernetes/master/logo/logo.svg" width="100" alt="Kubernetes Logo"/>

  # 🚀 K8s CI/CD Pipeline Starter

  ### The Ultimate Starter Kit for Kubernetes CI/CD Pipelines

  **A production-ready, batteries-included CI/CD pipeline template for deploying containerized apps to Kubernetes — featuring Docker, Helm, GitLab CI/CD & JFrog Artifactory.**

  > _Stop building pipelines from scratch. Clone, configure, deploy._ ✨

  <br/>

  [![Kubernetes](https://img.shields.io/badge/Kubernetes-326CE5?style=for-the-badge&logo=kubernetes&logoColor=white)](https://kubernetes.io/)
  [![Docker](https://img.shields.io/badge/Docker-2496ED?style=for-the-badge&logo=docker&logoColor=white)](https://www.docker.com/)
  [![Helm](https://img.shields.io/badge/Helm-0F1689?style=for-the-badge&logo=helm&logoColor=white)](https://helm.sh/)
  [![Node.js](https://img.shields.io/badge/Node.js-339933?style=for-the-badge&logo=nodedotjs&logoColor=white)](https://nodejs.org/)
  [![GitLab CI/CD](https://img.shields.io/badge/GitLab_CI/CD-FC6D26?style=for-the-badge&logo=gitlab&logoColor=white)](https://docs.gitlab.com/ee/ci/)

  <br/>

  ![Version](https://img.shields.io/badge/version-0.1.0-blue?style=flat-square)
  ![Chart](https://img.shields.io/badge/chart-devops--api-blueviolet?style=flat-square)
  ![License](https://img.shields.io/badge/license-MIT-green?style=flat-square)
  ![Platform](https://img.shields.io/badge/platform-linux%20%7C%20macOS-lightgrey?style=flat-square)
  ![K8s](https://img.shields.io/badge/k8s-1.19%2B-blue?style=flat-square)
  ![Helm](https://img.shields.io/badge/helm-v3-purple?style=flat-square)

  <br/>

  [Overview](#-overview) •
  [Architecture](#-architecture) •
  [Quick Start](#-quick-start) •
  [Configuration](#-configuration) •
  [CI/CD Pipeline](#-cicd-pipeline) •
  [Contributing](#-contributing)

  <br/>

</div>

<!-- ============================= OVERVIEW ============================= -->

## 🌟 Overview

Tired of spending hours wiring up CI/CD pipelines from scratch? **K8s CI/CD Pipeline Starter** gives you a **complete, production-grade pipeline** that works out of the box.

This project is perfect for:
- 🎓 **DevOps beginners** learning Kubernetes, Docker & CI/CD concepts
- 🏢 **Teams** who need a battle-tested pipeline template for their microservices
- 🧪 **Interviewees** looking for a portfolio project that screams "I know DevOps"
- 🚀 **Startups** wanting to ship to production fast without reinventing the wheel

<br/>

<table>
<tr>
<td>

### ✨ Key Features

</td>
</tr>
<tr>
<td>

| Feature | Description |
|:---|:---|
| 🐳 **Containerization** | Lightweight Docker image for a Node.js Express app |
| ⎈ **Orchestration** | Kubernetes manifests managed via Helm charts |
| 🔄 **Automation** | GitLab CI/CD pipeline for build, test & deploy |
| 📈 **Scalability** | Horizontal Pod Autoscaler (HPA) out of the box |
| 🔒 **Security** | Service accounts, pod security contexts & private registry auth |
| 🩺 **Observability** | Liveness & readiness probes configured by default |
| 📦 **Registry** | JFrog Artifactory integration for image storage |

</td>
</tr>
</table>

---

<!-- ============================= ARCHITECTURE ============================= -->

## 🏗 Architecture

<div align="center">

```
┌─────────────┐       ┌──────────────┐       ┌─────────────────────────┐       ┌──────────────────┐
│             │       │              │       │    GitLab CI/CD         │       │   Kubernetes     │
│  Developer  │──────▶│  GitLab Repo │──────▶│    Pipeline             │──────▶│   Cluster        │
│  Push Code  │       │              │       │                         │       │                  │
└─────────────┘       └──────────────┘       │  ┌─────────────────┐   │       │  ┌────────────┐  │
                                              │  │ 🔨 Build Image  │   │       │  │   Pods     │  │
                                              │  └────────┬────────┘   │       │  ├────────────┤  │
                                              │           ▼            │       │  │  Service   │  │
                                              │  ┌─────────────────┐   │       │  ├────────────┤  │
                                              │  │ 🧪 Run Tests    │   │       │  │  Ingress   │  │
                                              │  └────────┬────────┘   │       │  ├────────────┤  │
                                              │           ▼            │       │  │    HPA     │  │
                                              │  ┌─────────────────┐   │       │  ├────────────┤  │
                                              │  │ 📦 Push to JFrog│───┼──────▶│  │  Service   │  │
                                              │  └────────┬────────┘   │       │  │  Account   │  │
                                              │           ▼            │       │  └────────────┘  │
                                              │  ┌─────────────────┐   │       │                  │
                                              │  │ 🚀 Helm Deploy  │───┼──────▶│                  │
                                              │  └─────────────────┘   │       │                  │
                                              └─────────────────────────┘       └──────────────────┘
```

</div>

---

<!-- ============================= PROJECT STRUCTURE ============================= -->

## 📁 Project Structure

```
k8s-cicd-pipeline-starter/
│
├── 📄 README.md                          # You are here!
├── 📄 .gitlab-ci.yml                     # CI/CD pipeline definition (see below)
│
└── CI-CD/
    │
    ├── 🐳 docker/
    │   ├── app.js                        # Express.js application — "🚀 DevOps API is live and running!" server
    │   └── Dockerfile                    # Container image definition (Node 14)
    │
    └── ⎈  helm/
        ├── Chart.yaml                    # Helm chart metadata (v0.1.0)
        ├── values.yaml                   # Default configuration values
        ├── docker-registry-jfrog.yaml    # JFrog Artifactory registry credentials
        │
        └── templates/
            ├── _helpers.tpl              # Template helper functions & labels
            ├── deployment.yaml           # Deployment — rolling updates, probes
            ├── service.yaml              # Service — ClusterIP by default
            ├── ingress.yaml              # Ingress — external traffic routing
            ├── hpa.yaml                  # HPA — CPU/memory-based autoscaling
            ├── serviceaccount.yaml       # ServiceAccount — RBAC identity
            ├── NOTES.txt                 # Post-install usage instructions
            └── tests/
                └── test-connection.yaml  # Helm connectivity test
```

---

<!-- ============================= TECH STACK ============================= -->

## 🛠 Tech Stack

<div align="center">

| | Technology | Purpose | Version |
|:---:|:---|:---|:---|
| <img src="https://cdn.jsdelivr.net/gh/devicons/devicon/icons/nodejs/nodejs-original.svg" width="20"/> | **Node.js** | Application runtime | 14.x |
| <img src="https://cdn.jsdelivr.net/gh/devicons/devicon/icons/express/express-original.svg" width="20"/> | **Express.js** | Web framework | latest |
| <img src="https://cdn.jsdelivr.net/gh/devicons/devicon/icons/docker/docker-original.svg" width="20"/> | **Docker** | Containerization | — |
| <img src="https://cdn.jsdelivr.net/gh/devicons/devicon/icons/kubernetes/kubernetes-plain.svg" width="20"/> | **Kubernetes** | Container orchestration | 1.19+ |
| <img src="https://cdn.jsdelivr.net/gh/devicons/devicon/icons/helm/helm-original.svg" width="20"/> | **Helm** | K8s package manager | v3 (API v2) |
| <img src="https://cdn.jsdelivr.net/gh/devicons/devicon/icons/gitlab/gitlab-original.svg" width="20"/> | **GitLab CI/CD** | CI/CD automation | — |
| 📦 | **JFrog Artifactory** | Docker image registry | — |

</div>

---

<!-- ============================= QUICK START ============================= -->

## ⚡ Quick Start

Get up and running in **under 5 minutes**:

```bash
# 1️⃣  Clone the repository
git clone https://gitlab.com/zeldebro/k8s-cicd-pipeline-starter.git && cd k8s-cicd-pipeline-starter

# 2️⃣  Build & run with Docker
docker build -t devops-api:latest ./CI-CD/docker
docker run -d -p 3000:3000 --name devops-api devops-api:latest

# 3️⃣  Verify
curl http://localhost:3000
# → 🚀 DevOps API is live and running! 🎉
```

---

<!-- ============================= GETTING STARTED ============================= -->

## 🚀 Getting Started

### Prerequisites

<table>
<tr>
<td>

| Tool | Version | Installation |
|:---|:---|:---|
| 🐳 **Docker** | Latest | [Install Docker](https://docs.docker.com/get-docker/) |
| ☸️ **kubectl** | 1.19+ | [Install kubectl](https://kubernetes.io/docs/tasks/tools/) |
| ⎈ **Helm** | v3 | [Install Helm](https://helm.sh/docs/intro/install/) |
| 💚 **Node.js** | 14+ | [Install Node.js](https://nodejs.org/) |

</td>
</tr>
</table>

### Local Development

```bash
# Navigate to the app directory
cd CI-CD/docker

# Install dependencies & start the server
npm install express
node app.js

# 🎉 App is running at http://localhost:3000
```

### Docker Build

```bash
# Build the Docker image
docker build -t devops-api:latest ./CI-CD/docker

# Run the container
docker run -d -p 3000:3000 --name devops-api devops-api:latest

# Verify it's running
curl http://localhost:3000
# → 🚀 DevOps API is live and running!

# Stop & clean up
docker stop devops-api && docker rm devops-api
```

### Helm Deployment

```bash
# 1. Create image pull secret (if using JFrog Artifactory)
kubectl create secret docker-registry jfrog-secret \
  --docker-server=artifactory.devops.telekom.de \
  --docker-username=<USERNAME> \
  --docker-password=<PASSWORD>

# 2. Install the Helm chart
helm install devops-api ./CI-CD/helm \
  --set image.repository=artifactory.devops.telekom.de/your-repo/devops-api \
  --set image.tag=latest

# 3. Verify the deployment
kubectl get pods -l app.kubernetes.io/name=devops-api

# 4. Upgrade with new values
helm upgrade devops-api ./CI-CD/helm -f ./CI-CD/helm/values.yaml
```

---

<!-- ============================= CONFIGURATION ============================= -->

## ⚙️ Configuration

All configuration is managed through [`values.yaml`](CI-CD/helm/values.yaml). Key parameters:

<details>
<summary><b>📋 Click to expand full configuration reference</b></summary>

<br/>

| Parameter | Description | Default |
|:---|:---|:---|
| `replicaCount` | Number of pod replicas | `1` |
| `image.repository` | Docker image registry/repo | `nginx` |
| `image.pullPolicy` | Image pull policy | `IfNotPresent` |
| `image.tag` | Image tag (overrides `appVersion`) | `""` |
| `service.type` | Kubernetes Service type | `ClusterIP` |
| `service.port` | Service port | `80` |
| `ingress.enabled` | Enable Ingress resource | `false` |
| `ingress.className` | Ingress class name | `""` |
| `ingress.hosts[0].host` | Ingress hostname | `devops-api.dev.com` |
| `autoscaling.enabled` | Enable HPA | `false` |
| `autoscaling.minReplicas` | Minimum replicas for HPA | `1` |
| `autoscaling.maxReplicas` | Maximum replicas for HPA | `100` |
| `autoscaling.targetCPUUtilizationPercentage` | CPU threshold for scaling | `80` |
| `serviceAccount.create` | Create a ServiceAccount | `true` |
| `serviceAccount.name` | ServiceAccount name | `""` |
| `podAnnotations` | Additional pod annotations | `{}` |
| `podSecurityContext` | Pod security context | `{}` |
| `securityContext` | Container security context | `{}` |
| `resources` | CPU/Memory resource requests & limits | `{}` |
| `nodeSelector` | Node selector constraints | `{}` |
| `tolerations` | Pod tolerations | `[]` |
| `affinity` | Pod affinity rules | `{}` |

</details>

<br/>

### 🏭 Example: Production Override

Create a `values-production.yaml` for production-grade deployments:

```yaml
# values-production.yaml
replicaCount: 3

image:
  repository: artifactory.devops.telekom.de/your-repo/devops-api
  tag: "1.2.0"
  pullPolicy: Always

resources:
  limits:
    cpu: 200m
    memory: 256Mi
  requests:
    cpu: 100m
    memory: 128Mi

autoscaling:
  enabled: true
  minReplicas: 3
  maxReplicas: 10
  targetCPUUtilizationPercentage: 75

ingress:
  enabled: true
  className: nginx
  hosts:
    - host: devops-api.production.com
      paths:
        - path: /
          pathType: Prefix
```

```bash
# Deploy with production values
helm upgrade --install devops-api ./CI-CD/helm -f values-production.yaml
```

---

<!-- ============================= HELM CHART ============================= -->

## ⎈ Helm Chart Details

<div align="center">

| Property | Value |
|:---|:---|
| **Chart Name** | `devops-api` |
| **Chart Version** | `0.1.0` |
| **App Version** | `1.16.0` |
| **Type** | `application` |
| **API Version** | `v2` |

</div>

### Included Kubernetes Resources

| Resource | Template | Description |
|:---|:---|:---|
| 🟢 `Deployment` | `deployment.yaml` | Manages pod replicas with rolling updates, liveness & readiness probes |
| 🔵 `Service` | `service.yaml` | Exposes the application within the cluster (ClusterIP) |
| 🟣 `Ingress` | `ingress.yaml` | Routes external HTTP/HTTPS traffic to the service *(optional)* |
| 🟡 `HPA` | `hpa.yaml` | Auto-scales pods based on CPU/Memory utilization *(optional)* |
| 🔴 `ServiceAccount` | `serviceaccount.yaml` | Provides pod identity for RBAC policies |

---

<!-- ============================= CI/CD PIPELINE ============================= -->

## 🔄 CI/CD Pipeline

The GitLab CI/CD pipeline automates the complete application lifecycle from code to production:

<div align="center">

```
  ╔══════════╗     ╔══════════╗     ╔══════════╗     ╔══════════╗
  ║  BUILD   ║────▶║   TEST   ║────▶║   PUSH   ║────▶║  DEPLOY  ║
  ║          ║     ║          ║     ║          ║     ║          ║
  ║ 🔨 Docker║     ║ 🧪 Unit  ║     ║ 📦 JFrog ║     ║ 🚀 Helm  ║
  ║   Build  ║     ║   Tests  ║     ║  Upload  ║     ║  Upgrade ║
  ╚══════════╝     ╚══════════╝     ╚══════════╝     ╚══════════╝
```

</div>

### Pipeline Stages

| Stage | What It Does | Trigger |
|:---|:---|:---|
| **🔨 Build** | Builds the Docker image from `Dockerfile` | Every push |
| **🧪 Test** | Runs application & Helm chart tests | Every push |
| **📦 Push** | Pushes the image to JFrog Artifactory | On `main` branch |
| **🚀 Deploy** | Deploys/upgrades the Helm release on Kubernetes | On `main` branch |

### Sample `.gitlab-ci.yml`

<details>
<summary><b>📋 Click to expand the sample pipeline configuration</b></summary>

```yaml
stages:
  - build
  - test
  - push
  - deploy

variables:
  DOCKER_IMAGE: artifactory.devops.telekom.de/your-repo/devops-api
  DOCKER_TAG: $CI_COMMIT_SHORT_SHA
  HELM_RELEASE: devops-api
  HELM_CHART: ./CI-CD/helm
  KUBE_NAMESPACE: default

# ─── BUILD ──────────────────────────────────────────────
build:
  stage: build
  image: docker:latest
  services:
    - docker:dind
  script:
    - docker build -t $DOCKER_IMAGE:$DOCKER_TAG ./CI-CD/docker
    - docker tag $DOCKER_IMAGE:$DOCKER_TAG $DOCKER_IMAGE:latest
  only:
    - main
    - merge_requests

# ─── TEST ───────────────────────────────────────────────
test:
  stage: test
  image: node:14
  script:
    - cd CI-CD/docker
    - npm install express
    - node -e "require('./app.js')" &
    - sleep 2
    - curl -f http://localhost:3000 || exit 1
  only:
    - main
    - merge_requests

# ─── PUSH ───────────────────────────────────────────────
push:
  stage: push
  image: docker:latest
  services:
    - docker:dind
  script:
    - docker login -u $JFROG_USER -p $JFROG_PASS artifactory.devops.telekom.de
    - docker push $DOCKER_IMAGE:$DOCKER_TAG
    - docker push $DOCKER_IMAGE:latest
  only:
    - main

# ─── DEPLOY ─────────────────────────────────────────────
deploy:
  stage: deploy
  image: alpine/helm:3.12.0
  script:
    - helm upgrade --install $HELM_RELEASE $HELM_CHART
        --namespace $KUBE_NAMESPACE
        --set image.repository=$DOCKER_IMAGE
        --set image.tag=$DOCKER_TAG
        --wait
        --timeout 300s
  only:
    - main
  environment:
    name: production
    url: https://devops-api.production.com
```

</details>

> 💡 **Tip:** Copy this into a `.gitlab-ci.yml` file at the root of your repository and configure the CI/CD variables (`JFROG_USER`, `JFROG_PASS`) in **Settings → CI/CD → Variables**.

---

<!-- ============================= APP CODE ============================= -->

## 💻 Application Code

The sample application is a minimal **Express.js** server:

```javascript
// CI-CD/docker/app.js
const express = require('express')
const app = express()

app.get('/', (req, res) => res.send('🚀 DevOps API is live and running!'))
app.listen(3000, () => console.log('Server ready'))
```

**Dockerfile** — Lightweight Node.js 14 container:

```dockerfile
FROM node:14
WORKDIR /usr/src/app
COPY app.js ./
RUN npm install express
EXPOSE 3000
CMD ["node", "app.js"]
```

---

<!-- ============================= TROUBLESHOOTING ============================= -->

## 🔧 Troubleshooting

<details>
<summary><b>Pod stuck in <code>ImagePullBackOff</code></b></summary>

Ensure your image pull secret is configured correctly:

```bash
kubectl get secret jfrog-secret -o yaml
kubectl describe pod <pod-name>
```

Verify the secret is referenced in `values.yaml` under `imagePullSecrets`.

</details>

<details>
<summary><b>Helm install fails with <code>UPGRADE FAILED</code></b></summary>

Try uninstalling first and reinstalling:

```bash
helm uninstall devops-api
helm install devops-api ./CI-CD/helm
```

</details>

<details>
<summary><b>Application returns <code>502 Bad Gateway</code></b></summary>

Check that the container port matches your service configuration:

```bash
kubectl logs -l app.kubernetes.io/name=devops-api
kubectl get endpoints devops-api
```

The app listens on port **3000** — make sure the deployment's `containerPort` and service `targetPort` are aligned.

</details>

<details>
<summary><b>HPA not scaling</b></summary>

Ensure metrics-server is installed in your cluster and resource requests are defined:

```bash
kubectl top pods
kubectl describe hpa devops-api
```

</details>

---

<!-- ============================= CONTRIBUTING ============================= -->

## 🤝 Contributing

Contributions are welcome! Here's how to get started:

```
1. 🍴 Fork the repository
2. 🌿 Create a feature branch     → git checkout -b feature/amazing-feature
3. 💾 Commit your changes          → git commit -m 'feat: add amazing feature'
4. 📤 Push to the branch           → git push origin feature/amazing-feature
5. 🔃 Open a Merge Request
```

### Commit Convention

This project follows [Conventional Commits](https://www.conventionalcommits.org/):

| Prefix | Purpose |
|:---|:---|
| `feat:` | New feature |
| `fix:` | Bug fix |
| `docs:` | Documentation changes |
| `chore:` | Maintenance tasks |
| `refactor:` | Code refactoring |

---

<!-- ============================= LICENSE ============================= -->

## 📜 License

This project is licensed under the **MIT License**.

```
MIT License

Copyright (c) 2026

Permission is hereby granted, free of charge, to any person obtaining a copy
of this software and associated documentation files (the "Software"), to deal
in the Software without restriction, including without limitation the rights
to use, copy, modify, merge, publish, distribute, sublicense, and/or sell
copies of the Software, and to permit persons to whom the Software is
furnished to do so, subject to the following conditions:

The above copyright notice and this permission notice shall be included in all
copies or substantial portions of the Software.

THE SOFTWARE IS PROVIDED "AS IS", WITHOUT WARRANTY OF ANY KIND, EXPRESS OR
IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES OF MERCHANTABILITY,
FITNESS FOR A PARTICULAR PURPOSE AND NONINFRINGEMENT.
```

---

<!-- ============================= FOOTER ============================= -->

<div align="center">

  <br/>

  **⭐ Star this repo if it saved you time!**

  <br/>

  Made with ❤️ for the DevOps Community

  <br/>

  <sub>🔑 Keywords: Kubernetes, CI/CD, Docker, Helm, GitLab, Pipeline, DevOps, K8s, Starter Kit, Template, JFrog, Microservices, Deployment</sub>

</div>
