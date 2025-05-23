# nginx-helm-chart

This repository contains a custom **Helm chart** designed to deploy a simple NGINX web application using **GitOps principles** through **Argo CD**. It was created as part of the **Irembo DevOps Internship** to fulfill the Continuous Deployment with Argo CD assignment.

---

## Purpose

The goal of this repository is to:
- Define a reusable Helm chart to deploy a sample NGINX application.
- Integrate the chart with Argo CD for GitOps-based continuous deployment.
- Demonstrate Helm chart structure, Kubernetes manifests templating, and resource management.
- Showcase Argo CD's ability to monitor and auto-sync changes from GitHub.

---

## 📁 Repository Structure

```
nginx-helm-chart/
├── Chart.yaml
├── values.yaml
└── templates/
    ├── deployment.yaml
    ├── service.yaml
    ├── hpa.yaml
    ├── serviceaccount.yaml
    ├── _helpers.tpl
    └── NOTES.txt
```

---

## 📄 File/Directory Overview

### `Chart.yaml`
Defines the Helm chart metadata such as name, version, description, and app version.

### `values.yaml`
Contains the default configuration values for the Helm chart:
- `replicaCount`: number of pods to deploy
- `image`: Docker image info for NGINX
- `resources`: CPU/memory limits and requests
- `service`: service type and port

### `templates/`
Holds all the templated Kubernetes manifests that are rendered using Helm.

#### `deployment.yaml`
Defines the `Deployment` object that launches the NGINX pods and includes:
- Liveness and readiness probes
- Service account usage

#### `service.yaml`
Defines the `Service` object that exposes the NGINX app internally within the cluster.

#### `hpa.yaml`
Defines a `HorizontalPodAutoscaler` resource for autoscaling based on CPU.

#### `serviceaccount.yaml`
Creates a `ServiceAccount` bound to the pod for secure access control.

#### `_helpers.tpl`
Contains reusable Helm template functions for naming and labeling Kubernetes objects.

#### `NOTES.txt`
Optional helper text displayed to users after chart installation.

---

## How It Works with Argo CD

1. This GitHub repository is connected to Argo CD as a **Git source**.
2. Argo CD continuously watches the `main` branch and syncs changes.
3. Any update to values (e.g. replica count) is automatically deployed.
4. Argo CD shows real-time health, sync status, and logs for all managed resources.

---

## Outcome

- Verified Argo CD GitOps flow with real-time auto-sync.
- Web app confirmed running and accessible via port-forward.
- Demonstrated custom chart templating and live cluster deployment.
- Implemented HPA, probes, and service account to meet production-readiness best practices.

---

## 👤 Author

**Moise Iradukunda Ingabire**  
DevOps Intern @ Irembo  
🔗 [GitHub Profile](https://github.com/1moses1)
