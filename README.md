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
3. Port Forward ArgoCD
    ```bash
    kubectl port-forward svc/argocd-server -n argocd 8080:443
    ```
4. Get the ArgoCD Password. The default username is `admin`
    ```bash
    kubectl -n argocd get secret argocd-initial-admin-secret -o jsonpath="{.data.password}" | base64 -d; echo
    ```
4. Login
    ```
    argocd login localhost:8080
    ```