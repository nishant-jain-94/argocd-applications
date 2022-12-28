# Odoo ArgoCD Setup

## Setup Instructions
1. Provision a AutoPilot Kubernetes Cluster
    ```bash
    gcloud container clusters create-auto argocd-playground \
        --region asia-south1 \
        --project=propane-service-353606
    ```
2. Install Argocd to `argocd` namespace using 
    ```bash
    kubectl create namespace argocd
    kubectl apply -n argocd -f https://raw.githubusercontent.com/argoproj/argo-cd/stable/manifests/install.yaml
    ```
3. 