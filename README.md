# argocd-journey

## Definition:
ArgoCD is a Pull-based GitOps tool for Kubernetes that ensures clusters match the desired state defined in Git. It automatically syncs the cluster with the repository, making the repo the single source of truth for configuration.


## Terms:
- **Application**:  
   **Application:** A resource in ArgoCD for deploying Kubernetes resources from a Git repo in a specific namespace.

- **App of Apps**:  
   **App of Apps:** A pattern where a root app manages multiple child apps.

- **ApplicationSet**:  
   **ApplicationSet:** An extension that dynamically manages multiple apps using generators.

## Prerequisites
You need a running Kubernetes cluster to use Helm. For local Kubernetes with Colima, use the following command:
``` 
colima start --with-kubernetes
 ```
 
## Commands

**Create Namespace**  
   ```
   kubectl create namespace argocd
   ```

**Apply ArgoCD Manifests**  
   ```
   kubectl apply -n argocd -f https://raw.githubusercontent.com/argoproj/argo-cd/stable/manifests/install.yaml
   ```

**Verify Pods**  
   ```
   kubectl get pods -A
   ```

**Port-forward ArgoCD Server**  
   ```
   kubectl port-forward -n argocd svc/argocd-server 8080:443
   ```

**Get Initial Admin Secret**  
   ```
   kubectl get secret argocd-initial-admin-secret -n argocd -o yaml
   ```

**Decode Password**  
   ```
   echo PASSWORD | base64 --decode
   ```

**Apply ApplicationSet**  
   ```
   kubectl apply -f applicationset.yaml -n argocd
   ```

**Verify ApplicationSets**  
    ```
    kubectl get applicationsets -n argocd
    ```

## Access ArgoCD Web UI

Visit `http://localhost:8080` and log in with the `admin` username and decoded password.

## Screenshots

![image](https://github.com/user-attachments/assets/bf0c8235-815c-498e-b84e-dcac8b2c8851)

![image](https://github.com/user-attachments/assets/f98cac04-17ba-4816-8725-1a973e7b5545)


