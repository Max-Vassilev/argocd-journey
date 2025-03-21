# ArgoCD Journey

This is my learning repository for ArgoCD.

## What is ArgoCD?

ArgoCD is a **Pull-based GitOps continuous delivery tool** for Kubernetes that synchronizes clusters with desired states defined in Git repositories. It monitors Git repositories and automatically applies changes to Kubernetes clusters, ensuring they stay in sync with the declared configuration.

## Commands

1. **Start Colima**  
   `colima start`

2. **Start Minikube**  
   `minikube start`

3. **Create Namespace**  
   `kubectl create namespace argocd`

4. **Apply ArgoCD Manifests**  
   `kubectl apply -n argocd -f https://raw.githubusercontent.com/argoproj/argo-cd/stable/manifests/install.yaml`

5. **Verify Pods**  
   `kubectl get pods -A`

6. **Port-forward ArgoCD Server**  
   `kubectl port-forward -n argocd svc/argocd-server 8080:443`

7. **Get Initial Admin Secret**  
   `kubectl get secret argocd-initial-admin-secret -n argocd -o yaml`

8. **Decode Password**  
   `echo PASSWORD | base64 --decode`

9. **Apply ApplicationSet**  
   `kubectl apply -f applicationset.yaml -n argocd`

10. **Verify ApplicationSets**  
    `kubectl get applicationsets -n argocd`

## Access ArgoCD Web UI

Visit `http://localhost:8080` and log in with the `admin` username and decoded password.

## Screenshot

![image](https://github.com/user-attachments/assets/bf0c8235-815c-498e-b84e-dcac8b2c8851)

![ArgoCD Web UI](https://github.com/user-attachments/assets/aad94b9f-e165-4d5b-accf-655a03f17d7b)
