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

![image](https://github.com/user-attachments/assets/f98cac04-17ba-4816-8725-1a973e7b5545)

## Difference Between Application, App of Apps, and ApplicationSets

- **Application**:  
   An **Application** is the fundamental resource in ArgoCD that represents a deployment of a set of Kubernetes resources (like deployments, services, config maps) defined in a Git repository. Each application is tied to a specific namespace and is usually associated with a specific repo, branch, or tag.

- **App of Apps**:  
   An **App of Apps** pattern is where you define a root application in ArgoCD, and this root application has sub-applications (children). Each child application can be a separate set of Kubernetes resources, but they are all managed and controlled by the parent application. This is useful when managing multiple applications that have dependencies or need to be synchronized together.

- **ApplicationSet**:  
   **ApplicationSet** is an extension of the `Application` resource that allows you to manage multiple applications dynamically based on a set of generators. Instead of manually creating individual applications, you define an `ApplicationSet` that automatically generates and manages multiple `Application` resources. This is great for cases like deploying applications across multiple environments, regions, or clusters. You can use generators like list, Git, or Cluster to dynamically manage applications.
